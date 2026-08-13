# First-Principles Spike — 2026-08-13

## Question

Should an autonomous trading agent's capital-preservation circuit breaker
(e.g. WOLF's daily -3% / weekly -7% limits) use **fixed percentage loss
thresholds**, or should the threshold be **volatility-adjusted** (scaled to
recent realized vol / ATR, tighter in calm markets and wider in turbulent
ones)?

This is grounded in this repo directly: `WOLF_Command_Center.txt` shows a
live circuit breaker with fixed daily/weekly limits (-3% / -7%) gating a
still-unproven agent (capability 49/100, real money unlocks at 80). Whether
that fixed design is correct, or a known-better vol-adjusted design should
replace it, is exactly the kind of load-bearing architecture question this
spike series exists to pressure-test.

## First-Principles Answer (derived cold, no lookup)

**Primitives.** A circuit breaker exists to stop an agent from continuing to
act once there's enough evidence that (a) the environment no longer matches
the model's assumptions, or (b) the strategy has produced enough contrary
evidence to doubt its edge — and to do so *before* the loss becomes
unrecoverable. Two candidate designs:

1. **Fixed %**: halt at -3% day / -7% week, regardless of context.
2. **Vol-adjusted**: halt when losses exceed what's statistically normal
   given recent realized volatility — tighter in calm regimes, looser in
   turbulent ones.

**Reasoning chain.**

Markets exhibit volatility clustering — calm stretches and turbulent
stretches, each internally more consistent than the boundary between them
would suggest. Under a fixed threshold, a turbulent regime pushes ordinary,
non-informative noise up against the -3%/-7% line more often: the agent gets
stopped out on days where nothing is actually broken, just amplified normal
variance. In a calm regime, the same fixed threshold rarely trips even when
something *is* wrong — a slow strategy decay or a subtle bug can compound
for a long time before -3%/-7% is reached, because ordinary daily noise is
small relative to the threshold. So on pure statistical-detection grounds,
vol-adjusted looks strictly better: it asks "is this abnormal for right
now?" rather than "have we crossed an arbitrary absolute line?"

But detection accuracy isn't the only job a circuit breaker does for an
autonomous agent. It's also a **precommitment device** — a hard constraint
placed by a past, more careful version of the system against a future
version that might be compromised: a bug, a feedback loop, adversarial or
corrupted input, or simple overconfidence after a lucky streak recalibrating
its own risk model. This reframes the vol-adjusted design's key feature —
loosening the stop precisely when volatility is high — as a liability, not a
virtue. High-volatility periods are exactly when regime breaks, liquidity
crunches, and cascading failures happen; letting the stop expand right then
means the device is weakest exactly when danger is greatest. A pure
detection framing wants the threshold to track "normal," but a
capital-preservation framing wants it to track "how much can I afford to
lose before the damage becomes hard to reverse" — a question about the
agent's balance sheet, not about the market's current statistics.

The resolution comes from weighing the asymmetry of the two failure modes.
A **false stop** (halting a still-good strategy on ordinary high-vol noise)
costs forgone profit — bounded, recoverable, cheap to diagnose after the
fact. A **false non-stop** (letting a broken or dangerous strategy keep
running because the vol-adjusted band expanded to cover its losses) costs
capital directly, with a tail that runs toward ruin and is not
recoverable by definition. When one failure mode is bounded and the other is
unbounded/irreversible, the correct design errs toward the bounded one — i.e.
toward simplicity and tightness, not toward loosening in exactly the
conditions that make the unbounded failure mode more likely.

There's a second, independent argument specific to an *unproven* agent (this
is where WOLF sits today, per its own capability score). A vol-adjusted
threshold requires trusting a volatility estimator that the agent itself
computes — another moving part, another place for a bug or miscalibration to
hide, evaluated by the very system whose judgment the circuit breaker exists
to not fully trust yet. A fixed threshold is auditable by a human in five
seconds; a vol-adjusted one requires re-deriving what "normal" meant on the
day in question. Early-stage, low-trust systems should be gated by rules
simple enough that their correctness doesn't depend on the system's own
still-unproven internals.

