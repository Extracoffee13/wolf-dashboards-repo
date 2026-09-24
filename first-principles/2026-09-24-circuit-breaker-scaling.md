# First-Principles Spike — 2026-09-24

## Question

WOLF's live risk config trips a daily loss circuit breaker and a separate
weekly loss circuit breaker. There are 5 trading days in a week. Should the
weekly threshold be set at **5× the daily threshold** (linear scaling), or
does some other multiple follow from first principles?

## First-principles derivation (no retrieval)

**1. What a circuit breaker is for.** It exists to halt an agent before a
sequence of losses compounds past a recoverable point, calibrated so it
doesn't trip on ordinary day-to-day noise but does trip before a genuine
breakdown. Two design failure modes to avoid: too tight (trips on noise,
destroys the strategy's ability to run) and too loose (fails to protect
capital before it's too late).

**2. The simplest model of daily P&L.** Absent any other information, model
daily returns as a sequence of roughly independent, identically distributed
random draws — a random walk. This is the null hypothesis; deviations from
it (autocorrelation, regime clustering, fat tails) are corrections to layer
on afterward, not the starting point.

**3. How variance behaves under independence.** For independent random
variables, variances add: Var(sum of N draws) = N × Var(single draw).
Standard deviation — which is what a "percent move" threshold is really
denominated in — is the square root of variance, so it scales as √N, not N.
Five trading days of independent daily P&L therefore has a standard
deviation of √5 ≈ 2.236× the single-day standard deviation, not 5×.

**4. Why linear (5×) scaling is wrong, concretely.** If the daily threshold
is calibrated at k standard deviations of daily returns (choose k so the
breaker trips rarely enough not to interfere with normal operation but
reliably before real damage), the *equivalent* weekly threshold — the one
that trips at the same k-sigma confidence level after 5 days of typical
(not worst-case) daily noise — is k·σ_day·√5. A 5×-daily weekly cap is
therefore roughly 2.2× looser than the statistically equivalent bound. That
slack is not free: it means a portfolio could bleed steadily below the
weekly-equivalent noise band on 4 separate days without ever tripping the
daily breaker, and still have headroom left under the 5×-linear weekly cap
that a properly √N-scaled breaker would already have caught. Linear scaling
implicitly assumes the daily edge case (the worst day) repeats identically
every day — but that scenario is already what the daily breaker is *for*.
The weekly breaker's actual job is to catch the case the daily breaker
structurally can't see: typical noise accumulating across days without any
single day looking extreme. That's a statistical accumulation question, so
it needs a statistical accumulation answer.

**5. First correction — autocorrelation.** Real daily returns are not
perfectly independent. Short-horizon mean reversion (today's loss partially
reverses tomorrow) would pull the true multiplier below √5. Momentum,
regime persistence, or a strategy actively digging itself deeper (a stuck
position, a trend against it) would push the multiplier above √5, because
losses are no longer independent draws but correlated in the bad direction.

**6. Second correction — fat tails.** The Gaussian assumption underlying
step 3 understates the probability of large joint moves. Real market
return distributions have heavier tails than a Gaussian, so purely
√N-scaling a Gaussian-calibrated daily threshold will under-protect against
the joint-extreme-days scenario. A prudent design pads the statistical
multiplier with a safety margin above √5 to compensate — not all the way
back to 5, but somewhat above 2.236, landing in something like a 2.2–3×
band depending on how fat the tails are judged to be.

**7. Conclusion.** From first principles: weekly threshold ≈ daily
threshold × √5 (≈2.24×) as a baseline, nudged upward from there — not to
5×, and not exactly to 2.24× either — to account for fat tails and possible
positive autocorrelation in a losing streak. The right answer is "roughly
2.2×–3×, derived from the square root of elapsed independent periods, not
from the linear day-count."

## Corpus answer

Web search on the standard quantitative-finance treatment confirms this is
a named, well-established result: the **square-root-of-time rule** for
scaling volatility / Value-at-Risk across horizons. The rule states that to
convert a higher-frequency volatility estimate to a lower-frequency one,
multiply by the square root of the ratio of sample counts (e.g. daily VaR
to weekly VaR uses √5, or √7 if scaling by calendar rather than trading
days). This is exactly the same derivation as above (variance additivity
under i.i.d. returns → std dev scales as √N), and the standard literature
carries the same caveat independently arrived at in step 5–6 above: the
rule "works only under the assumption of iid Gaussian returns," and "serial
dependence and heavy-tailedness... can lead to a systematic underestimation
of risk" when applied naively (Danielsson et al.; Journal of Risk empirical
studies on the rule's accuracy across market indexes).

Sources:
- [Square Root of Time Rule — Gregory Gundersen](https://gregorygundersen.com/blog/2022/05/24/square-root-of-time-rule/)
- [On time-scaling of risk and the square-root-of-time rule — Danielsson et al. (LSE)](https://eprints.lse.ac.uk/24827/1/dp439.pdf)
- [Scaling by the square-root-of-time rule: an empirical investigation using five market indexes — Journal of Risk](https://www.risk.net/journal-of-risk/2475516/scaling-by-the-square-root-of-time-rule-an-empirical-investigation-using-five-market-indexes)

## Sanity check against WOLF's own live config

`wolf_live_data.json` (2026-06-24 snapshot) reports:
`"Daily: -1.3% (buf: 1.7%) | Weekly: -3.9% (buf: 3.1%)"`. Reconstructing the
actual limits from actual-loss + remaining-buffer: daily limit ≈ -3.0%,
weekly limit ≈ -7.0%. That's a ratio of 7/3 ≈ **2.33×** — not 5×, and close
to the √5 ≈ 2.236× baseline derived above (with a small margin on top,
consistent with the fat-tail correction in step 6). WOLF's actual
circuit-breaker configuration already follows statistically-correct
time-scaling rather than naive linear scaling, whether or not that was the
explicit design intent.

## Delta category: **rediscovered**

The first-principles derivation arrived independently at the
square-root-of-time rule (and its Gaussian/iid caveats) before any search
was performed, matching the named standard result in quantitative risk
management almost exactly. This validates the reasoning chain from
variance-additivity-under-independence through to the √N scaling law, and
turned up a useful, unprompted confirmation that WOLF's own live risk
config (2.33×) already sits close to the theoretically correct multiple
rather than the naive linear one.

## Commentary

The interesting part isn't that √N scaling exists — it's *why* linear
scaling is the wrong intuition to reach for by default: it implicitly
conflates "the daily breaker's job" (catch one bad day) with "the weekly
breaker's job" (catch accumulated typical-noise drift across days), and the
day-count is the wrong unit to scale by once you notice those are different
failure modes. The fat-tail caveat is also worth carrying forward: any
agent-authored risk threshold derived by "clean" √N scaling should get a
deliberate margin added, not shipped at the theoretical minimum — the same
correction quant risk teams apply in practice.
