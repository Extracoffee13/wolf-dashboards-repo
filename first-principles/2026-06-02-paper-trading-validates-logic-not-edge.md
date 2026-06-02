# Spike: Does a paper-trading track record validate a strategy's edge, or only its alpha-generating logic?

**Date:** 2026-06-02
**Relevance:** WOLF Brief Day-60 real-money unlock review is 2026-06-07. The kill criterion requires paper Sharpe ≥ 1.0. This question asks what that criterion actually proves.

---

## First-Principles Answer

### Decompose "edge"

Edge = positive expected value per trade, sustained over a statistically meaningful sample. It has exactly **two separable components**:

1. **Alpha logic** — the belief/signal that a price will move in a predictable direction
2. **Execution capability** — the ability to convert that prediction into realized P&L at real fills, at real scale

These are distinct systems. One can be valid while the other fails completely.

### What paper trading measures

Paper trading simulates entry and exit at observed market prices with no capital at risk. It measures whether the alpha logic was directionally correct at *theoretical* fill prices. Nothing more.

### What paper trading cannot measure

| Gap | Why it's structural |
|-----|---------------------|
| **Slippage** | Your real order moves the bid/ask; theoretical fills assume zero market impact |
| **Liquidity constraints** | Strategy may require more size than daily volume allows |
| **Spread cost** | Real execution eats the bid/ask; paper often fills at mid |
| **Borrow cost** | Short positions have real lending fees; paper books ignore them |
| **Drawdown survivability** | A real margin call or risk-manager stops the position before the thesis plays out; paper lets you hold forever |
| **Behavioral divergence** | Real capital creates loss aversion and anchoring; simulated capital doesn't |
| **Capacity threshold** | At what AUM does market impact self-defeat the strategy? Paper doesn't surface this |

### The key structural insight

All unmeasured frictions run in **one direction**: against the trader. The gap between paper and live P&L is not random noise — it is systematic and always negative. This means a paper Sharpe of 1.0 is an *upper bound* on live Sharpe, not a point estimate.

### Conclusion

Paper trading validates **alpha logic**. Edge requires alpha logic *plus* execution capability. A paper Sharpe ≥ 1.0 is the entrance criterion to the live-execution question — necessary but not sufficient for real-money deployment.

For WOLF specifically, additional questions Day-60 should surface:
- Would these trades have been executable at the assumed fill prices? (fill quality audit)
- Did the committee actually hold to its stated thesis through interim drawdowns, or did behavioral drift change the book mid-period? (behavioral coherence check)
- At what AUM would market impact start degrading the Sharpe? (capacity analysis)

---

## Corpus Answer

Orthodox quant finance and practitioner literature confirms:

- Paper trading is a necessary but insufficient validation hurdle
- **Over 90% of academic strategies fail in live implementation** (consistent finding across quant practitioners)
- Paper bots fill at mid-price ~90% of the time; live bots only ~60% — a structural fill-quality gap
- Residual implementation effects account for roughly -2.7% in documented case studies
- Recommended validation stack: paper trading + out-of-sample testing + walk-forward validation + realistic transaction-cost modeling + multi-instrument testing

Key references from corpus:
- Practitioner work on paper vs. live slippage analysis (markrbest.github.io)
- Institutional research: 90%+ academic strategy failure rate at live implementation
- Quant frameworks: walk-forward validation as the bridge between paper and live

---

## Delta Analysis

**Category: `rediscovered`**

My first-principles reasoning arrived independently at the same core truth: paper trading validates signal direction, not execution capability, and the gap is structural not random.

**Where my framing adds precision the corpus doesn't explicitly state:**

1. **Two-system decomposition** — naming alpha logic and execution capability as *separable systems* (not just a list of problems) gives a cleaner mental model for what Day-60 actually proves
2. **Directional asymmetry as a principle** — the corpus shows the gap exists; my framing names it as structurally one-directional (all frictions run against the trader), making the paper Sharpe an upper bound rather than a noisy estimate
3. **Behavioral coherence as a distinct measurable** — whether a committee *actually held its stated thesis* through drawdowns is testable in a structured process like WOLF but the corpus doesn't highlight this as a separate audit item
4. **Capacity threshold framing** — the corpus covers market impact but frames it as a problem; my framing frames it as a specific question (at what AUM does the strategy self-defeat?) which is actionable for WOLF's monetization path

**Not novel in substance** — the corpus has all the ingredients. Novel in structure and actionability for this specific use case.

---

## Commentary

The WOLF Brief kill criterion (paper Sharpe ≥ 1.0 by Day-90) is correctly scoped as a *necessary* gate, not a sufficient one. What it actually validates is that the four-role committee's alpha-generating logic has directional validity over a 90-day out-of-sample window. That's valuable: most committees can't achieve this.

What it doesn't validate is whether WOLF can execute that logic profitably with real capital. The Day-60 and Day-90 reviews are the right structure. The recommendation from this spike: add an explicit **fill-quality audit** and **behavioral coherence review** to the Day-60 checklist — not just the headline Sharpe number.
