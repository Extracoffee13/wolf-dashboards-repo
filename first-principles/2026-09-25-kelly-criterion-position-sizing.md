# First-Principles Spike — 2026-09-25

## Question

From first principles, why does the Kelly criterion determine optimal position
sizing for a strategy with a known win rate and payoff ratio? (Picked from
`first-principles-backlog.md`, Trading / WOLF / Hartley Capital section — directly
relevant to WOLF's approved-strategy sizing and its -3%/-7% circuit breaker.)

## First-principles answer (derived, no retrieval)

Start from what "optimal" has to mean for a bet that gets repeated many times
with capital that compounds. Two candidate objectives compete: maximize
*expected wealth* after N bets, or maximize the *long-run growth rate* of
wealth. These are not the same thing, and the difference is the whole
question.

If you size bets as a fixed fraction `f` of current wealth (not a fixed
dollar amount — this matters, see below), wealth after N rounds is a
*product* of per-round multipliers, not a sum:

  W_N = W_0 · M_1 · M_2 · ... · M_N

where each M_i is `(1 + b·f)` on a win (probability p) or `(1 − f)` on a loss
(probability q = 1 − p), and b is the payoff ratio (win pays b units per unit
staked).

Maximizing E[W_N] directly is a trap: expected value is dominated by
astronomically unlikely, astronomically large outcomes, and the formula that
maximizes it is "bet everything, every time" (f = 1), which hits a loss
eventually and hits it at f = 1, meaning total ruin with probability 1 as N
grows. Expected-value maximization is the wrong objective whenever outcomes
compound multiplicatively, because the arithmetic mean of the multipliers is
not what determines where your wealth actually ends up — the *typical*
trajectory (what happens with probability → 1 as N → ∞) is governed by the
mean of the *logs* of the multipliers, by the law of large numbers:

  (1/N)·ln(W_N / W_0) = (1/N)·Σ ln(M_i) → E[ln M]   almost surely

So the growth rate that a single long-run realization actually experiences is
g(f) = E[ln M] = p·ln(1 + b·f) + q·ln(1 − f). This is the right objective:
maximize the almost-sure long-run exponential growth rate, not the expected
value of a single draw from a fat-tailed distribution.

Now it's a one-variable calculus problem. Differentiate g with respect to f
and set to zero:

  g'(f) = p·b / (1 + b·f) − q / (1 − f) = 0

  ⇒ p·b·(1 − f) = q·(1 + b·f)
  ⇒ p·b − p·b·f = q + q·b·f
  ⇒ p·b − q = b·f·(p + q)
  ⇒ p·b − q = b·f            (since p + q = 1)
  ⇒ f* = (b·p − q) / b  =  p − q/b

The second derivative g''(f) = −p·b²/(1+bf)² − q/(1−f)² is always negative on
the feasible range, so this critical point is a maximum, not a saddle — the
growth-rate objective is concave in f, so there's a unique best fraction, not
just a best direction.

A few things fall out of the formula itself, for free:

- **Edge determines direction and magnitude.** f* > 0 exactly when b·p > q,
  i.e., when expected value per unit staked (b·p − q) is positive — no edge,
  no bet, which matches intuition: you can't out-position-size a losing
  strategy.
- **f* scales with edge, not just with win rate.** A high win rate with a
  poor payoff ratio (small b) can still yield a small or negative f*; a low
  win rate with a large payoff ratio can yield a large f*. Win rate alone
  (WOLF's dashboards track WR%) is an incomplete sizing input without b.
- **The multiplicative-compounding assumption is load-bearing.** If bets were
  sized as a fixed dollar amount instead of a fixed fraction of current
  capital, wealth would be a sum, not a product, the log-growth argument
  wouldn't apply, and there'd be no interior optimum at all — you'd just
  maximize expected dollar value per bet, unboundedly. Kelly sizing is
  specifically a consequence of position size being a fraction of a
  compounding account, which is exactly how WOLF's buying-power-based sizing
  works.
- **Full Kelly is provably growth-optimal but not the only reasonable
  choice.** Nothing in the derivation says growth rate is the only thing
  that matters — path variance (drawdown) along the way is a separate axis
  the derivation doesn't price in at all, since g(f) only captures the
  long-run slope, not the volatility of getting there. That's a genuine gap
  in the first-principles argument, not a refinement of it — closing it
  requires a second objective (e.g., bounding ruin probability or drawdown)
  layered on top, which is a different optimization problem.

## Corpus answer (found via web search)

Search confirms the standard result matches the derivation exactly: the
canonical Kelly formula is stated as **f\* = (b·p − q) / b**, with b the
payout odds, p the win probability, q = 1 − p. Multiple sources (Corporate
Finance Institute, market-math explainers, quant-practice writeups) describe
the derivation the same way — maximize expected log-wealth (log-utility) over
repeated multiplicative bets, which "maximizes the geometric growth rate of
capital." The origin is also as recalled: John Kelly derived it at Bell Labs
in 1956, originally in the context of Shannon's information theory applied to
noisy communication channels, with the bet-sizing formula falling out as a
side result.

The corpus adds one thing the pure derivation above flags as a gap but
doesn't resolve: **practitioners essentially never use full Kelly**. Because
edge estimates (p and b) are themselves uncertain and errors in estimating
edge get amplified by the sizing formula, industry practice uses *fractional*
Kelly (commonly half- or quarter-Kelly) — same growth direction, much lower
variance, explicitly trading some growth rate for reduced estimation risk and
drawdown. This is precisely the "close the gap with a second objective"
step the first-principles reasoning above identified as necessary but did not
perform.

## Delta category: **rediscovered**

The derivation arrived at the exact canonical formula (f* = (bp − q)/b) and
the exact canonical justification (maximize expected log-wealth because
wealth compounds multiplicatively, per the law of large numbers) independently,
without having seen it this session. The corpus didn't correct anything in
the math — it validated it — and its one addition (fractional Kelly in
practice) was already anticipated as an open gap in the reasoning ("path
variance is a separate axis the derivation doesn't price in"), just not
solved. That's a real but narrow miss, not a wrong turn.

## Commentary

The interesting part of this spike isn't that Kelly is a known formula — it's
that the *reason* for concavity/multiplicativity (why fixed-fraction sizing
on compounding capital produces a unique interior optimum, while fixed-dollar
sizing wouldn't) is a structural fact about the betting/trading setup, not
about the formula. That structural fact — WOLF sizes as a fraction of
buying power, which is exactly the regime Kelly requires — is directly
actionable: it says WOLF's approved-strategy sizing (Sharpe/DD/WR tracked per
strategy) is missing the one number the formula actually needs, the payoff
ratio b, to compute a principled f* per strategy rather than a fixed or
ad-hoc allocation. That's a candidate follow-up, not something this spike
implements.
