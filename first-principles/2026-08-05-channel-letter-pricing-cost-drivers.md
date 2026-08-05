# First-Principles Spike — 2026-08-05

## Question

The backlog file was empty, so I generated a question from current Construct work (Brand 9 Signs is a signage operator/fabricator): **Is per-square-foot pricing for illuminated channel letter signage actually cost-reflective — or is it a value-based heuristic riding on a correlation that breaks down at the edges?**

## Step 2 — First-principles derivation (no retrieval)

Start from what a channel letter sign physically *is*: a set of N individually fabricated 3D letterforms. Each letter has a return (usually bent aluminum coil forming the sides), a face (routed/cut acrylic), internal illumination (LED modules wired in series/parallel), a shared power supply/transformer, mounting studs or a raceway, and a final electrical whip to building power. Decompose cost into its true drivers rather than the customer-facing unit:

**Materials.** Aluminum coil is consumed per linear foot of return actually bent — a function of total *perimeter* across all letters, not their footprint area. Acrylic face material does scale with area (plus a sheet-nesting waste factor), so area is a real driver here, but only for the face, which is a minority of material cost. LED module count scales with the letter's interior area for even illumination *and* with stroke length for thin strokes — so even lighting cost is partly a perimeter function, not a pure area function.

**Labor.** This is where the square-foot heuristic should break hardest. Fabricating a return is a per-letter, per-corner operation: cut, form each bend, weld or glue seams, mount studs, run and test wiring. A 10-sq-ft block letter like "O" is one continuous bend. Ten square feet of thin, high-count serif letters spread across a wordmark has the same ink area but many more individual pieces, corners, and wire joints. Labor therefore tracks (letter count × perimeter complexity), not area.

**Engineering/design and permitting.** Roughly fixed per job — one vector file, one engineering stamp, one municipal permit application — largely independent of size, until a size threshold trips a zoning variance (a step function, not a continuous one).

**Installation.** Driven by mounting height and access class (ladder vs. bucket truck vs. crane) and by the number of individual letters that must each be leveled, fastened, and electrically hooked up on the wall — again a function of access and letter count, not total area.

**Risk/warranty.** Failure points scale with the number of LED modules and wiring connections (perimeter/count-driven), and UL listing is per-unit, not per-area.

**Synthesis.** True cost ≈ f(letter_count, total_perimeter, mounting_height/access_class, jurisdiction_fixed_fee, LED_module_count). Square footage correlates only weakly in the middle of the distribution (typical jobs of moderate, uniform letter complexity) and badly at the extremes — a single giant block letter vs. many small intricate letters at equal footprint are wildly different costs to fabricate, yet identical "sq ft."

**Why would the heuristic persist anyway?** Pricing doesn't need to track cost 1:1 to be rational — it needs to track willingness-to-pay while holding margin positive across the *portfolio* of jobs sold. Square footage is the easiest number for a customer to picture and compare across bids, and it loosely proxies the value being bought (visibility/read-distance/curb presence). So $/sq ft is a value-based heuristic wearing a cost-based costume. It only stays solvent if the shop also applies a complexity/style multiplier to true up the outliers. A shop that quotes naive, unadjusted $/sq ft is exposed to adverse selection: competitors underbid them on simple block-letter jobs (real cost is lower there) while they become the only bidder willing to take thin-lettered, high-count jobs — at a loss, while looking "competitive" on paper.

**Falsifiable prediction before searching:** real sign shops should price channel letters per-letter, per-vertical-inch, or via an explicit letter-count/complexity formula — reserving true $/sq ft for cabinet or panel signs, where face material genuinely does scale with area and there is no "letter count" primitive at all.

## Step 3 — Corpus check

Searched current sign-industry pricing guides and shop calculators (channelletter.com, blinksigns.com, frontsigns.com, signcrunch.app, and others, 2025–2026). Findings:

- Channel letters are priced **per letter** ($250–$500/letter ballpark) or **per vertical inch of letter height** (~$12/inch), not per square foot of sign face.
- One shop-published formula: `(Letters × Height) × Style Rate = Base Fabrication Cost` — height and letter count are the base units, and "Style Rate" is exactly the complexity multiplier predicted above.
- Font/style complexity is explicitly called out as a cost driver: standard block fonts are optimized for automated benders; tight serif or script fonts require hand-notching and add 15–25% to fabrication time — i.e., labor tracks perimeter/shape complexity, not area, exactly as derived.
- LED module density and raceway (linear-foot-priced) are called out as separate line items, consistent with the perimeter/count decomposition above.
- Multiple sources explicitly warn that a flat "price per letter" shortcut is itself unreliable/oversimplified — the real formula nests letter count, height, and style rate, which is a slightly finer-grained version of the same conclusion (cost is multi-dimensional, area is not the dimension).

## Step 4 — Delta

**Category: rediscovered.**

The first-principles chain independently arrived at the industry's actual practice: channel letters are billed on letter count / height / perimeter-driven complexity, not square footage, and square-foot pricing is reserved for area-scaling products (cabinets, panels) where it's genuinely cost-reflective. The corpus even supplied the same structural insight in almost the same words ("Style Rate" ≈ the predicted complexity multiplier; hand-notching for serif/script ≈ the predicted perimeter/labor link).

One piece of my reasoning wasn't directly confirmed or denied by the search (permitting as a near-fixed, jurisdiction-driven cost independent of size) — it's a plausible unverified residual, not a corpus contradiction.

## Commentary

The interesting part isn't the pricing fact itself — it's *why* the reasoning converged: decomposing "channel letter sign" into its fabrication primitives (return, face, illumination, mounting) before asking "what does each primitive scale with" forces the perimeter-vs-area distinction to surface on its own, without needing to have seen a sign shop's price sheet. That's a case where enumerating physical primitives and asking "what scales with what" substitutes cleanly for looking up the answer — the reasoning path *is* the answer path here, because the cost structure is determined by manufacturing geometry, not by market convention that could have gone either way.
