# First-Principles Spike — 2026-07-24

## Question

For a leveraged trading portfolio (like Hartley Capital's), what is the
mathematically optimal fraction of capital to risk per position — and why
do practitioners systematically bet *less* than that optimum, even when
their edge estimate is correct?

Chosen because Hartley Capital's live portfolio (`wolf_live_data.json`)
already runs a heuristic risk control — a daily/weekly drawdown circuit
breaker (currently: daily -1.3% against a 1.7% buffer, weekly -3.9%
against a 3.1% buffer) — without a stated derivation for why those
particular thresholds, or that particular control shape, are correct.

## First-Principles Derivation (no retrieval)

**Primitive 1: capital compounds multiplicatively.** Wealth after n bets
is W_n = W_0 · Π(1 + f·r_i), not W_0 + Σ(f·r_i). This single fact is the
whole ballgame — it means the object to optimize is *not* expected wealth.

**Why not maximize expected wealth?** Consider a coin-flip bet: win 2.5x
stake with p=0.5, lose stake with p=0.5. Expected value of betting your
entire bankroll every round is strictly positive and grows without bound
in expectation. But almost every individual path goes to zero, because a
single loss at f=1 is wealth-annihilating and no future win can recover
from zero. The *mean* of a multiplicative process is dominated by
astronomically unlikely tail paths; the *typical* (median, almost-sure)
path is governed by something else. That something else is the expected
growth rate of log-wealth: g(f) = E[ln(1 + f·r)]. Maximizing E[log W_n] is
equivalent to maximizing the typical path's long-run compounding rate,
which is what an ongoing trading operation actually cares about (you live
one path, not the ensemble average).

**Deriving the optimal fraction.** Take the simplest edge case: a bet that
wins b:1 with probability p, loses the full stake with probability q=1-p.
Wealth relative per round is (1+bf) w.p. p, (1-f) w.p. q. Growth rate:

  g(f) = p·ln(1+bf) + q·ln(1-f)

Differentiate and set to zero:

  g'(f) = pb/(1+bf) − q/(1−f) = 0
  ⟹ pb(1−f) = q(1+bf)
  ⟹ pb − q = f·b·(p+q) = f·b   (since p+q=1)
  ⟹ f* = p − q/b = (bp − q)/b

That's the Kelly fraction. For a continuous-return asset (the relevant
case for equities), the analogous derivation (maximize E[ln(1+f·r)] via a
second-order/Gaussian approximation) yields:

  f* ≈ μ/σ²

i.e., optimal leverage is expected excess return divided by the *variance*
of returns — edge scaled inversely by risk-squared, not risk. This alone
explains why doubling position size to chase double the expected return is
never correct: variance in the denominator grows faster than the linear
edge gain once you're above f*.

**Why bet less than f\*, given a correct edge estimate?** Two independent
arguments, neither requiring parameter error:

1. *g(f) is concave and flat near the peak.* Near f*, g'(f)≈0 by
   construction, so g(0.5·f*) is close to g(f*) — you give up a modest
   slice of growth rate. But the variance of terminal wealth (and the
   depth of drawdowns along the way) scales roughly with f², not f. Half
   the fraction gives you ~75% of the growth at ~25% of the variance. This
   is a pure risk-adjusted-return argument, no estimation error needed.

2. *The penalty for overbetting is asymmetric and steep, while the penalty
   for underbetting is linear and shallow.* g(f) is concave with g(0)=0
   and g(f) turns negative again well before f=2f* in most parameterizations
   — meaning an error that overshoots the true optimum by even a small
   margin can flip you from compounding growth to compounding *ruin*.
   Undershooting by the same margin only costs you a proportional amount
   of growth. Since real edge estimates (p, b, or μ, σ²) are always noisy,
   and the cost function is asymmetric around the estimate, a rational
   bettor shades down from their point estimate of f* — not because the
   math changes, but because the estimate itself has an error distribution
   and the loss function punishes one side of that distribution far more
   than the other.

**Connecting back to the portfolio.** A multi-position portfolio adds a
third factor beyond single-asset Kelly: realized correlation across
"independent" bets is usually higher than assumed (everything sells off
together in a drawdown), which understates effective variance and means
naive per-position Kelly sizing overstates the safe aggregate fraction.
A fixed-percentage daily/weekly circuit breaker, like the one already
running in `wolf_live_data.json`, is best understood as a *model-free
proxy* for fractional-Kelly variance control: rather than estimating μ
and σ² per position and solving for f*, it observes realized portfolio
drawdown directly and throttles when a threshold is crossed. It doesn't
require trusting an edge estimate at all — which is itself a hedge against
exactly the estimation-error problem the derivation above surfaces. The
open question that follows (queued in the backlog) is whether a *fixed*
percentage breaker is well-calibrated, or whether it should be
volatility-normalized (ATR-scaled) so the throttle triggers at a
consistent point in risk-space rather than a consistent point in
percent-P&L-space.

## Corpus Answer

The standard treatment (Kelly 1956, popularized by Thorp) matches the
derivation above closely:

- Formula: **f\* = (bp − q) / b**, derived by maximizing E[log(wealth)]
  rather than E[wealth], for exactly the reason given above (multiplicative
  compounding makes the arithmetic mean the wrong optimization target).
- Continuous/Gaussian analogue used in quant finance: **f\* ≈ μ/σ²**.
- Practitioners near-universally use **fractional Kelly** (commonly half-
  Kelly), for the two reasons independently derived above, stated in the
  literature as: (1) growth scales ~linearly with f near the optimum while
  variance scales ~f², so half-Kelly captures roughly 75% of the growth
  rate at a fraction of the variance/drawdown risk; (2) **estimation
  error** in p/b (or μ/σ²) combined with the **asymmetric penalty** for
  overbetting (overshooting f* by 50% can turn a positive-growth bet into
  a negative-growth one) makes shading down from the point-estimate
  optimum the correct response to parameter uncertainty, not just a
  conservative preference.

## Delta

**Category: rediscovered**

The derivation independently reconstructed the exact formula (f* = (bp−q)/b,
f* ≈ μ/σ² for continuous returns), the exact justification for optimizing
log-wealth over expected wealth, and both standard arguments for fractional
Kelly (variance scaling as f², and the asymmetric penalty for overbetting
under parameter uncertainty) — with no material gap or error against the
corpus. The one piece the corpus made explicit that the derivation reached
only qualitatively: the ~75%-growth-at-¼-variance quantification for
half-Kelly specifically, which falls out of the same g(f) concavity
argument but wasn't computed numerically here.

## Commentary

The genuinely load-bearing insight — multiplicative compounding forces you
to optimize expected *log* wealth rather than expected wealth — is also
the one the corpus takes as a starting axiom rather than re-deriving from
"why not just maximize EV." That's worth flagging as the actual crux for
anyone applying this to Hartley Capital sizing: the entire Kelly apparatus
only *applies* because positions compound sequentially against the same
capital base. A model that risk-sizes off expected-value-per-trade without
that adjustment isn't a simplification of Kelly — it's answering a
different, wrong-for-this-context question. The practical takeaway for the
circuit-breaker backlog item: the current daily/-weekly % breaker is a
reasonable model-free stand-in for fractional-Kelly variance control, but
it inherits the same "percent-space vs. risk-space" ambiguity that the
Kelly literature resolves by normalizing to σ² — which argues for
volatility-normalizing the breaker thresholds rather than leaving them as
flat percentages.