**Conclusion**: fixed percentage thresholds are the right *floor* for an
autonomous agent that hasn't yet earned trust, precisely because they're
dumb, auditable, and don't loosen when danger is highest. Volatility
adjustment is a legitimate refinement — but it belongs on top of the fixed
floor (e.g. tightening the effective stop in high vol, informing position
sizing) once there's enough of a track record to trust the vol estimator
itself, never as a replacement that lets the hard floor move.

## Corpus Answer

Two independent lines of evidence converge with the reasoning above:

- **Exchange-level circuit breakers are fixed percentage, by design.**
  NYSE/SEC market-wide circuit breakers (Rule 80B) halt trading at fixed
  7% / 13% / 20% declines off the prior day's S&P 500 close — recalculated
  daily against a fixed reference point, but the *threshold logic itself* is
  a simple fixed percentage, not volatility-scaled. This is the closest
  real-world analog to "precommitment device gating an entire system," and
  regulators chose fixed simplicity over statistical sophistication.
- **Practitioner risk-management guidance treats the two mechanisms as
  complementary, not substitutes.** Algo-trading risk literature
  consistently frames fixed daily/weekly/monthly drawdown limits as the
  account-level kill switch ("set in advance, in writing, with explicit
  thresholds"), while volatility-based adjustment shows up separately, at
  the *position-sizing* and *stop-tightening* layer — reducing size or
  tightening stops in high-vol conditions rather than replacing the fixed
  drawdown ceiling. The consistent recommendation is a combined approach:
  fixed limits as the hard floor, volatility awareness layered underneath
  it.

Sources:
- [Market Wide Circuit Breaker — Nasdaq Trader](https://www.nasdaqtrader.com/trader.aspx?id=CircuitBreaker)
- [Report of the Market-Wide Circuit Breaker Working Group — NYSE](https://www.nyse.com/publicdocs/nyse/markets/nyse/Report_of_the_Market-Wide_Circuit_Breaker_Working_Group.pdf)
- [7 Risk Management Strategies for Algorithmic Trading — Nurp](https://nurp.com/algorithmic-trading-blog/7-risk-management-strategies-for-algorithmic-trading/)
- [Reducing Drawdown: 7 Risk-Management Techniques for Algo Traders — Tradetron](https://tradetron.tech/blog/reducing-drawdown-7-risk-management-techniques-for-algo-traders)
- [Dollar Stop Losses vs. Volatility Stop Losses — HackerNoon](https://hackernoon.com/dollar-stop-losses-vs-volatility-stop-losses-algorithmic-trading-tips-oj8j32jv)

## Delta

**Category: rediscovered**

The reasoning chain, run cold from precommitment/asymmetric-cost primitives,
landed on the same structure the corpus independently converged on: a fixed
percentage threshold as the non-negotiable kill switch, with volatility
adjustment as a subordinate refinement layered on top (sizing, stop
tightening) rather than a replacement for the floor. The exchange-level
precedent (NYSE MWCB) is a stronger validation than expected — it's not just
"one plausible practice" but the mechanism a whole market infrastructure
converged on for exactly the precommitment reason derived here.

## Commentary

The interesting part isn't the conclusion (fixed thresholds), it's *why* the
first-principles path and the corpus path agree: both are answering "what
survives an adversarial future version of the thing being gated," not
"what's statistically optimal given known-good assumptions." That's a
useful tell for when reasoning-from-primitives is likely to track the
corpus: whenever a design question is really a trust/precommitment problem
in disguise, simplicity tends to be the load-bearing property, and that's
derivable without needing the domain literature — you just need to ask what
happens when the thing doing the estimating is also the thing you don't
fully trust yet.

For WOLF specifically: keep the fixed -3%/-7% breaker as the hard floor
through at least the current low-capability phase; volatility-aware sizing
or tightening is a reasonable addition *once* capability score and track
record justify trusting the vol estimator, but it should never be allowed to
widen the hard floor.
