# Spike 2026-11-06 — Sign cost scaling vs. area

**Question:** Why does sign cost scale sub-linearly with area for printed substrates, but super-linearly for illuminated and structural signs?

## First-principles answer (derived before any search)

Total cost = fixed + area-driven + perimeter-driven + height/load-driven.

1. **Fixed costs (per job, independent of size):** design/proof, file prep, machine setup, travel, truck roll, crew mobilization, permit/admin. Divided by area these fall as 1/A, so $/ft² drops with size. This dominates small printed signs: a 2x2 and a 4x8 vinyl-on-substrate cost a similar setup, so per-ft² is sub-linear in A.
2. **Material cost ~ A** for flat printed goods (substrate, ink, laminate), but sold in discrete sheets/rolls (4x8, 48"/60" rolls). Waste is a step function, so cost is piecewise-linear and efficient at sheet multiples. Hence the B9 sheet-economics concern: pricing at whole-sheet breakpoints.
3. **Handling cost** is linear until a threshold (one person → two people → lift/crane). Past the threshold it steps up. Another step function.
4. **Illuminated signs** add a cost that scales with *perimeter* (channel letter returns, LED modules per inch of stroke) rather than area, plus electrical (power supplies, runs, circuits) that is mostly fixed + stepped. Letter fabrication is labor ~ number of letters x complexity, almost independent of height until large. So illuminated cost is driven by letter count and stroke length, not ft². A per-ft² price is a poor proxy.
5. **Structural signs (monuments, pylons):** wind load force ~ A. Overturning moment ~ A x height. Foundation volume needed to resist moment grows faster than A (roughly A^1.5 for geometrically similar signs). Steel/concrete cost therefore rises super-linearly, plus engineering and permit thresholds appear (steps) above height/area limits.
6. **Net:** small and flat → fixed costs dominate → $/ft² falls with size. Large, tall, or lit → load, labor-type and electrical terms dominate → $/ft² flat or rising. Real prices are a sum of these regimes, so "price per sq ft" is only valid inside one regime. Outside it, the right quoting unit is per letter, per linear ft of stroke, or a lump sum with line items.

Prediction: per-ft² quotes should be quoted for flat printed goods, per-letter for channel letters, lump-sum for monuments, and the lump sum's implied $/ft² should be much higher than the flat-goods rate and non-monotonic.

## Corpus answer (web search, standard mode)

- Per-ft² is common but only a rough proxy; channel letters and monuments are usually quoted as project totals or per letter, because size is only one input.
- Cost drivers named: letter height/complexity, illumination type, mounting, site access, electrical, permits, engineering, foundation, trenching, masonry vs aluminum, single/double-sided.
- Illumination can double or triple material and labor vs. non-lit.
- Worked example: 6x2 ft backlit channel sign totals ~$3,450 with labor, electrical, permits, delivery, ≈ $290/ft² — far above flat-panel rates ($15–40/ft²).
- Monuments range ~$5k to $65k+; masonry builds cost far more than aluminum.
- Caveat: sources are mostly vendor marketing with inconsistent figures.

Sources: homeadvisor cost guide, blinksigns.com/monument-sign-cost-guide, angi.com commercial sign installation cost, mydiysigns.com letters-lit.

## Delta category: **rediscovered**

Same conclusion on units (per-ft² for flat, per-letter for lit, lump sum for monuments) and the same cost drivers. Two details of my derivation were not found in the corpus: (a) the A^1.5 foundation/moment scaling as the reason structural cost is super-linear, and (b) lit cost tracking stroke perimeter rather than area. These are plausible but unverified; marketing sources don't state scaling exponents.

## Commentary

Useful for B9: don't use a single $/ft² curve across product lines. Quote by regime, and put whole-sheet breakpoints and step thresholds (two-person lift, engineering trigger height) into pricing logic. Confidence in the A^1.5 claim is moderate and should be checked against an engineer before use in any customer-facing claim. Corpus check was one standard search, so thin.
