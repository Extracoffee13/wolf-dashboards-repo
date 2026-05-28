# First-Principles Spike — 2026-05-28

## Question

**Is a paper-trading Sharpe ratio a valid predictor of live-trading performance, and what multiplier should WOLF apply to its 90-day kill criterion?**

*Operational context:* WOLF Brief kill criterion is paper Sharpe < 1.0 at Day 90 (2026-07-30). Is 1.0 the right threshold, or is the criterion miscalibrated?

---

## First-Principles Answer (no retrieval)

**What does Sharpe measure?**  
`Sharpe = (E[r] − r_f) / σ(r)` — excess return per unit of volatility. It measures *signal quality*: whether directional calls are right, and by how much. Paper trading isolates signal quality from friction.

**What live trading adds that paper trading omits:**

1. **Bid-ask spread** — every round-trip costs at minimum the spread. For daily macro calls on liquid ETFs, ~2–5 bps per trade. Low per trade; compounds with frequency.
2. **Execution latency** — signal exists at T, execution happens at T+ε. Daily macro calls are low-frequency, so latency decay is modest.
3. **Market impact** — at small AUM (WOLF's early stage), negligible. Becomes dominant at scale.
4. **Behavioral/psychological cost** — this is the *largest* unmeasured variable. Paper drawdowns don't trigger real loss aversion. Live investors cut at the worst moment. An AI committee never flinches at a drawdown; real readers who follow the thesis do. Their realized Sharpe is lower than the committee's stated Sharpe.
5. **Fill quality** — fills happen at inside ask (buying) or bid (selling); queue depth adds further slippage.

**Magnitude of degradation for WOLF's profile:**  
WOLF is fundamentally-driven, daily cadence, liquid instruments, small AUM. Friction items 1–3 are minor. Item 4 (behavioral) is the dominant driver of the paper-to-live gap.

Estimated haircut: **20–40%** for a committee-style macro strategy.

| Paper Sharpe | Expected live Sharpe |
|---|---|
| 1.0 | ~0.6–0.8 |
| 1.4 | ~0.85–1.1 |
| 1.5 | ~0.9–1.2 |
| 2.0 | ~1.2–1.6 |

**Estimation noise:**  
A 90-day window is ~63 trading days. Standard error of the Sharpe estimator ≈ `1/√63 ≈ 0.13`. A measured paper Sharpe of 1.0 has a 95% CI of approximately [0.74, 1.26]. The point estimate is noisy; a borderline reading is statistically uninformative.

**First-principles conclusion:**  
Kill criterion of paper Sharpe < 1.0 is set too low. A 1.0 paper Sharpe likely implies live Sharpe of ~0.6–0.8 — not compelling to a family office. Recommended recalibration: require paper Sharpe ≥ **1.4–1.5** to have reasonable confidence in live Sharpe ≥ 1.0. Additionally, apply Lo's standard error adjustment: a measured 1.4 over 63 days is statistically significant vs. zero but has wide confidence intervals. Track record extension to 180 days halves the estimation noise.

---

## Corpus Answer (after search)

**Implementation shortfall (Perold, 1988):** The formal framework for measuring the gap between paper-portfolio performance and live execution. The gap is caused by bid-ask spread, market impact, and timing slippage.

**Institutional practice:** Quant funds require backtested Sharpe ≥ 2.0–2.5 before live deployment consideration. The high threshold exists primarily because of *overfitting risk* in data-mined algorithmic strategies, not just friction. After haircuts, live Sharpe ≥ 1.0–1.5 is considered acceptable.

**Lo (2002) — Statistics of Sharpe Ratios:** Formally derived the sampling distribution of the Sharpe ratio. Shows that autocorrelation in returns can materially bias inference; provides explicit standard error formula. Short track records (< 60 days) produce very noisy estimates.

**Probabilistic Sharpe Ratio (PSR):** Extends Lo's work by asking: *given a sample Sharpe over N observations, what is the probability that the true Sharpe exceeds a benchmark?* Answers the exact operational question WOLF needs — minimum track record length to achieve a given statistical confidence.

---

## Delta Analysis

**Category: `rediscovered`**

The first-principles chain correctly arrived at the core corpus answer: paper Sharpe overstates live Sharpe, the gap is friction-driven, and the kill criterion needs a buffer above 1.0. The 20–40% haircut estimate aligns with the institutional practice of requiring 2.0–2.5x the target live Sharpe in backtest.

The estimation-noise argument was independently derived and matches Lo (2002) — the standard error formula `SE ≈ 1/√T` is correct for i.i.d. returns.

**Where first principles fell short:**  
The corpus distinguishes *friction degradation* (what I derived) from *overfitting degradation* (dominant concern for algorithmic strategies). For WOLF, overfitting isn't the concern (no historical data was curve-fit), but the corpus doesn't cleanly separate these two failure modes in most accessible material. The PSR framework was not independently derived — it would have required knowing that "confidence interval around Sharpe" had already been formalized.

**Novel angle not in corpus:**  
The corpus frames paper-to-live degradation as a *strategy* problem. For WOLF, the primary degradation channel is *reader behavioral friction* — the committee achieves paper Sharpe X, but readers following the thesis achieve lower realized returns due to delayed entry, early exit under drawdown, and incomplete position sizing. This means WOLF's actual success metric should not be committee paper Sharpe alone but **reader tracking error** — how closely do readers actually replicate the stated thesis. The corpus has no direct treatment of this.

---

## Commentary

For WOLF's kill criterion: raise from 1.0 to **1.4** minimum, and consider supplementing with PSR at 80% confidence level as the formal gate. Also instrument reader behavior (e.g., poll whether readers actually made the thesis trade) to surface the behavioral tracking gap.

The 90-day window is statistically thin. Extending the proof to 180 days before the kill/continue/double-down vote would halve Sharpe estimation noise without materially delaying the decision — the current Day 90 vote date of 2026-07-30 could become a *preliminary* vote with a final at Day 180 (2026-10-19).
