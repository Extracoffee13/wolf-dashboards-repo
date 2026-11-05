# Spike 2026-11-05: What are the minimum primitives an agent must compute to price a custom sign?

**Question source:** generated (backlog was missing) - Brand 9 Signs operations.

## First-principles answer (derived before any search)
1. A sign is material + machine time + human time, plus delivery and sometimes install.
2. Material = area x unit cost x waste. Waste comes from whole-sheet buying (4x8 = 32 sq ft) and nesting.
3. Labor splits into fixed setup per job (art, file prep, proofing, machine setup) and variable time per unit. Fixed setup explains quantity breaks and why tiny orders lose money.
4. Install is a separate cost stack (travel, crew, equipment, site risk) and does not scale with sign area.
5. Overhead is recovered by loading it onto billable or machine hours.
6. Margin is a share of price, not a markup on cost: P = C / (1 - m). A 50% markup is only a 33% margin.
7. Setup dominance implies a minimum-order floor: price = max(computed, floor).
8. Above cost-plus sits value to the buyer; cost is the lower bound, buyer alternatives the upper bound.
9. Primitives: area, material $/sq ft, waste factor, setup hrs, unit labor hrs, install stack, overhead rate, target margin, floor.

## Corpus answer
Sign-industry guides (Signs101, SignShop, Graphics-Pro, bookkeeping guides) converge on: (materials + labor + labor burden + overhead) with markup/margin applied; per-sq-ft pricing adjusted for complexity and job size (small jobs cost more per sq ft); a shop minimum; and explicit warnings that 50% markup = 33% margin. Sanity-check tip: price a comparable wholesale banner, double it, divide by area.

Sources: signshop.com "Understanding Sign Pricing"; graphics-pro.com "Pricing signs and graphics profitably"; signs101.com pricing threads; beancount.io sign shop job-costing guides.

## Delta: rediscovered
All nine primitives except one match the corpus. Differences: the corpus names "labor burden" (taxes, benefits) separately, which I folded into overhead; and the corpus is vaguer on value ceiling and on the sheet-waste factor, which I emphasized (relevant to B9's whole-sheet vs custom-piece ordering).

## Commentary
Validates reasoning. The most reusable output is the margin identity P = C/(1-m), which an agent should always use instead of "x1.5". Web sources are shop-owner blogs and forums, so numeric rates are anecdotal; B9's own job-costing data should be the benchmark. Confidence moderate: no B9-specific numbers were tested.
