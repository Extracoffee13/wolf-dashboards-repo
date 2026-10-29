# First-Principles Spike — 2026-10-29

## Question
What is the right unit of price for a custom sign, and why isn't it square foot?

## First-principles answer (derived before any lookup)
1. Price must (a) cover cost, (b) leave margin, (c) stay under the customer's value ceiling. Cost is the floor, value the ceiling; the unit should track whichever drives the quote.
2. Decompose cost by what it scales with:
   - Materials: scale with area, but via *yield* (sheet/roll size, nesting waste), not net area. A 3x5 ft sign cut from a 4x8 sheet consumes more than 15 sq ft.
   - Fabrication labor/machine time: a *fixed setup* (file prep, tool changes, fixturing) plus a variable part driven by complexity (path length, finishing, layers), not area.
   - Design/art: fixed per job, independent of size.
   - Installation: driven by site (height, lift/truck, travel, mounting substrate, permits), nearly independent of sign area.
   - Overhead: per job (quoting, invoicing, project management).
3. So cost ≈ F (fixed per job) + a·Area_yielded + b·Complexity + I (install). Area appears in only one term. At small sizes F dominates, at large sizes I and materials dominate; a pure $/sqft line is wrong at both ends and only right in a mid-band of homogeneous product.
4. Value side: customer pays for visibility/function/permanence (a monument sign anchors a community's identity), not square footage. Value is weakly correlated with area, which makes $/sqft a poor ceiling too.
5. Why $/sqft survives anyway: it's cheap to communicate, comparable across bidders, and within one product class (e.g., flat vinyl-on-aluminum) F, b and I are roughly proportional to area on average. It is a *compression* of the cost model, valid per product class.
6. Conclusion: the right unit is the *job*, built from a cost model (fixed + area-yield + complexity + install) with a minimum charge, then optionally presented as a per-class $/sqft or per-piece rate for the customer. Quote $/sqft only within a class and with explicit minimum, setup and install lines. Internally, track margin per machine-hour and per install-hour, since those are the scarce resources.

## Corpus answer
Web sources (signs101 forum threads, sign-shop bookkeeping guides, HomeAdvisor/Angi cost pages): price is built cost-plus from base/admin charge + art charge + per-sqft charge + material cost × markup + installation; per-sqft is the customer-facing convenience rate; minimum charges protect small jobs; install is a separate line; design/setup can be 20–40% of cost. Benchmarks run ~$10–$200/sqft depending on type. Sources are forums and marketing guides, so quality is mixed.

## Delta category
**rediscovered**: independent derivation matches the orthodox structure (fixed + area + material markup + install + minimums).

## Commentary
Two small additions the corpus underplays: (1) price material on *yielded* area (nesting waste) not net area, which ties directly to the B9 vinyl-nesting work; (2) margin should be tracked per scarce resource (router/plotter hours, install crew hours) because that is what actually caps revenue. Both are worth testing against B9 quote history, not asserting. Confidence moderate: the corpus check was a single standard search of non-authoritative sources.
