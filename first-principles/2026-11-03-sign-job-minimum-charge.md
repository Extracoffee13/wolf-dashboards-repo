# Why do custom sign jobs need a minimum charge, and how should it be derived?

Date: 2026-11-03

## First-principles answer (derived before any lookup)

Primitives: a sign job consumes (a) material area, (b) machine time, (c) human time, (d) fixed per-job overhead that does not scale with size: quote/intake, file prep and proof, machine setup and calibration, order handling, packing, invoicing/payment processing, shipping label, and the risk of reprint.

1. Cost of a job = c_fixed + c_area * A. Price per sq ft only captures the second term. For a large job c_fixed/A is negligible; as A -> 0 the per-sqft price needed to recover cost goes to infinity.
2. A seller who prices purely per sq ft therefore loses money on small jobs, and worse, adversely selects: customers with many tiny jobs (each carrying a full c_fixed) are the ones the pricing subsidizes.
3. The rational fix is a price floor P_min = c_fixed + c_area*A_min + margin, where A_min is the size at which per-sqft pricing starts covering c_fixed. Below A_min the customer pays the floor; above it, area pricing. Equivalent alternative: a setup fee + per-sqft rate. They are the same cost structure expressed two ways; the floor is simpler to communicate, the setup fee is more honest and avoids a pricing "cliff" feeling.
4. Second-order: the floor should sit near the point where the customer's alternative (a competitor, DIY, a cheaper product) becomes attractive, so it is bounded above by willingness to pay for tiny jobs. If the floor exceeds that, don't serve the segment, or bundle (gang many small items onto one sheet/one setup).
5. Bundling insight: since c_fixed is per job not per item, the lever is to amortize it - gang-run multiple small items per sheet, per-order (not per-line) minimums, quantity breaks. Quantity breaks are the same fixed-cost amortization seen from the unit side.
6. Waste: material is sold in discrete units (sheet/roll width), so effective c_area is A_consumed (incl. waste/nesting), not A_ordered. Pricing on ordered area under-recovers on awkward sizes; rule: price on the bounding sheet/roll footprint for low-yield shapes.

Conclusion: min charge = fixed handling cost + material/time at the threshold size + margin; minimums apply per order; amortize via ganging and quantity breaks; price on consumed, not ordered, area.
Confidence: 0.75

## Corpus answer (web, standard search; mostly Signs101 forum anecdote, not formal studies)
- Minimums exist because small jobs take nearly as much labor as large ones; per-sq-ft pricing misses this.
- Derive it by timing the simplest job end to end (setup, cut, weed, mask, apply, bill) and pricing time plus material. Worked example: ~10 min setup at $60/hr = ~$20, plus material = ~$25 minimum.
- Minimums also screen time-wasters; tradeoff is losing small customers who grow into large ones; shops make exceptions for repeat customers; explain the minimum so it doesn't feel arbitrary.
- Reported minimums range $25-$87.50; one shop uses a $5/sq ft shop fee on top of material.
Sources: https://signs101.com/threads/minimum-charges.60212 , https://www.signs101.com/threads/minimum-charge-on-small-jobs.76355/ , https://signs101.com/threads/whats-your-shop-minimum.86967/page-2 , https://www.signshop.com/graphic/digital-printing/print-shop-pricing-know-your-worth/

## Delta: rediscovered (with small novel edges)
Core result (fixed cost per job not scaling with area -> floor = fixed cost + material + margin) matches the corpus exactly. Not in the corpus excerpts: (1) price on consumed/nested area rather than ordered area, (2) the floor is bounded above by customer willingness to pay, (3) quantity breaks and ganging are the same fixed-cost amortization. Those are plausible but unverified edges, not enough to call novel.

## Commentary
Relevance to Brand 9: matches the per-order (not per-line) cap logic in partner sheet economics. Reasoning reached the known answer without retrieval, but the corpus is anecdotal, so numbers (not structure) must come from timing B9's own jobs. Confidence 0.75.
