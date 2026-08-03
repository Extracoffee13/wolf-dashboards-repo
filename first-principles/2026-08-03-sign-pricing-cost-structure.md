# First-Principles Spike — 2026-08-03

## Question

From first principles, how should a custom exterior commercial sign (e.g. a channel-letter
set or a monument sign) be priced — and is a single blended $/sq ft rate the right pricing
unit, or does the true cost structure demand something else?

*(Backlog was empty; generated this question myself as directly relevant to Brand 9 Signs
operations.)*

## First-Principles Answer (derived before any search)

Start from what a sign actually is and what it costs to bring into existence, with no
reference to how the industry currently quotes anything.

**Decompose the cost into its physical and organizational primitives:**

1. **Materials** — aluminum returns/faces, acrylic faces, LED modules, wiring/power supplies,
   raceway or backing, paint, vinyl overlay, and for monument signs: masonry/EIFS, structural
   steel, footings, concrete. Material quantity scales with *surface area and volume* of the
   sign, not with the job as a whole.
2. **Design/engineering labor** — CAD layout, structural calculations (especially wind/ice
   load for anything tall or cantilevered), proofs, revisions. This is largely a **fixed cost
   per job**: a 2 sq ft letter set and a 20 sq ft letter set both need one round of design work.
3. **Fabrication labor** — cutting, forming, welding, wiring, painting. This scales with
   *piece count and complexity* more than raw area — a sign with 12 individual channel letters
   has 12 separate fabrication and wiring operations regardless of how large or small the
   letters are.
4. **Permitting** — a near-fixed cost per job (a flat municipal fee plus staff time to prepare
   and submit the application), occasionally with a variable engineering-stamp cost that
   scales with height/wind exposure, not with sign area.
5. **Installation** — mobilization (crew, vehicle, lift/crane rental) is a **fixed cost per
   trip**; the marginal cost of installing a slightly bigger sign in the same trip is small.
   A large sign doesn't need proportionally more trips than a small one.
6. **Overhead + margin** — shop rent, insurance, equipment depreciation, admin, and target
   profit, allocated per job against expected annual volume.

**The key structural insight:** several of the largest cost centers (design, permitting,
mobilization/install) do **not** scale with sign area — they are approximately fixed per job.
Only raw material and some fabrication labor scale with size, and even labor scales more with
*piece/letter count* than with square footage.

This means the true cost function looks like:

```
Cost(job) = Fixed_per_job (design + permit + mobilization + overhead allocation)
          + Variable_per_unit × (area, and/or letter count, and/or complexity)
```

— i.e. a line with a **positive intercept**, not a line through the origin.

**Consequence:** if a shop (or a customer doing back-of-envelope math) tries to price purely
as `$/sq ft × area`, forcing a linear-through-origin model onto a cost structure that actually
has a large fixed component, the result is systematic mispricing:

- **Small signs get underpriced** — the fixed costs (design, permit, one install trip) don't
  shrink just because the sign is small, so a pure-$/sqft quote undercharges relative to true
  cost, and the shop loses money or has to pad tiny jobs disproportionately.
- **Large signs get overpriced relative to marginal cost** — once the fixed costs are already
  covered, additional square footage costs mostly just material + a bit more labor, so a flat
  $/sqft rate captures excess margin on big jobs (which is *fine* for the business, but it
  means the rate is really a blended average, not a real per-unit cost).

**Prediction, before looking anything up:** a rational, mature sign industry should have
converged on one of two adaptations to this reality:
(a) **itemized quoting** — design, permit, fabrication, and install broken out as separate
line items rather than folded into one $/sqft number, and/or
(b) **per-unit pricing for discrete elements** (e.g. per-letter pricing for channel letters,
since each letter carries its own fixed fabrication/wiring cost independent of its size) rather
than pure area-based pricing, and/or
(c) **tiered or size-banded $/sqft rates**, higher for small jobs and lower for large ones, as
a crude approximation of the fixed+variable curve.

