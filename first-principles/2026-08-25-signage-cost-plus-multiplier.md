# First-Principles Spike — 2026-08-25

## Question

From first principles, how should a custom exterior sign (e.g. a set of
illuminated channel letters) be priced — and specifically, why would the
markup multiplier a shop applies over raw cost differ from one sign type to
another (vinyl banner vs. aluminum cabinet vs. dimensional letters)?

Chosen because it sits directly under Brand 9 Signs' operating economics and
is a clean, decidable question: reasoning from primitives should produce a
falsifiable prediction (a shape for how multipliers should vary), not just a
vague "it depends."

## First-Principles Answer (no retrieval)

**What is being sold.** A sign is a bundle of four things: a physical
artifact (materials formed into a shape), a fabrication service (labor +
machine time to turn material into that shape), a delivery service
(design/engineering, permitting, installation), and a warranty (the
fabricator remains on the hook if LEDs, transformers, or adhesion fail within
some window). The buyer isn't purchasing aluminum and acrylic; they're
purchasing durable visibility — foot traffic, brand legibility, lease
compliance — amortized over the sign's working life (years).

**Price floor and ceiling.** In a competitive market with repeat entrants
(several shops can bid the same job), price gets pulled toward a floor set by
true cost (materials + labor + machine time + overhead allocation) plus a
"normal profit" needed to keep the shop as a going concern — below that,
shops exit. Price has a ceiling set by the buyer's value capture: what the
sign is worth to them relative to alternatives (a banner, no sign, a
competitor's fabricator). Actual price sits somewhere between, pulled toward
the floor as competition increases and toward the ceiling as differentiation
(speed, design quality, single-point permitting, reputation) increases.

**Why cost-plus, and why a multiplier specifically.** Each job is bespoke —
no two channel-letter sets are identical in size, letter count, wall
material, or site conditions. Computing true marginal cost precisely before
quoting is itself costly (a site visit, an engineering pass, a materials
takeoff) — call this the "bid-preparation cost." A shop that must win many
bids to keep throughput cannot afford to fully cost every one before quoting.
So the efficient move is a heuristic: measure something cheap and observable
at bid time (letter count, square footage of face, linear footage of
cabinet) and multiply by a rate calibrated from historical job outcomes. This
sacrifices precision (a sparse word like "I O" gets over-priced by a
bounding-box metric, a dense word like "EXCHANGE" gets under-priced) in
exchange for near-zero bid-prep cost and fast, comparable-across-competitors
quoting. This is the same logic as any regression-proxy metric replacing an
expensive-to-measure true variable.

**Why the *multiplier itself* should vary by sign type — the falsifiable
prediction.** Total price = cost × multiplier must still land near true
cost + overhead + margin. If material cost is a *small* share of true total
cost (e.g., vinyl: the roll of material is nearly free relative to design
time, weeding, laminating, application skill, and travel), then a multiplier
applied only to the cheap material line item must be *large* to still cover
the largely-fixed real costs sitting elsewhere. Conversely, if material cost
is a *large* share of true total cost (e.g., welded aluminum returns,
extruded channel — heavy, priced-by-weight stock), the multiplier needed to
reach the same total is *smaller*, because the material line item is already
doing more of the work of representing true cost. So: **multiplier should be
inversely related to material's share of total job cost**, not a single
industry-wide constant. This is a mechanism claim, not just an observation —
it predicts the *ordering* of multipliers across sign categories before ever
seeing a price list: cheap-material/labor-heavy categories (vinyl, paint,
design-heavy pieces) should carry the highest multipliers; expensive-raw-
material categories (welded metal, large-format aluminum composite, pylon
steel structures) should carry the lowest.

**Risk and permitting as a second-order adjustment.** Custom exterior signs
also carry job-specific risk the multiplier must absorb: permitting timeline
uncertainty (a municipal delay ties up shop capacity and financing), unknown
site conditions until install day (wall substrate, electrical run length),
and code-driven rework (wind load, ADA, HOA rejection). These are harder to
fold into a clean per-unit rate and should show up as either a wider
multiplier band for architecturally complex jobs, or a separate line-item
contingency — a second, independent lever alongside the material-share
mechanism above.

## Corpus Answer

Industry sources (channelletter.com, signworld.org, shopVOX, Signs101 forum,
Sign Builder Illustrated, Beancount job-costing guide) converge on:

- Cost-plus pricing with a markup multiplier is the standard method; typical
  job costing = material cost (+ waste) + labor time + machine/CNC time +
  overhead allocation + profit margin.
- The multiplier is explicitly **not** a flat industry constant — it varies
  by category, and the stated *reason* matches the mechanism above almost
  exactly: **"vinyl commonly carries a markup around 10x cost because the
  material itself is cheap relative to the design, printing, and application
  labor wrapped around it, while aluminum or ACM often runs closer to 3–4x
  cost because the raw material cost is a bigger share of the job."**
  LED/dimensional letters sit at 2.5–3.5x, pylon signs (steel-heavy,
  large-format) at 1.8–2.5x — a monotonic ordering from
  cheap-material/labor-heavy to expensive-material/labor-light, exactly the
  ordering the material-cost-share mechanism predicts.
- Per-letter and per-square-foot quoting are real, common heuristics, but
  there is no single clean industry-wide $/sq ft number for channel letters
  — actual price is dominated by letter height, illumination type
  (front-lit vs. halo-lit), mounting (raceway vs. flush), and geography, i.e.
  exactly the kind of job-specific complexity the bounding-box heuristic is
  known to smear over.
- Shop labor rates cluster around $50–60/hr; a real typical installed job
  (10 front-lit letters, 20", painted raceway) runs $4,500–$6,500.

## Delta

**Category: rediscovered.**

The overall shape (cost-plus with a heuristic per-unit proxy to avoid
per-job bid-prep cost) is unsurprising and would be "noise" on its own. What
elevates this to rediscovered rather than noise is the specific,
falsifiable mechanism claim — multiplier size should be inversely related to
material's share of true cost — derived before looking, which the corpus
then confirms almost verbatim, including matching the *ordering* across
vinyl > dimensional letters/LED > aluminum/ACM > pylon. Independently
deriving not just the answer but the specific causal reason the corpus gives
for it is a stronger validation than matching a headline number.

## Commentary

The risk/permitting layer was correctly flagged as a second, harder-to-
formalize lever, but the reasoning didn't produce a concrete number the way
the multiplier mechanism did — the corpus sources don't quantify it cleanly
either (it shows up qualitatively as "complexity" in cost guides), so that
part stays an open question rather than a resolved one. Worth a follow-up
spike: does B9's own historical job data show the same material-cost-share
ordering, and could contingency-for-permitting-risk be estimated the same
way (as a function of jurisdiction variance) rather than folded into a flat
multiplier?
