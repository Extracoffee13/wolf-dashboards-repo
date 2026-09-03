# First-Principles Spike — 2026-09-03

## Question

Why does channel-letter signage price per letter/inch of letter height rather
than per square foot of face area, and is that pricing primitive actually
tracking the real cost driver?

## First-principles answer (derived before any search)

Start from what a channel letter physically is: an individually fabricated
3D letter box, made of an aluminum "return" (the side wall that gives the
letter its depth, typically 3–5"), a back (usually aluminum), a face
(acrylic, often with translucent vinyl overlay), a strip of trim cap sealing
the face-to-return joint, LED modules mounted inside on standoffs, wiring
run from each letter, and a power supply (transformer) feeding a group of
letters. It is mounted individually to a wall or raceway, one letter at a
time.

Two candidate cost invariants compete to explain price: **area** of the
letter's face (the "square footage" analogy borrowed from flat signage) and
**perimeter** of the letter's outline (since the return is a strip of metal
wrapped around that outline).

Decompose the cost function by what actually gets purchased and worked:

1. **Return fabrication** (labor-dominant): a sheet of aluminum coil is cut
   to a strip equal to the letter's perimeter × the return depth, then
   bent/formed to follow every curve and corner of the glyph, welded or
   riveted at the seams, and painted. The material and labor here scale with
   **perimeter**, not area — a strip's length is a perimeter, full stop.
2. **Face and back**: acrylic and aluminum sheet cut to the letter's
   silhouette. This *does* scale with **area**, but acrylic and aluminum
   sheet stock are cheap per square inch relative to the labor of forming
   and welding a return — a commodity material cost, not the cost driver.
3. **Trim cap**: another strip that runs the perimeter, applied by hand.
   Perimeter-scaling, labor-heavy.
4. **LED modules and wiring**: modules are spaced along the interior at
   roughly fixed intervals to avoid shadowing, so count scales closer to
   area (more interior surface to illuminate evenly) — but LEDs are cheap
   per unit, and this is a smaller share of total cost for typical
   storefront sizes.
5. **Install labor**: roughly fixed per letter (mount, wire, connect),
   largely size-independent within a normal range.

For a fixed typeface and fixed return depth, if you uniformly scale a
letter's height by factor *k*, its perimeter scales by *k* (linear) while
its area scales by *k²* (quadratic). Since the dominant costs — return
forming/welding and trim cap application, i.e. labor applied along a
perimeter — scale linearly with height, and the area-scaling costs
(sheet stock, LED count) are a minority of total spend at typical
storefront sizes (roughly 6"–30"), the **aggregate cost curve is
approximately linear in letter height** across that range. A per-inch price
is therefore a reasonable linear regression fit to an underlying
labor-perimeter cost structure — it isn't an arbitrary convention, it's
tracking the right invariant for *this specific fabrication process*,
which is why it differs from flat cabinet signs, awnings, and banners
(sheet-good, area-dominated processes) that correctly price per square foot
instead.

This predicts three things a good pricing primitive should get right, and
where a naive one should fail:

- **Complex glyphs should cost more than simple ones at the same height.**
  An "M" or "&" has far more perimeter than an "I" or "O" at identical
  height, so a strict per-inch price undercharges complex letters and
  overcharges simple ones. Real quotes should show per-letter or
  per-complexity adjustments layered on top of the height rate, or simply
  average the effect across a typical word (most real signs are quoted as
  a whole word/name, which smooths this out).
- **Return depth is a second axis, not absorbed by height.** A 5" return
  uses more aluminum per inch of perimeter than a 3" return, so depth
  should carry its own upcharge, separate from height.
- **The linear-per-inch model should break down at extremes.** At very
  large letter heights (raceway letters several feet tall), area-scaling
  costs (sheet stock, LED count, power supply capacity) grow as *k²* while
  labor grows as *k*, so area costs should eventually catch up to and
  exceed labor costs. A pure per-inch rate would then underprice large
  letters — predicting that real-world quotes either taper into a higher
  effective rate per inch at large sizes, or switch to a different pricing
  model (per-piece custom quote) above some threshold, rather than
  extrapolating the small-letter rate indefinitely.

## Corpus answer (searched after the above was written)

Industry sources (channelletter.com, frontsigns.com, flexlume.com,
signs101.com forum, others) confirm per-vertical-inch pricing is the
standard convention, typically quoted per letter and summed across a name,
in the rough range of $12–$40 per inch depending on vendor, lighting type,
and letter style, with typical storefront jobs (12–24" letters) landing at
$800–$4,000 total. Their stated rationale is a loose bundle: taller letters
need "more aluminum for the returns and backs, more acrylic for the faces,
and more LED modules for even illumination," and per-letter figures "hide"
the variables of height, lighting, mounting, and access that per-inch
pricing is meant to expose. Notably, at least one source states that
doubling letter height "nearly quadruples" material needed — an
area-scaling claim — while the same sources describe the market price as
linear per inch. None of the sources found articulate a perimeter-vs-area
geometric mechanism, name labor-on-perimeter as the dominant cost, or
reconcile the tension between their own quadratic-material claim and the
linear-price convention.

## Delta category: **novel**

## Commentary

The surface conclusion — per-inch pricing is real and industry-standard —
was rediscovered rather than novel by itself. What's novel is the
mechanism: the corpus gestures at "more material at larger sizes" without
distinguishing perimeter-scaling (labor, linear) from area-scaling
(material, quadratic), and consequently states both a quadratic material
claim and a linear pricing convention side by side without noticing the
tension. The first-principles derivation resolves that tension directly:
per-inch pricing works *because* labor applied along the perimeter
dominates total cost at typical sizes, not because material cost is
linear (it isn't). That framing also generates falsifiable predictions
the corpus doesn't state — that pricing should show per-letter complexity
adjustments, a separate depth upcharge, and a rate that steepens or breaks
into custom-quote territory at large letter heights — which would be worth
checking against real vendor rate cards if this question gets revisited
for actual Brand 9 Signs quoting logic.
</content>
