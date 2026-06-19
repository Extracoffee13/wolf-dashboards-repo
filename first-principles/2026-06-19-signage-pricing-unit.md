# First-Principles Spike: Signage Pricing Unit

**Date:** 2026-06-19
**Question:** What is the correct unit of pricing for custom sign fabrication work, and what cost structure should determine it?
**Delta category:** rediscovered

---

## Step 1 — First-Principles Derivation

*(Reasoning only — no retrieval at this stage.)*

### Decompose the cost structure

Custom sign fabrication has four cost categories:

1. **Materials** — substrate (aluminum, acrylic, PVC, MDO, foam board), ink/vinyl, hardware, electrical components. These scale roughly with physical size and material choice, but type dominates: a 4 sq ft neon unit uses completely different materials than a 4 sq ft vinyl banner.

2. **Labor** — three distinct phases with different scaling laws:
   - *Design*: scales with complexity, not size. A simple large banner may be trivially fast; a complex small dimensional logo may take hours.
   - *Fabrication*: scales with size × material difficulty × method (CNC routing vs. hand-cut vs. cast metal vs. illuminated cabinet assembly). Not proportional to sq footage across job types.
   - *Installation*: scales with height, weight, substrate, access difficulty, and electrical requirements — almost entirely decoupled from fabrication square footage.

3. **Fixed overhead** — shop rent, equipment depreciation (CNC router, wide-format printer, laser, vehicle fleet), insurance. These are sunk and must be recovered by volume × margin. They don't scale per job.

4. **Variable overhead** — permits, lift/boom rental, subcontractor electrical, travel. These are highly job-specific and often unpredictable.

### What is the natural pricing unit?

For a pricing unit to work, it must be (a) proportional to actual cost, and (b) communicable to customers.

**Square footage** is the industry default for communicability. It fails the proportionality test across job types: the per-sqft cost of illuminated channel letters is 10–30× the per-sqft cost of a vinyl banner. When you use sq footage as the primary axis, you must attach a complexity multiplier so large that it swallows the utility of the metric.

**Time and materials (T&M)** is proportional to actual cost for labor-dominant jobs, but customers distrust open-ended T&M quotes because they bear the estimation risk.

**Flat job quote (itemized internally, fixed-price externally)** satisfies both requirements: internally you build it from materials + labor + overhead + margin; externally the customer sees a single price. This is what contractors call "lump-sum fixed-price."

### The structural insight

**Every custom job has a setup cost floor** that is roughly independent of job size: customer contact, design iteration, job programming, scheduling. For a small shop this might be $200–$500 per job. This means:
- A minimum job price must exist — below it you destroy value regardless of how little material is used.
- Volume discounts are only valid when variable costs (materials) dominate, not when fixed-per-job setup costs dominate.

**Installation is structurally independent from fabrication size.** A 2 sq ft illuminated sign installed at 30 feet on a masonry wall may cost $1,500 to install. A 50 sq ft vinyl banner hung from a fence may cost $200 to install. Any pricing model that treats installation as proportional to fabrication sq footage will systematically underprice complex installs.

### First-principles conclusion

> The correct pricing unit for custom sign fabrication is **the job**, priced as a lump sum derived from itemized cost components: Σ(materials × material markup) + Σ(labor hours × fully-loaded shop rate) + variable overhead + risk premium for novelty + profit margin, subject to a minimum job floor.
>
> Square footage is a useful sanity-check heuristic when comparing similar job types, not a primary pricing axis. The axis that explains cost variance across job types is labor hours × complexity — not size.

---

## Step 2 — Corpus Answer

*(Search results from signage industry sources.)*

**What the corpus says:**

- Square footage is the dominant customer-facing pricing axis. Industry ranges: $5/sqft (vinyl banners) to $300/sqft (illuminated custom signs), with the wide variance explicitly attributed to material type and complexity.
- Design labor is quoted at $50–$150/hr independently.
- Installation is cited as $2,000–$5,000 typical, and treated as a separate line item (not folded into sq footage).
- Complexity multipliers are widely used on top of sq footage.
- **Job costing** (itemized materials + labor + overhead) is explicitly recommended in manufacturing/fabrication management literature as the correct *internal* model for accurate quoting.
- Sources: Signs101 forum, Sign Builder Illustrated, Angi, ISA Sign Cost Guide.

**Orthodox practitioner framing:**

"Use sq footage for the customer-facing quote; use job costing internally to make sure you're covered." Many shops use estimating software (Cyrious, ShopVox, Estimate) that generates itemized job cost and then produces a customer price.

---

## Step 3 — Delta Analysis

| Dimension | First-Principles | Corpus |
|-----------|-----------------|--------|
| Correct internal model | Job costing (itemized) | Job costing (itemized) ✓ |
| Customer-facing unit | Job lump sum or tier | Sq footage (with multiplier) |
| Installation treatment | Structurally independent from size | Separate line item (same conclusion, less explicit framing) |
| Minimum job floor | Explicit | Implied but rarely stated |
| Risk premium for novelty | Explicit | Not commonly framed this way |

**Delta category: rediscovered**

I arrived independently at the same conclusion the corpus holds: job costing is correct internally; sq footage is a communicability heuristic that breaks down at the extremes. The corpus confirms both legs.

Two minor additions that aren't prominent in corpus framing:
1. The **setup cost floor** as a first-class concept (not just a "minimum charge" that feels arbitrary)
2. The **structural decoupling of installation cost from fabrication size** stated as a flaw in sq-footage pricing rather than just treated as a separate add-on

Neither is contradicted by the corpus — they're latent in the data but not framed as rules.

---

## Commentary

For Brand 9 Signs specifically: the actionable implication is that **every job should have an internal itemized cost sheet before a quote is given**, and installation should be estimated as a distinct sub-job (height + substrate + access + electrical). The customer price can still be a single number, but it should derive from the itemized sheet, not from $/sqft applied to fabrication dimensions alone.

Shops that price from sq footage and add installation "at cost" are leaving money on the table on complex installs and overcharging on simple large-format jobs — which erodes their competitive position on vinyl/banner work while undercharging on high-margin illuminated sign work.
