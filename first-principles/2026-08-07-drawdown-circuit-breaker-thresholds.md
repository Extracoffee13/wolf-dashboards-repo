# First-Principles Spike — 2026-08-07

## Question

How should a daily/weekly drawdown circuit-breaker threshold be derived from
first principles for an automated trading system, and how does WOLF's actual
pair (-3% daily / -7% weekly, per `wolf_live_data.json`'s
`circuit_breaker` block and dashboard buffer readout: "Daily: -1.3% (buf:
1.7%) | Weekly: -3.9% (buf: 3.1%)") compare to standard risk-management
practice?

The backlog file (`first-principles-backlog.md`) did not exist yet — it was
created by this run, seeded with a few candidate questions, and this one was
picked because it's directly load-bearing for live Construct work (WOLF is
in PAPER mode, Ascension Phase 2, `real_money_unlocked: false`).

## Step 1 — First-principles derivation (no retrieval)

**What a circuit breaker is actually for.** It's a control-chart problem,
not a prediction problem: using only cumulative P&L observed in real time,
decide whether today's loss is "ordinary variance" or "the strategy broke."
Two failure costs trade off against each other — a false halt (strategy is
fine, breaker fires, foregone edge for the day) versus a false continue
(strategy is broken, breaker stays green, capital keeps bleeding every day
until a human catches it). False-continue cost compounds daily; false-halt
cost is roughly one-shot. That asymmetry argues for erring toward tighter
thresholds, especially pre-capital-unlock, where the false-halt cost is
near zero (it's paper money) but the trust-building cost of an undetected
break is not.

**Statistical basis for a single-day threshold.** If a strategy's live
daily return falls k standard deviations below its backtested expected
return, that's evidence the live process has diverged from the backtested
one. Standard control-chart practice uses k≈2–3σ (2σ ≈ 1-in-20 daily false
alarm rate — too often, roughly one false halt a month by chance alone; 3σ ≈
1-in-370 — rare enough to trust). For a strategy running daily, 3σ is the
more defensible choice for a *daily* halt precisely because the false-alarm
budget has to survive ~250 trading days a year.

**Time-scaling from daily to weekly.** For a return process with
independent daily increments, variance is additive, so standard deviation
over n days scales as √n, not n. A 5-trading-day week therefore has
σ_week ≈ σ_day · √5 ≈ 2.236·σ_day — not 5·σ_day. If the daily threshold sits
at kσ_day, the i.i.d.-consistent weekly threshold at the same confidence
level is k·σ_day·√5 = daily_threshold · √5 ≈ daily_threshold · 2.236. This
is the single fact that separates a naive linear breaker (week = 5× day)
from a first-principles one.

**Why real strategy failure breaks the i.i.d. assumption — and which way.**
A broken model, bad data feed, or regime shift produces *autocorrelated*
losing days: today's loss raises the odds tomorrow is also a loss, because
the underlying cause persists. Under positive autocorrelation, a five-day
cumulative loss is stronger evidence of "broken" than pure luck would
produce under independence. So a well-designed weekly gate should sit at or
*below* the √5 multiple of the daily one, not above it — sustained badness
is disproportionately caused by real breakage rather than chance, and the
breaker should be at least as suspicious of it as the i.i.d. null model,
arguably more.

**Graduated response.** A rational design shouldn't binary-flip from
"trade normally" to "flatten everything." A soft stop (halt new entries,
let existing positions play out) before a hard stop (flatten all) avoids
paying forced-liquidation/timing costs on every trigger, while still
capping the addition of new exposure the moment the soft threshold fires.

**Applying the numbers.** WOLF's daily threshold is 3%. The i.i.d.
prediction for the matching weekly threshold is 3%·√5 ≈ 6.7%. WOLF's actual
weekly threshold is 7% — within ~5% of the pure-independence prediction,
and, per the autocorrelation argument above, if anything slightly *looser*
than a first-principles design informed by realistic (correlated) failure
modes would recommend. WOLF's structure also already separates
`halt_new_entries` from `halt_all_activity` as independent booleans, and
publishes a live buffer-to-threshold number on the dashboard — both are
graduated-response and leading-indicator features that fall directly out of
the reasoning above, independent of knowing any named convention for them.

## Step 2 — Corpus search (after the derivation above was written)

Two searches: algo-trading drawdown/circuit-breaker conventions, and the
square-root-of-time volatility-scaling rule.

- **Square-root-of-time rule**: confirmed as the standard method — a one-day
  risk estimate is scaled to a longer horizon T by multiplying by √T; this
  is the method the Basel Committee on Banking Supervision recommends for
  scaling 1-day VaR to the 10-day regulatory VaR, and it's widely used
  across the industry. ([breakingdownfinance.com](https://breakingdownfinance.com/finance-topics/finance-basics/square-root-of-time-rule/), [LSE working paper](https://eprints.lse.ac.uk/24827/1/dp439.pdf))
- **The rule is known to be lenient under serial dependence**: published
  literature finds the square-root-of-time rule is only accurate under
  i.i.d., approximately-normal returns, and is *generally downward-biased*
  (understates risk) when returns show serial dependence or volatility
  clustering — i.e., it systematically produces multi-day thresholds that
  are looser than warranted exactly when failure is autocorrelated.
  ([ScienceDirect: how accurate is the square-root-of-time rule in scaling tail risk](https://www.sciencedirect.com/science/article/abs/pii/S037842661000378X))
- **Industry drawdown-limit conventions**: 2026 prop-trading norms (FTMO,
  Topstep and similar) commonly use a 5% max daily loss limit; weekly caps
  are more heterogeneous across sources, with some citing 2–3% (to keep a
  bad week from becoming a bad month) and others 5–6%, alongside ~10–12%
  monthly caps. ([P&L Ledger: daily loss limits & weekly max drawdown rules](https://www.pnlledger.com/daily-loss-limits-weekly-max-drawdown-rules/))
- **Two-tier / graduated response**: a common pattern is Tier 1 at ~50% of
  the daily limit (cut position size), Tier 2 at 100% (stop trading
  entirely) — the same soft-stop/hard-stop structure derived above.
  ([Traders4Traders: daily drawdown vs max drawdown](https://traders4traders.com/daily-drawdown-vs-max-drawdown-the-institutional-guide-to-professional-risk-control/))

## Step 3 — Delta

**Category: rediscovered.**

The core mechanism — scale a daily threshold to a weekly one by √(trading
days), not linearly, and treat that scaling as *lenient* rather than exact
because real failure is autocorrelated — is exactly the Basel-endorsed
square-root-of-time rule plus its known bias direction, arrived at here
purely from the additive-variance / independent-increments argument, before
any search confirmed either the rule's name or its documented bias. The
graduated soft-stop/hard-stop structure also matches the industry's
published two-tier pattern independently.

One place the two disagree in magnitude rather than mechanism: cited
industry weekly caps cluster at 2–6%, while WOLF's 7% sits at or slightly
above that range even though it's consistent with (in fact very close to)
the √5-scaled version of WOLF's own 3% daily figure. That's not a
mechanism error — it's a legitimate calibration choice (WOLF is PAPER
mode, so a looser weekly cap costs nothing in real dollars yet) but it's
worth flagging as the one number that doesn't fully triangulate with both
the derivation *and* the industry range simultaneously. WOLF's 3% daily
threshold, by contrast, sits comfortably tighter than the widely-cited 5%
prop-firm daily standard — consistent with the first-principles argument
that a pre-capital-unlock system should bias toward catching problems early
since the cost of a false halt is currently near zero.

## Commentary

The strongest confirmation here isn't the numbers, it's the *bias
direction*: reasoning from "variance is additive under independence, so
std-dev scales as √n" predicts not just a formula but a known failure mode
of that formula (it understates risk when the real process is
autocorrelated) — and that failure mode is exactly what the published
critique literature on the square-root-of-time rule says. Getting the
formula right is arithmetic; getting the *direction of its bias* right from
a one-sentence causal argument about persistence is the part worth trusting
this method for going forward.