If the industry instead uses one flat $/sqft number across all job sizes with no adjustment,
that would be economically anomalous — either most shops don't do enough volume analysis to
notice the mispricing, or (more likely) they informally pad small-job quotes and call it
"minimum charge," which is itself evidence of an implicit fixed cost floor.

## Corpus Answer (found after searching)

Searched sign-industry cost guides (Blink Signs, Channel Letter, OnDisplay Signs, AGC Signs,
Signdealz, Lee's Signs, Flexlume, Western Signs, and ISA-referenced figures). Findings:

- **Channel letters are priced per letter/set** (typically $800–$4,000 for a basic set,
  $3,000–$6,000 for a typical illuminated set), not per square foot of letter face. This is
  exactly the "discrete piece pricing" prediction (b) — each letter's fixed fabrication/wiring
  cost dominates over its individual size.
- **Monument signs are priced by sq ft of sign face**, with the International Sign Association
  cited at roughly $150–$400/sq ft — but every guide immediately qualifies this with a long
  list of separate add-ons: illumination type, materials, site conditions, and **permitting is
  consistently called out as a distinct line item**, not folded into the per-sqft rate. Several
  guides explicitly separate "design," "permit," "fabrication," and "installation" as line
  items in a full estimate — matching prediction (a).
- **A "minimum charge" / shop markup dynamic exists**: guides note that going through a local
  sign shop vs. ordering factory-direct swings price 30–50%, and note a 30–50% shop markup
  layered on manufacturing cost — evidence of the fixed-overhead allocation baked into local
  shop pricing that a factory-direct (higher volume, better fixed-cost amortization) doesn't
  need to charge as heavily.
- No source frames the *reason* for itemization or per-piece pricing in explicit fixed vs.
  variable cost-curve terms — it's presented as "these are the factors that affect price," not
  as "here's why $/sqft alone would misprice small and large jobs."

## Delta Category: **rediscovered**

The first-principles reasoning independently arrived at the actual industry convention:
itemized quotes (design/permit/fab/install broken out) and per-letter (not per-area) pricing
for channel letters — both are standard practice, confirming the reasoning rather than
correcting or extending it.

## Commentary

This is a clean validation case, not a novel-framing case: the corpus doesn't state the
underlying economic argument (fixed-per-job + variable-per-unit cost curve) explicitly, but
the *behavior* the argument predicts (itemization, per-piece pricing, minimum charges) is
exactly what's observed. The value of the first-principles pass here isn't a new fact — it's
a *causal model* underneath a convention that the corpus only describes empirically ("here are
the factors that affect price") rather than explains ("here's why a single $/sqft number would
be wrong"). That causal model is directly usable at Brand 9 Signs: any time a customer
benchmarks a quote against a single $/sqft rule of thumb found online, the fixed-cost argument
is the correct rebuttal, and it also flags where Brand 9's own quoting practice should be
checked — is the shop's minimum charge actually covering fixed design/permit/mobilization cost
on small jobs, or is it an arbitrary number inherited from competitors?

## Sources

- [Commercial Signage Cost Guide 2026](https://blinksigns.com/commercial-signage-cost-guide/)
- [Channel Letter Sign Cost: 2026 Pricing Guide](https://www.channelletter.com/news/channel-letter-sign-cost/)
- [Sign Project Financing — Monument Signs](https://www.signdealz.com/sign-project-financing-monument-signs)
- [The Ultimate Guide to Channel Letter Sign Cost](https://www.ondisplaysigns.com/channel-letter-sign-cost/)
- [How Much Does a Business Sign Cost?](https://www.agcsigns.com/blog/how-much-does-a-business-sign-cost)
- [Channel Letter Signs Cost Consideration](https://www.signdealz.com/blog/channel-letter-signs-cost-consideration)
- [Business Sign Costs in 2026](https://www.leessign.com/blog/business-sign-cost-guide-2026)
- [Business Signs Costs 2025](https://westernsignsaz.com/business-signs-costs-2025/)
- [How Much Does a Channel Letter Sign Cost? (2025)](https://www.flexlume.com/blog/how-much-does-a-channel-letter-sign-cost)
