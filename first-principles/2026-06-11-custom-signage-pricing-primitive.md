# First-Principles Spike: Custom Signage Pricing Primitive

**Date:** 2026-06-11  
**Question:** What is the correct pricing primitive for custom fabricated signage — time-and-materials, fixed-project, or value-based — and which minimizes information asymmetry between buyer and seller?  
**Delta category:** novel

---

## Question

Custom sign shops must choose a pricing structure before a quote can be delivered. The three canonical options are:

1. **Time-and-materials (T&M):** buyer pays for actual hours + actual materials + markup
2. **Fixed-project (FP):** seller quotes a lump sum and bears the risk of overruns
3. **Value-based (VB):** price tied to buyer's estimated economic benefit from the sign

Which structure is *correct*? And "correct" here means: minimizes the dead-weight loss that comes from both parties not knowing what the other knows.

---

## Step 2 — First-Principles Answer

### Decompose a custom sign

A sign is a communication artifact with two separable components:

- **Information content:** the design (logo, copy, layout) — largely a one-time cost that amortizes across units
- **Physical substrate:** materials (vinyl, aluminum, acrylic, LEDs) + fabrication + installation

Installation is where the information asymmetry lives. Before site survey, neither party knows:
- substrate condition (backing material, hidden structural members)
- local permit or code compliance requirements
- revision cycles required by the design approval process

The seller knows fabrication costs well. The buyer knows their budget and their expected ROI from the sign. Neither knows the full install cost until the job is underway.

### Map each pricing model to the asymmetry it creates

**T&M:**
- Seller knows true cost; buyer cannot easily verify labor hours → seller has a pad-hours incentive
- Buyer has no cost certainty → blocks purchasing decisions or forces contingency reserves
- Information asymmetry *shifts to the seller's favor*

**Fixed-price:**
- Seller must over-estimate to protect against unknown install conditions → buyer overpays on average
- If seller under-estimates, quality gets cut or seller absorbs loss → misaligned incentives
- Information asymmetry → both parties price uncertainty into their position → dead-weight loss is the sum of both contingency reserves

**Value-based:**
- Buyer has better information about their own business economics than the seller
- Almost impossible to measure sign ROI with precision; most buyers can't (or won't) quantify conversion lift from a storefront sign
- Requires negotiation overhead disproportionate to the contract value
- Information asymmetry → buyer's advantage, but also buyer's ignorance makes this impractical

### The decision variable

The correct model is a function of one variable: **the ratio of unknown costs to total costs at the time of quote**.

- If unknown costs > ~30% of total: no fixed-price contract can be written without substantial contingency premium → T&M is more efficient
- If unknown costs < ~30% of total (repeat job, standard substrate, previously surveyed site): fixed-price removes seller's pad-hours incentive → FP wins
- If buyer's expected value >> fabrication cost (flagship rebrand, anchor tenant signage): VB is theoretically optimal, but only if buyer is sophisticated enough to negotiate it

### The dominant structure that first principles predicts

A **capped T&M** (time-and-materials with a not-to-exceed ceiling):

- Buyer gets cost certainty (the cap acts like a fixed-price ceiling)
- Seller is protected against scope uncertainty up to the cap
- Both parties have efficiency incentive: if job completes under cap, buyer pays only actuals
- The cap forces the seller to disclose, pre-quote, all known risks that might breach the ceiling → asymmetry is surfaced, not hidden
- For unknowns that emerge mid-job (hidden structural damage, permit delays), the seller must get buyer approval before busting the cap → change order discipline enforced by structure

**First-principles conclusion:** Capped T&M dominates for custom one-off fabrication with partially unknown installation conditions. Fixed-price dominates for repeat/standardized jobs where the seller has cost data from prior identical jobs. Value-based is theoretically superior at high-value strategic installs but informationally impractical for most signage.

---

## Step 3 — Corpus Answer

From trade sources (Sign Builder Illustrated, Sign Trade Supplies, Signs of the Times):

- Industry consensus practice: **fixed-price quoting**, using itemized templates that control markups separately for materials and labor
- The industry's practical solution to information asymmetry: **do the site survey before quoting** — gather photos, permit research, subcontractor quotes, then deliver a fixed-price bid
- Pricing philosophies range from "gut feeling" to "T&M formulas" to overhead-analysis methods; most estimators do not take a scientific approach (estimates are non-uniform across shops)
- No mention of capped T&M as a structure in signage-specific literature
- The concept of *choosing* a pricing model based on a decision variable (unknown/known cost ratio) does not appear; shops pick a model based on convention or owner preference

---

## Step 4 — Delta Analysis

**Category: novel**

The corpus describes *what practitioners do* — survey first, then fixed-price — but doesn't provide a principled framework for:

1. **When** to use T&M vs. FP (the corpus treats it as a preference, not a function of job unknowns)
2. **Capped T&M** as a structure that beats both T&M and FP when unknowns are substantial but not total — this doesn't appear in signage industry literature
3. The **unknown-to-known cost ratio** as an explicit decision variable for model selection

The corpus solution (site survey before quote) is operationally sound but assumes the survey cost is always worth incurring — which it isn't on small or competitive bids. For those cases, the corpus offers no principled alternative. Capped T&M fills that gap.

**Commentary:** The signage industry is operating on a dominant-practice equilibrium (survey → fixed-price) that works for shops with the leverage to demand a pre-quote survey. Shops competing on price or chasing small jobs can't always run that play. A capped T&M structure with a clear change-order process would let them bid competitively without absorbing asymmetric risk. This is common in construction and government contracting but hasn't crossed into the sign trade.

**Confidence:** 0.72 — strong on the structural analysis, moderate on the industry claim (corpus sourced from trade press, not academic survey of shop practices).

---

## Actionable implication for Brand 9 Signs

Default quoting structure:
- **Repeat job, known substrate:** fixed-price with itemized template
- **New client, unvisited site, custom fabrication:** capped T&M — quote materials at cost-plus, quote labor as NTE, change orders priced separately
- **Flagship or strategic install (Hartley Capital properties, anchor tenants):** explore value-based framing for design retainer; fabrication still capped T&M
