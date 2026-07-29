# First-Principles Spike — 2026-07-29

## Question

WOLF's live circuit breaker (`wolf_live_data.json`) reports:
`CLEAR — Daily: -1.3% (buf: 1.7%) | Weekly: -3.9% (buf: 3.1%)`

Working out the implied breach thresholds (current loss + remaining buffer):
daily breach ≈ **3.0%**, weekly breach ≈ **7.0%** — a ratio of about **2.33×**.

Question: *From first principles, why should a weekly loss-circuit-breaker
threshold sit at roughly 2–2.5× the daily threshold, rather than 5× (stacking
five identical daily limits) or 1× (the same number for both)? And does
WOLF's actual configured ratio make sense under that reasoning?*

The backlog file (`first-principles-backlog.md`) didn't exist yet, so this
question was self-generated from the agent architecture / trading-system
primitives visible in this repo's live data, per the spike's fallback rule.

## First-Principles Answer (derived before any search)

Start from the simplest possible model of daily P&L: treat each day's return
`r_t` as drawn i.i.d. from some distribution with mean ≈0 and standard
deviation σ (a random walk — the null hypothesis you'd reach for before
assuming anything fancier about markets). A circuit breaker threshold is,
functionally, a statement like "stop when losses look like more than pure
noise for this window" — i.e., set it at *k* standard deviations of the
window's *own* distribution, for some fixed confidence level *k* the designer
is willing to tolerate as a false-positive rate.

Key primitive: for independent random variables, variances add:
`Var(ΣX_i) = ΣVar(X_i)`. So the standard deviation of a sum of N i.i.d. daily
returns is `σ_N = σ·√N`, not `σ·N`. A trading week has N = 5 sessions. If the
weekly breaker is meant to represent the *same* confidence level k as the
daily breaker (i.e., "equally surprising" under the null model), then:

```
Threshold_weekly = k · σ · √5 = √5 · Threshold_daily
√5 ≈ 2.236
```

So a first-principles designer lands on **≈2.24×**, not 5× and not 1×.

Why not 5×? That would implicitly assume perfect correlation — that a bad
week is "five equally bad days stacked with zero diversification benefit."
But if daily moves are actually independent, five simultaneously bad days is
a far rarer coincidence than any one bad day; requiring 5× would make the
weekly breaker almost never trip on its own (redundant with the daily one,
wasting the tolerance budget on an unrealistically extreme joint event).

Why not 1× (same number for both)? That ignores that noise *accumulates*
over time at all. A random walk's typical spread still grows with the
window even with no signal whatsoever; using the daily ceiling as the weekly
ceiling too would trip the weekly breaker constantly on pure noise, making it
a useless (non-informative) signal.

Refinement pass, still without looking anything up: real markets aren't
perfectly i.i.d. Two known deviations from the toy model, reasoned from what
"a bad trading week" structurally is: (1) fat left tails — large losses are
more probable than a Gaussian implies, and (2) positive autocorrelation
during drawdowns — forced deleveraging, stop-outs, and trend-following
mechanically make a bad day more likely to be followed by another bad day,
which directly breaks the independence assumption `√N` relies on. Both
effects should push the *true* safe ratio somewhat *above* the naive 2.236,
as a margin for regime risk — but nowhere close to 5×, since that would
require near-total, sustained correlation across the whole week.

**Prediction to check against WOLF's real numbers:** the actual configured
ratio should land a bit above 2.236, not at it exactly and not near 5.

## Corpus Answer (found after searching)

Standard quantitative risk management has a name for exactly this: the
**square-root-of-time rule** for scaling volatility/VaR across horizons.
Textbook statement, found verbatim in the search: *"Weekly volatility =
daily volatility × √5 = daily volatility × 2.24"* — the same derivation and
the same numeric constant, arrived at independently above. The Basel
Committee's market-risk framework uses the same logic to scale 1-day VaR to
10-day VaR by ×√10. The literature also flags the same caveat reasoned out
above: the rule assumes i.i.d., roughly-normal returns and *underestimates*
risk when there's linear dependence (autocorrelation) or fat tails — which
is precisely the direction and reason the refinement pass predicted.

Separately, prop-trading-firm practice (FTMO/Topstep-style funded accounts)
uses a much flatter ratio — commonly a flat 5% daily limit and a 5–7% weekly
limit, i.e. roughly 1.0–1.4×, far below the statistical 2.24×. The stated
rationale there is *behavioral*, not statistical: the daily limit exists to
stop revenge-trading/emotional decisions within a session, not to bound
random-walk noise — a genuinely different design goal from the VaR-scaling
one.

## Delta

**Category: rediscovered**, with one **novel** side-observation.

The core derivation (√N scaling, the 2.24 constant, the fat-tail/
autocorrelation caveat) independently reconstructed the standard
square-root-of-time rule almost exactly, including the direction of its
known bias. That's a clean rediscovery — it validates that the reasoning
chain here (variance additivity → σ√N → same-confidence-level thresholds)
is the *real* mechanism behind the textbook rule, not just a memorized
constant.

The side-observation is more novel: WOLF's actual live ratio (7.0% / 3.0% =
2.33×) sits almost exactly on the statistical/VaR-scaling prediction
(2.236×, plus a small pad in the predicted direction) rather than on the
prop-firm behavioral heuristic (~1.0–1.4×). That's a real design signal,
not something the corpus states explicitly: it suggests WOLF's circuit
breaker was built (deliberately or by convergent reasoning) as a
statistical noise-floor detector, not as a behavioral guardrail against
"revenge trading" — which matters for how it should be tuned going
forward (e.g., if paper-trading autocorrelation turns out higher than
assumed, the weekly threshold is the one that most needs the extra pad,
not the daily one).

## Confidence

0.6 — the √N derivation and its corpus match are solid; the claim about
*why* WOLF's specific ratio landed near 2.33 (deliberate vs. coincidental)
is an inference from one data point, not something confirmed against any
design doc.
