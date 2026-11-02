# First-Principles Spike — 2026-11-02

## Question
What is the right unit of price for a custom sign: area, material yield, or time?

## First-principles answer (derived before any lookup)
Primitives: a sign job consumes (1) material that is bought in fixed quanta (4x8 sheet, vinyl roll width), (2) machine time (printer, router, plotter), (3) human time (design, prep, finishing, install), (4) overhead and risk (remakes, shipping damage), and must clear a margin and a customer's willingness to pay.

Chain:
1. Cost is not linear in area. Material is purchased in quanta, and a job pays for what it *consumes*, which is the sheet footprint it blocks, not the area it uses. Consumed area = used area + waste. Waste depends on nesting: a 30x40 piece on a 48x96 sheet leaves an awkward remainder. So the true material cost driver is yield: area / (area consumed incl. unusable offcuts). Price by area alone under-charges awkward shapes and over-charges ones that nest well.
2. Machine time scales with different things per process: print time ~ area; router/plotter cut time ~ perimeter and detail (path length), not area; so a word-art die-cut is perimeter-driven, a flat panel is area-driven.
3. Human time is largely fixed per job (setup, file prep, proofing, packing), independent of size. Small jobs are dominated by this fixed cost; hence a minimum order price is not a convention but a necessity: below some area, price = fixed cost + margin.
4. So cost per job ≈ F (fixed) + a·area_consumed + b·path_length + c·handling(size, weight, freight) . Price must be >= cost x (1+margin); but the customer's perceived value is anchored on area (they can compare square footage) so market price converges on a per-sq-ft rate with a minimum and quantity breaks.
5. Quantity breaks arise because F amortizes and nesting yield improves with more pieces per sheet.
6. Therefore the right *internal* unit is consumed-sheet-fraction plus fixed charge plus cut-path; the right *external* unit is price per sq ft with a minimum and break tiers, because it is legible and anchors comparison. Time is the weakest unit for production items (it punishes efficiency) but the right one for install and custom design labor.
Prediction: the industry quotes per sq ft with tiers and minimums, and sophisticated shops cost internally on material yield + machine time.

## Corpus answer (web, standard search)
- Customer-facing: price per sq ft (or per letter / per sign), with a shop minimum and a declining rate as size grows.
- Internal: material cost x multiplier (2x to 4x) plus labor at a shop hourly rate; labor-times-4-or-5 shortcuts; formula like MAX(minimum, job time x hourly rate).
- Installation priced separately with its own minimum and hourly rate.
- Caveat: sources are forum threads (signs101) and trade primers; several "2026 price guide" pages look like SEO filler and were ignored.

## Delta category: rediscovered
Per-sq-ft external pricing, shop minimum, size/quantity breaks and separate install labor all matched. Two parts of my chain are not in the corpus answers I found: costing on consumed sheet fraction (nesting yield) rather than used area, and treating cut time as perimeter-driven rather than area-driven. The corpus treats material as a flat multiplier, which hides waste. That is a possible extension, not a corpus error: the multiplier is a rule of thumb that implicitly averages yield.

## Commentary
Relevant to Brand 9: the partner-sheet-economics work (whole sheets vs custom pieces) is the yield argument in practice. A quote engine that uses the multiplier on used area will mis-price awkward shapes and die-cut word art. Worth testing: compare quoted price against consumed-sheet cost on the last N jobs. Confidence is moderate: my derivation was shaped by existing knowledge of this business, so it is not a clean-room test.
