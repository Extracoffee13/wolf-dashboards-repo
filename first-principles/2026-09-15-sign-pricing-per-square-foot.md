# First-Principles Spike — 2026-09-15

## Question

Does the signage industry's standard "price per square foot" convention actually
track the true cost drivers of a custom commercial sign, or is it a heuristic that
systematically misprices certain jobs?

(Self-generated — backlog was empty. Chosen for direct relevance to Brand 9 Signs
quoting/estimation practice.)

## First-principles answer (derived before any search)

Start from the physical and transactional primitives of what it actually takes to
put a sign on a building, with no reference to how the industry talks about pricing.

**Decompose the cost function.** A sign job consumes five categories of input:

1. *Materials* — aluminum, acrylic, LED modules, vinyl, paint, structural steel for
   monument bases. This is the one input that scales roughly linearly with surface
   area (and, for dimensional/3D work, with volume).
2. *Design & engineering* — layout, code research, structural stamps where required.
   This is close to a fixed cost per job: a 2 sq ft ADA sign and a 200 sq ft pylon
   sign both need one round of design and one engineer's signature, not 100x more.
3. *Fabrication labor* — cutting, welding, routing, wiring, assembly. This scales
   with part count and joint complexity, not area — a single flat panel of 100 sq ft
   is fabricated faster than ten small dimensional letters totaling 10 sq ft.
4. *Installation labor and equipment* — this is the one most decoupled from area.
   A sign mounted at 6 feet needs a ladder; the same sign at 40 feet over a highway
   needs a crane or bucket truck, traffic control, and possibly night work. Height
   and site access, not square footage, are what move this number, and they move it
   in step functions (crossing an equipment-class threshold), not smoothly.
5. *Permitting and compliance* — a flat per-jurisdiction transaction cost (filing,
   plan review) that occasionally jumps discontinuously if a zoning variance is
   triggered. This has essentially zero correlation with sign area.

**Build the true cost model.** Summing these:

`Cost ≈ fixed_admin + design(complexity) + materials(area) + fabrication(part_count) + install(height, access) + permit(jurisdiction, variance?)`

Area appears as exactly one additive term among several, and for most sign types it
is not the dominant one. Only for large, flat, low-mounted, unlit signage (banners,
flat wall panels at grade) does the materials term dominate and does "price per
square foot" approximate the true cost curve well.

**Predict the failure modes of a pure per-sq-ft model.** Because several of the real
cost terms are fixed or step-function rather than area-proportional:

- *Small, complex, high-mounted, illuminated signs get underpriced* — the fixed
  costs (design, permit, crane mobilization, electrical hookup) don't shrink with
  area, so a flat rate-per-sqft quote undercharges relative to true cost. This is
  the job type most likely to blow a fixed-bid budget.
- *Large, simple, low, unlit signs get overpriced* relative to true marginal cost —
  charging the same blended rate captures margin the customer may notice if they
  comparison-shop against a large-format-only vendor.
- The real profit *and* real risk both live in the terms per-sq-ft pricing hides:
  installation access and permitting/variance exposure — exactly the two variables
  a shop most needs to price explicitly, not average away.

**Why would an entire industry use a heuristic it knows is imprecise?** Because
per-sq-ft pricing isn't primarily a costing tool — it's a negotiation and
comparison-shopping convention. Square footage is the one input a non-expert buyer
can verify independently, without trusting the seller's internal labor/equipment
model. This is the same tradeoff seen in real-estate price-per-square-foot and
cloud storage price-per-GB: the industry prices on the *most legible* variable, not
the *most causal* one, because legibility is what lets buyers compare bids at all.
The prediction this generates: sophisticated shops should quietly run a hybrid model
(base trip/mobilization charge + per-sqft material rate + itemized adders for
electrical, height/equipment class, and permit complexity) while still quoting
customers a single blended "$/sq ft" headline number for comparability.

## Corpus answer

Web search on commercial sign pricing guides (Angi, MegaSign, NeonSignsNow, Lee's
Signs, and others, 2026) confirms the predicted structure almost exactly:

- "Sign type is often the single best predictor of installation costs because each
  category carries its own labor, equipment, and permitting requirements that go
  far beyond square footage."
- "Foundation and permitting costs are fixed expenses that disproportionately
  impact the price per square foot for smaller signs" — i.e. the industry's own
  literature names the exact distortion predicted above (fixed costs inflate the
  effective per-sqft rate on small jobs).
- Installed cost is explicitly modeled as sign type + height/access (crane/bucket
  truck) + permits ($200–$1,000) + structural engineering review ($500–$2,000) +
  materials — a itemized/hybrid model, not a pure area multiplier.
- Per-sq-ft figures are presented as a *range-finding baseline* ("$10–$300 per sq
  ft") for buyer comparison, with the guides explicitly caveating that installation,
  permitting, and site prep are added on top.

## Delta category: **rediscovered**

The first-principles derivation independently reconstructed the industry's own
stated model: per-sq-ft is a legibility/negotiation heuristic layered on top of a
true cost function dominated by fixed and step-function terms (design, permits,
install access), which distort the effective rate most for small/complex/high jobs.
The corpus doesn't just have the same conclusion — it uses nearly the same causal
language ("fixed expenses that disproportionately impact... smaller signs").

## Commentary

No corpus error and nothing genuinely novel here — this is a case where reasoning
from primitives (materials/labor/equipment/permitting as separable cost terms with
different scaling behavior) lands on ground the industry has already mapped and
written down in consumer-facing buying guides. The value of doing it "blind" first
is calibration, not discovery: it confirms that decomposing a pricing convention
into its underlying cost terms before checking the answer is a reliable method,
which is useful to know before applying the same move to a question where the
corpus answer is less settled (e.g. Hartley Capital deal-structuring conventions,
where "market standard" terms may be legibility heuristics rather than
risk-optimal ones, same as $/sq ft here).
