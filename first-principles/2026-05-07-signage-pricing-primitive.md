# First-Principles Spike — 2026-05-07

## Question

What is the correct pricing primitive for a signage fabrication business — cost-plus, market-rate, or throughput-based — and which survives first-principles reasoning?

---

## First-Principles Answer

**Derived without retrieval.**

### Primitive 1: What does a sign buyer actually purchase?

A sign converts a physical location into a communication event. The buyer is not purchasing materials and labor — they are purchasing a communication outcome (attention, legibility, brand presence) at a specific place. The substrate, vinyl, and LEDs are merely the delivery medium.

### Primitive 2: What are the fabricator's real inputs?

| Input | Cost behavior |
|-------|--------------|
| Materials | Variable, per-job |
| Labor | Variable in quantity, but capacity-constrained (fixed weekly hours) |
| Equipment | Depreciating assets — fixed cost, variable utilization |
| Overhead | Fixed per period |

### Primitive 3: What does cost-plus pricing actually optimize?

Price = (material + labor + overhead allocation) × (1 + margin%). This ensures every job *covers* its allocated share of costs. But it embeds a hidden assumption: that all jobs consume overhead proportionally to direct costs. A $500-substrate job that ties up the CNC router for 6 hours is treated identically to a $500-substrate job that uses 45 minutes of router time — if direct costs happen to match. This is wrong.

### Primitive 4: What is the actual constraint in a sign shop?

Every shop has a bottleneck — typically skilled labor (installers, CNC operators, designers) or a specific machine (wide-format printer, router). That capacity is fixed per week. Unused constraint hours are permanently lost; they cannot be inventoried. Therefore, the value of a constraint hour is not its cost but its **opportunity cost**.

### Primitive 5: What does competitive pressure do to value-based pricing?

A retail tenant sign might drive $800k/year in revenue for a business. The sign costs $8k to make. Value-to-cost ratio: 100:1. On pure value terms, $8k is dramatically underpriced. But signage is a competitive commodity — buyers can solicit multiple bids, fabricators are regionally substitutable, specs are comparable. Competition compresses price toward cost, limiting how much value can be captured.

### Synthesis

- **Price floor**: total job cost (cannot sustain below-cost pricing)
- **Price ceiling**: market rate (competition prevents sustained premium without differentiation)
- **Optimization target**: gross profit per bottleneck hour consumed

If the router runs 40 hours/week at capacity:
- Job A: $400 GP in 2 router hours → $200 GP/hr
- Job B: $800 GP in 6 router hours → $133 GP/hr

Job A is the better business decision despite lower absolute margin. A shop that selects and prices jobs on cost-plus percentage will systematically overprice fast simple work and underprice complex machine-intensive work — misallocating the one resource it cannot expand in the short run.

**First-principles conclusion**: The correct pricing primitive is **throughput per constrained resource unit**. Cost-plus sets the floor; market rate sets the ceiling; throughput accounting tells you which jobs to prioritize and where you have pricing power within that band.

---

## Corpus Answer

Standard signage industry practice (Signs Builder Illustrated, shopVOX, Signs 101 forum, Signworld):

- **Materials markup**: 50–100% (vinyl ~10x cost; ACM/aluminum ~3–4x)
- **Labor markup**: ~1.3x fully-loaded labor cost
- **Shop rate**: $50–60/hour is the published norm
- **Method**: Job costing — track material, labor, and overhead per job; apply category-specific markups
- No mention of throughput accounting, constraint optimization, or GP-per-machine-hour anywhere in the signage corpus

---

## Delta Category

**`novel`**

The corpus correctly describes *how* to build a price. It never asks *what the shop should be maximizing*. Throughput accounting (Goldratt, *The Goal*, 1984) is well-established in manufacturing literature but absent from the signage-specific corpus. Applying the constraint lens to sign-shop capacity allocation is framing the signage industry hasn't adopted — and it produces materially different job-selection decisions than optimizing markup percentage.

---

## Commentary

The cost-plus model is operationally useful (simple, auditable, defensible to clients) and sets a correct floor. Its failure mode is invisible: a shop running at capacity with cost-plus pricing is leaving money on the table by accepting low-GP/hr jobs that crowd out high-GP/hr ones. The fix is not to abandon cost-plus but to layer a throughput filter on top: use cost-plus to set minimums, market rate to set maximums, and GP/constraint-hour to rank competing jobs when capacity is tight.

For Brand 9 Signs specifically: identify the bottleneck (likely skilled installation labor or the wide-format printer), calculate GP/hour for each job category, and use that to prioritize quoting effort and apply selective price premiums on constraint-intensive jobs.
