# First-Principles Spike — 2026-11-12

**Question:** Should a small sign shop (Brand 9 Signs scale) price by the square foot or by the piece?

**Source:** self-generated. `first-principles-backlog.md` was missing, so it was created and seeded.

---

## 1. First-principles answer (written before any search)

**The basic parts.** A price has to do two jobs: cover the cost of the work, and land under what the buyer is willing to pay. So I start from how cost behaves, then from how value behaves, and only then ask which unit (square foot or piece) fits both.

**Cost structure of one sign.** Break a single sign job into the steps it physically goes through:

1. *Intake and file work:* reading the request, building or fixing artwork, proofing, revisions. This takes roughly the same time for a 12x18 as for a 4x8. It scales with the **job**, not the area.
2. *Machine setup:* loading media, calibrating, nesting, starting the print or cut. Fixed per run.
3. *Material:* substrate, ink, laminate. This looks proportional to area, but it isn't quite. Substrate comes in sheets (4x8 coroplast, ACM, PVC), so the real cost is the **number of sheets consumed**, and that is a step function of how well the pieces nest. A 2x3 that leaves an awkward scrap costs more per square foot than six 2x4s cut from one sheet.
4. *Print/cut time:* roughly proportional to area. This is the only cost that is truly linear.
5. *Finishing and handling:* grommets, stakes, bagging, labeling. Per piece.
6. *Shipping or install:* per package or per site visit. Close to fixed for anything under oversize-freight limits.
7. *Admin:* invoice, payment, follow-up. Per order.

So the cost of a job is roughly:

  **C = F_order + n·F_piece + Σ sheets(nesting) · P_sheet + v·A_total**

where F is fixed cost, n is the piece count, A is area and v is the variable rate per square foot. For small signs, the F terms are most of the cost. For big signs, the area terms are.

**What that means for pure per-square-foot pricing.** If price = r·A, then margin = r·A − C. With C carrying a large fixed part, margin goes negative below some break-even area A* = F / (r − v). Pure per-square-foot pricing loses money on every sign below A* and makes extra profit on every sign above it. Because a typical shop's volume is mostly small signs (yard, A-frame inserts, door decals, deck signs), this isn't an edge case. It is the main way the shop leaks money.

**What that means for pure per-piece pricing.** A flat price per piece flips the error: the shop overcharges on small signs (and loses those buyers to cheaper shops) and undercharges on large ones. It only works when the pieces are a fixed set of sizes, which makes it per-piece pricing inside a size tier.

**The value side.** Buyers don't value signs by the square foot. A builder buying a model-home deck set is buying "this community looks open for business by Saturday," and a homeowner buying a yard sign is buying an event. What they compare is the price per *finished thing*, against the competitor's quote for the same thing. That favors quoting by piece. Square-foot quoting makes the buyer do math and turns the sign into a commodity.

**Putting it together.**

- *Internal model:* cost-based, with an explicit fixed charge per order and per piece, a sheet-yield material term, and a linear print term. Never a single blended rate.
- *Customer-facing price:* per piece, in a few standard size tiers (the sizes that nest well on a 4x8: 12x18, 18x24, 24x36, 2x4, 4x4, 4x8), with quantity breaks that pass along the fixed-cost spread and the nesting gains.
- *Square-foot pricing* is only honest for large-format custom work (banners, wall wraps, oversize panels), where the area term dominates. Even there it needs a minimum charge as a floor.
- *Tier boundaries* should follow **sheet-yield breakpoints**, not round numbers. Price a size that wastes half a sheet as if it uses the whole sheet, and steer buyers to the sizes that nest well.

**Prediction:** the industry consensus will be "per-square-foot plus a minimum or setup charge." The sheet-yield point is the part I expect the corpus to under-weight.

---

## 2. Corpus answer (searched afterwards)

- Forum and trade-press consensus (signs101 threads on minimum charges and small-job pricing; Sign Warehouse's basic pricing guide; Signs of the Times "Crunch Numb3rs" and "A Sign Pricing Primer"): per-square-foot rates cover material, and a **minimum charge or setup fee** covers the fixed labor on every job. Shops set the minimum by timing the simplest job end to end (open file, cut, weed, mask, apply, bill) and multiplying by the shop rate. Typical minimums cited were $25–$90.
- Shops admit that per-square-foot pricing "blows" on small items. Fixes they describe: a large setup charge, a square-foot rate that rises as size shrinks, or per-piece pricing for small multi-item orders.
- Printing-industry guidance (PRINTING United / printing.org) names two conventions, area pricing and cost-based pricing, and says the industry is moving to cost-based pricing as automated costing tools spread. The example formula given was "$30 + $10/sq ft."
- Bookkeeping guidance stresses job costing (comparing the estimate to the actual cost on each job) to catch leaks that a blended rate hides.
- The usual matrix: **price = max(minimum, base fee + sq ft × rate + material/art fees)**.

## 3. Delta

**Category: rediscovered**

The main structure (fixed per-job cost plus a linear area term, the per-square-foot failure on small signs, and the minimum-charge fix) matches the corpus almost exactly, including the "time the simplest job" way of setting the floor. The first-principles answer goes further than the corpus in two places:

1. **Sheet-yield as a step function.** The corpus treats material as linear per square foot. Deriving it from the physical sheet shows that cost jumps at nesting breakpoints, and that size tiers should be drawn at those breakpoints. This is already practiced inside B9 (see the partner-sheet economics rule: whole 4x8 sheets vs custom pieces), but the general pricing literature doesn't state it.
2. **Splitting the cost model from the quote format.** The corpus mixes up the question of how to cost a job with the question of what unit to quote in. First principles separates them: cost it with a fixed term plus area, but quote by piece in size tiers, because buyers value finished objects, not area.

Neither point is a corpus-error. Both are refinements, not contradictions, so the honest label is *rediscovered*, with a minor novel point on sheet-yield tiering.

## 4. Commentary

- The derivation reached the orthodox answer faster than the forums do. They get there through years of losing money on small jobs. That supports breaking cost into physical steps as a reasoning tool.
- Retrieval added the concrete numbers (the $25–$90 minimum range, the $30 + $10/sq ft shape). Reasoning could not produce those, and they are what you need to actually set a price.
- **Action for B9:** check that shop size tiers sit on 4x8 nesting breakpoints and that no listed size wastes more than ~15% of a sheet without carrying that waste in its price.
