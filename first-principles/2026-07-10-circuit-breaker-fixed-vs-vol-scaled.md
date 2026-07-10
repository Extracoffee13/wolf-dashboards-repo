# First-Principles Spike — 2026-07-10

## Question

Should a portfolio circuit breaker (like Hartley Capital's daily/weekly
loss guard visible in `wolf_live_data.json`) use a fixed-percentage loss
threshold, or one scaled to trailing volatility?

Chosen because the repo already contains a live instance of this design
decision: `daily_pnl.circuit_breaker_message` shows a fixed-looking
"Daily: -1.3% (buf: 1.7%) | Weekly: -3.9% (buf: 3.1%)" nested threshold
structure, worth interrogating rather than assuming is correct.

## First-principles answer (derived before any search)

A circuit breaker serves two purposes that get conflated under one number:

1. **Statistical tail-risk containment** — flag when today's loss is
   anomalous relative to the model's own assumptions.
2. **Capital / psychological floor** — a loss the operator cannot absorb,
   full stop, regardless of *why* it happened.

These want different math. If daily P&L has standard deviation σ, the
probability of breaching a fixed threshold T is roughly Φ(-T/σ). This is
not constant — it shrinks in calm regimes (breaker never fires, leverage
quietly builds) and spikes in turbulent regimes (breaker fires
constantly and stops being a meaningful signal). A threshold meant to
represent "this is a 1-in-100-day event" has to move with σ to keep
meaning that. So tail-risk containment is inherently volatility-relative.

Capital preservation is the opposite: it is legitimately fixed. The fund
doesn't get permission to lose more just because volatility happened to
be elevated that week — the floor is about what the operator/investor can
tolerate, not about statistical surprise.

Consequence: a pure fixed-% breaker under-protects in calm markets and
over-trips in stressed ones. A pure vol-scaled breaker is pro-cyclical —
trailing-volatility estimators lag, so the stop widens right as a shock
begins, since low realized vol typically precedes the first leg of a
crash, not follows it. And a vol-scaled breaker alone has no hard floor.

**Answer: run both, trip on whichever fires first** — vol-scaled as an
early statistical tripwire, fixed-% as the un-negotiable backstop.
`effective_threshold = min(fixed_floor, k · trailing_σ)`.

**Bonus check against this repo's actual numbers:** the observed
daily/weekly buffers (1.7% / 3.1%) can be sanity-checked against a
random-walk assumption, where weekly σ ≈ daily σ × √5 ≈ 2.24×. Pure
time-scaling from a 1.7% daily buffer would predict a ~3.8% weekly
buffer; the observed 3.1% is tighter. That means the weekly leg is
deliberately more conservative per unit time than sqrt-time scaling
alone would justify — it's not just a longer-window copy of the daily
rule, it's specifically tuned to catch "slow bleeds" (sequences of
days that each individually clear the daily bar but compound past
tolerance over a week). That's a legitimate second failure mode a
single daily-only breaker is blind to.

## Corpus answer (found via search, after the above was written)

- **Exchange-level circuit breakers (NYSE market-wide, 7% / 13% / 20% on
  the S&P 500)** are fixed-percentage, not vol-scaled. The 7% level was
  chosen by backtesting 1970–2012 data (a 7% intraday move happens less
  than once/year on average); levels are static once set. Design intent
  is explicitly about legibility and predictability across all market
  participants, plus a deliberate "speed bump" sequencing (Level 1 must
  fire before Level 2 can) to prevent cascading halts.
- **Professional/systematic portfolio risk management** (CTAs, risk
  parity, position-sizing literature) is the opposite: volatility
  targeting / inverse-vol weighting / ATR-based sizing is the orthodox
  default, precisely because it holds *risk* constant instead of holding
  *price move* constant. Cited empirical effect sizes: shifting from
  equal-weight to inverse-vol weighting raised Sharpe from 0.99 to 1.54
  and cut max drawdown from -30.84% to -13.81% in one study; ATR-based
  sizing is reported to cut drawdowns up to 25% in volatile periods vs.
  fixed-percentage sizing.

So the corpus doesn't give one universal answer — it bifurcates by
altitude: exchange-wide circuit breakers stay fixed (systemic legibility
beats statistical precision when millions of participants need to
predict the same rule), while individual portfolio/position risk
management goes vol-scaled (statistical precision beats legibility when
there's one decision-maker optimizing their own book).

## Delta category: **novel**

The corpus doesn't frame this as "combine both, take the min" — it
presents fixed-vs-vol-scaled as a fork chosen by altitude (exchange vs.
single book), not as complementary layers within the same book. The
first-principles run independently arrived at the same underlying
facts the corpus supplies as justification (vol-scaling reduces breach
volatility / improves risk-adjusted outcomes; fixed thresholds are
chosen for legibility and calibrated once via backtest) — that part is
essentially rediscovery. But the synthesis — that a *single* portfolio
should run a fixed floor and a vol-scaled tripwire concurrently, plus
the direct numeric audit showing Hartley Capital's own weekly buffer is
intentionally tighter than sqrt-time scaling would predict — is an
applied conclusion the corpus search didn't surface anywhere. It's a
usable, repo-specific finding, not just a restated textbook answer.

## Commentary

The generic "fixed vs. dynamic threshold" question has a real answer in
the literature and reasoning from primitives converged on it without
needing to look it up — that's the encouraging part. The more valuable
output wasn't the abstract answer, though; it was pointing the same
reasoning at the numbers already sitting in `wolf_live_data.json` and
getting a concrete, checkable claim about this fund's own risk
configuration. That's the shape worth repeating: derive the general
principle blind, then immediately apply it to whatever real numbers are
lying around in the Construct, since that's where a first-principles
answer earns more than a search would have.
