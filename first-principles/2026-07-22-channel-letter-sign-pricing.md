# First-Principles Spike — 2026-07-22

## Question

Does price-per-square-foot (the sign industry's default pricing heuristic)
actually track the real cost drivers of an illuminated channel-letter sign
job? If not, where does it systematically over- or under-charge, and what
would a first-principles cost function look like instead?

## First-principles derivation (no retrieval)

Start by physically decomposing what a channel-letter sign job actually is:
individually fabricated 3D letterforms, each with a metal (usually aluminum)
"return" wall around its perimeter, an acrylic face lit from inside by LED
modules, wired to a power supply/transformer, mounted to a wall or raceway,
and connected to building power — usually by an electrician. Someone also has
to design the layout, get it permitted by the municipality, fabricate it in
a shop, and install it on site, often at height.

Now ask, for each cost component, what physical quantity it actually scales
with:

1. **Design/engineering time.** This is roughly fixed per job. A logo with
   five letters takes about as long to lay out and structurally engineer as
   the same logo scaled 3x larger — the file doesn't get harder to draw
   because the letters are bigger. This cost is independent of area.

2. **Permitting.** Municipal permit fees and the labor to file them are
   almost always a flat fee or a fee banded by a coarse size threshold, not
   a continuous function of square footage. This is also close to fixed
   per job.

3. **Mobilization (site visit, lift/crane rental, travel).** This is driven
   by job count and install difficulty (height, access), not by how many
   square feet of letter face exist. A lift rental costs the same whether
   you're hanging 10 sq ft or 25 sq ft of letters at 20 feet up. This is
   fixed-ish per job, but a step function of install height/complexity.

4. **Trim cap / return material (the metal perimeter wall of each letter).**
   This scales with the *perimeter* of the letterforms, not their area.
   Perimeter and area are not proportional across different shapes: for a
   fixed area, a compact block letter (like a sans-serif "O") has much less
   perimeter than an intricate script letterform or a logo with many thin
   strokes. So two signs of identical square footage can have very
   different amounts of the material that channel-letter fabrication is
   named after.

5. **Acrylic face material, LED module count, and power supply capacity.**
   These are the components that genuinely scale with *face area* — more
   area needs more acrylic, roughly proportional LED coverage for even
   illumination, and power supplies sized to total LED wattage. This is the
   one part of the job where $/sqft is a physically sound proxy.

6. **Labor to bend, weld/rivet, paint, wire, and assemble.** This scales
   with *letter count* and *perimeter/complexity*, not area — a script "&"
   with many curves and thin strokes takes longer to fabricate than a block
   "O" of the same square footage.

Combining these, the real cost function looks like:

```
Cost = Fixed(design + permit + mobilization)
     + Perimeter(letterforms) × unit_trim_and_labor_cost
     + FaceArea × unit_material_cost(acrylic + LED + PSU)
     + InstallDifficulty(height, access)
     + Margin
```

Square-footage pricing collapses this into `Cost ≈ FaceArea × blended_rate`,
which only holds when perimeter-to-area ratio and install difficulty are
roughly constant across the jobs being compared — i.e., when a shop
implicitly prices "typical" signage (moderate letterform complexity,
ground-to-low-height install) and uses the blended rate as a fast quoting
shortcut, silently absorbing complexity/height variance into their margin
cushion.

**Predicted failure modes of pure $/sqft pricing**, derivable before ever
touching an industry price list:
- **Small jobs are overpriced by the model, or the shop underprices them**
  if they apply the same $/sqft blindly, because fixed costs (design,
  permit, mobilization) dominate at small area and don't shrink with size.
  A 2 sq ft job isn't proportionally cheaper to design and permit than a
  20 sq ft job.
- **Large jobs should get cheaper per-sqft** if fixed costs are amortized
  correctly — this is why big-box retrofit programs command volume
  discounts, which is a first-principles-predictable outcome, not a
  negotiating favor.
- **Complex/script letterforms are underpriced** relative to block
  letterforms of equal area, because perimeter (the real driver of trim
  and labor cost) is decoupled from area.
- **High or hard-access installs are underpriced** unless install
  difficulty is priced as its own line item, since $/sqft has no term for
  height or access at all.

**Testable claim:** a shop that quotes flat $/sqft company-wide will
systematically lose money on small, ornate, or high-install jobs, and will
over-earn on large, simple, ground-level jobs — unless its estimators
informally adjust the "per-sqft" number up or down per job, which is
functionally the same as abandoning the pure area model and reintroducing
the fixed+perimeter+install terms by hand.

## Corpus answer

Searched after the derivation above was locked in (no revision). Industry
sources (Flexlume, Front Signs, Sign Knights, Signdealz, OnDisplaySigns,
Lee's Signs, Western Signs AZ, 2025-2026 cost guides) converge on the same
structure I derived, almost term-for-term:

- **Channel letters are priced per letter, banded by height tier** (12–18″:
  ~$75–250/letter; 24–36″: ~$200–600/letter; 48″+: ~$400–1,200+/letter) —
  not by a single blended $/sqft rate. This is a fixed-plus-size-tier model,
  not a continuous area function.
- **Raceways (the mounting structure) are priced per linear foot**
  (~$35–65/linear ft) — a perimeter/length metric, matching my
  perimeter-driven trim/labor term.
- **Design/letterform intricacy carries an explicit surcharge**: complex
  shapes, multi-level faces, and tight tolerances are called out as adding
  20–40% to fabrication cost from extra CNC time, hand finishing, and
  masking — directly confirming the perimeter/complexity term I predicted
  would be underpriced by a pure area model.
- **LEDs, power supplies, and wiring are priced as separate line items**
  (~$40–50/letter for LEDs, ~$50–200 for electrical components) rather than
  folded into a blended sqft rate — matching the area/illumination term.
- **Installation (mounting method, wall penetration, access) is called out
  as a distinct, significant cost driver** — matching the install-difficulty
  term, which a pure $/sqft model has no place for.
- Notably, $/sqft as a headline metric shows up for a *different* sign
  type — monument signs (~$150–400/sqft), where the "sign" really is a
  slab whose cost tracks face area much more directly. That's consistent
  with the derivation: $/sqft is a good proxy exactly when perimeter and
  fixed costs are small relative to face area (a monument slab), and a
  poor proxy exactly when they aren't (individually fabricated
  letterforms).

## Delta category: **rediscovered**

The reasoning independently reconstructed the industry's actual estimating
structure — fixed cost + perimeter/complexity cost + area/illumination cost
+ install cost — without having seen it, including the specific prediction
that ornate/small/high-install jobs break flat $/sqft pricing. The corpus
doesn't just agree with the conclusion; it agrees with the *mechanism*
(per-letter tiers, per-linear-foot raceways, explicit intricacy surcharge,
separate electrical line items). This also sharpens *why* $/sqft persists
as informal shorthand in casual conversation even though nobody in the
industry actually quotes that way for channel letters: it's a
back-of-envelope communication tool for buyers, not the shop's real
estimating model — and it works passably only for sign types (monument
slabs) where face area really is the dominant cost term.

## Commentary

The value of doing the derivation blind wasn't reaching a number — it was
generating a *falsifiable structure* (four independent cost terms, each
with a predicted failure mode) before contamination by industry marketing
copy, which tends to quote a single "$/sqft" headline number for SEO
purposes even when it's not how the underlying business actually prices.
Search-first would likely have anchored on that headline number and missed
the per-letter/per-linear-foot/complexity-surcharge structure entirely,
because that structure is scattered across "6 key factors" listicles rather
than stated as a formula. The durable lesson: for any priced physical good,
decompose cost by *what physical quantity each cost input actually scales
with* (fixed / length / area / volume) before consulting comps — comps
report headline numbers, not the scaling law, and the scaling law is what
transfers to a new job that doesn't match any comp.
