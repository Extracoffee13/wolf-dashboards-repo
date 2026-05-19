# Spike: Does ranking trading strategies by Sharpe ratio correctly identify the best strategy for compounded wealth growth?

**Date:** 2026-05-19  
**Relevance:** WOLF strategy grader ranks three strategies by Sharpe (1.50→A, 1.76→A, 1.91→A+). Is that ranking valid for maximizing long-run wealth?

---

## First-Principles Answer

### Primitives

**P1 — Compounding is multiplicative.**  
Return sequences multiply. A +20% followed by -20% = 0.96 — a loss. The metric that matters for long-run wealth is the geometric mean, not the arithmetic mean.

**P2 — Variance drag identity.**  
For a log-normal return stream:

```
g ≈ μ − σ²/2
```

where `g` is the geometric (compounded) mean, `μ` is the arithmetic mean, and `σ` is volatility. Volatility is not merely "risk" — it is a direct, mathematical tax on compounded returns. This identity is exact for continuous compounding.

**P3 — What Sharpe encodes.**  
Sharpe ratio `S = (μ − Rf) / σ`. It captures arithmetic excess return per unit of volatility. It does NOT subtract `σ²/2`. Two strategies with identical Sharpe but different `σ` have very different geometric means.

**P4 — Derive the ranking condition.**  
Strategy A beats B in compounded growth iff:

```
S_A · σ_A − σ_A²/2  >  S_B · σ_B − σ_B²/2
```

This is NOT equivalent to `S_A > S_B` unless `σ_A ≈ σ_B`.

**Counter-example:**
- Strategy A: S=2.0, σ=5%  → g_excess ≈ 0.100 − 0.00125 = **9.9%**
- Strategy B: S=1.5, σ=40% → g_excess ≈ 0.600 − 0.080  = **52.0%**

Strategy B dominates despite a *lower* Sharpe, because the absolute return (S×σ) swamps the variance drag.

**P5 — When does Sharpe ranking hold?**  
If and only if σ_A ≈ σ_B. With equal volatility: `g_A − g_B = (S_A − S_B) · σ > 0`, so higher Sharpe always wins at the same risk level. Sharpe is a *conditional* proxy for compounded growth.

**P6 — Kelly optimum ties the two together.**  
Optimal volatility for max geometric growth: `σ* = S` (in annualized natural units). At that sizing: `g_max = S²/2`. Maximum geometric growth scales as the *square* of Sharpe — but only if the strategy is sized to its Kelly optimum. A Sharpe-1.5 strategy sized at 40% vol beats a Sharpe-2.0 strategy sized at 5% vol, but the Sharpe-2.0 strategy can deliver `2.0²/2 = 2.0×` the growth of the Sharpe-1.5 strategy if both are sized to their Kelly optima.

### Conclusion (first principles)

Sharpe ratio ranking is a *valid but conditional* proxy for compounded growth ranking. It is valid only when strategies are compared at the same volatility level. When volatilities differ, the correct ranking metric is the geometric excess return `g_excess = S·σ − σ²/2` evaluated at actual or intended operating volatility. For WOLF's strategy grader to produce correct A/B/C grades, the three strategies must have comparable σ — or the grader should compute geometric returns directly.

---

## Corpus Answer

The quantitative finance literature confirms this conclusion under multiple frameworks:

1. **Geometric Mean Maximization (GMM)** — Estrada (2010) and others show GMM and Sharpe-maximization produce different rankings when strategies have differing volatilities. "The Sharpe ratio may not be superior to the alternative criterion of maximizing the geometric mean return."

2. **Kelly Criterion** — The Kelly-optimal leverage that maximizes long-run geometric growth equals `S/σ` (full Kelly). Full Kelly portfolio volatility equals the Sharpe ratio. At full Kelly, `g_max = S²/2`, scaling as the square of Sharpe.

3. **Capital Market Parabola** — In risk-return space, the geometric growth rate traces a parabola. Peak growth is at `σ = S`; both lower and higher volatility reduce compounded returns. Sharpe is the slope of the line through the origin to any point on the parabola — not the height of the parabola.

4. **Variance drag** — Universally acknowledged as `μ − σ²/2` for log-normal returns. All three references name it explicitly as the mechanism by which volatility suppresses geometric returns.

**Orthodox conclusion:** Sharpe ranking correctly ranks strategies for *risk-adjusted arithmetic return*, not for *compounded wealth growth*, unless volatility is held constant. The correct metric for compounded growth ranking is the geometric Sharpe ratio (also called the Geometric Holding Period Return, GHPR) or equivalently `S·σ − σ²/2` evaluated at operating volatility.

---

## Delta Comparison

| Dimension | First-Principles | Corpus |
|-----------|-----------------|--------|
| Variance drag identity `g ≈ μ − σ²/2` | Derived ✓ | Confirmed ✓ |
| Sharpe ranking conditional on equal σ | Derived ✓ | Confirmed ✓ |
| Kelly optimum `σ* = S` | Derived ✓ | Confirmed ✓ |
| Max geometric growth = `S²/2` | Derived ✓ | Confirmed ✓ |
| Geometric Sharpe as correct metric | Named implicitly | Named explicitly |

**Delta category: `rediscovered`**

The first-principles chain arrived independently at all four core results in the literature. The only addition from the corpus was the named artifact — "Geometric Sharpe" / "Capital Market Parabola" — which gives the result a handle for communication.

---

## Commentary

**For WOLF:** The strategy grader's Sharpe-based grades (1.91 → A+) are correct *if* the three strategies operate at similar annualized volatility. If their actual σ values are e.g. 8%, 12%, 20%, the ranking should be recomputed using `S·σ − σ²/2`. The strategy with the highest *geometric excess return* at its expected operating volatility wins, not the highest Sharpe.

**Durable rule:** Use Sharpe to compare strategies at equal volatility or to set leverage. Use geometric mean (or `S·σ − σ²/2`) to rank strategies for compounded wealth at their actual operating volatility.
