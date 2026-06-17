# Why Cap Rates Dominate Commercial Real Estate Pricing

**Date:** 2026-06-17  
**Category:** rediscovered  
**Confidence:** 0.85

---

## Question

Why do cap rates exist as the dominant pricing convention in commercial real estate, and what would emerge to replace them if they were abandoned?

---

## First-Principles Answer

*Derived before any retrieval.*

Commercial real estate is a claim on future net cash flows. Money has time value. Investors compare across competing options. Information must compress into a portable signal.

From these primitives: the value of a stabilized income asset approximates a perpetuity — **V = NOI / r**, which rearranges to **r = NOI / V**. That ratio is cap rate. It falls out of the math before any convention is invented.

**Why this metric and not alternatives?**

| Convention | Failure mode |
|---|---|
| Price per sq ft | Ignores vacancy, lease terms, expense ratios |
| Gross Rent Multiplier | Ignores operating expenses; two buildings at 40% and 60% expense ratios look identical |
| DCF | Terminal value sensitivity makes it four-analyst, four-answer; not portable |
| Cash-on-cash return | Leverage-dependent; changes when the loan changes, so you can't compare across capital structures |

Cap rate survives because it hits the right level of abstraction:
1. **Net income, not gross** — cleans out operating efficiency differences
2. **Leverage-neutral** — the underlying asset is priced, not the financing stack
3. **Snapshot, no forecast required** — current NOI suffices
4. **Scale-invariant** — a $1M and a $500M deal share the same metric

The deeper principle: the best pricing convention for an income asset is the one that is (a) derivable from the asset's fundamental income/value relationship, (b) leverage-neutral, and (c) requires minimum forward assumptions. Cap rate satisfies all three. If it vanished, NOI yield would emerge in its place — which is cap rate by another name. The concept is overdetermined by the math.

---

## Corpus Answer

Standard formulation: **cap rate = NOI / current market value**. Derived from perpetuity pricing.

The Gordon Growth Model extension: **cap rate ≈ required return − growth expectations (r − g)**. This explains cross-market variation — gateway markets (NYC, SF) trade at 4% caps because investors price in higher rent growth (g is large); secondary/tertiary markets trade at 8–10% caps because growth expectations are lower.

Cap rate also embeds a risk premium above the risk-free rate. The corpus explains survival over alternatives primarily via market convention and network effects — everyone uses it because everyone uses it.

---

## Delta Analysis

**Category: rediscovered**

The first-principles derivation arrived at the same math (perpetuity formula → r = NOI / V) and the same conclusion (cap rate is the natural survivor among alternatives).

**What the corpus adds:** The Gordon Growth Model decomposition (cap rate = r − g) formalizes why cross-market cap rate spreads exist. This was gestured at but not fully formalized in the first-principles pass. Genuine addition.

**Where framing diverged:** The corpus explains cap rate's dominance largely as convention/network effect. The first-principles pass derived it from information sufficiency — cap rate is the *minimal sufficient statistic* for an unlevered income asset. That framing (information-theoretic, not sociological) doesn't appear prominently in standard corpus explanations of why cap rate beats GRM.

**Lesson:** When a convention is mathematically overdetermined, "network effects" is a weak explanation for its dominance — the real explanation is that it's the inevitable compression of a small set of primitives. Agents reasoning about industry conventions should first ask whether the convention is mathematically forced before attributing it to history or path dependence.
