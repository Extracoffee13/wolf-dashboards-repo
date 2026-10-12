# First-Principles Spike — 2026-10-12

## Question
What is the minimal correct pricing primitive for a custom sign job?

## First-principles answer (derived before any lookup)

**Primitives.** A custom sign job consumes: (1) materials (substrate, vinyl, LEDs, paint, hardware), (2) machine time (router/CNC, printer, cutter, paint booth), (3) human labor (design, prepress, fabrication, finishing), (4) install (crew, truck, lift, travel, site risk), (5) overhead (rent, software, insurance, admin), (6) risk and waste (remakes, scrap, change orders), (7) a margin that pays for the capital and the owner's risk. The customer buys none of these. They buy an outcome: a visible, durable object that does a job (wayfinding, brand presence) at a location.

**Step 1 — cost is a sum, price is not.** Cost = M(1+w) + sum(machine_hours x machine_rate) + sum(labor_hours x labor_rate) + install + overhead allocation. Each term is measurable per job, but only after the job is done. Quoting happens before. So the quote must be a forecast of these terms, and forecast error is the real enemy. Any pricing primitive must therefore be cheap to estimate and robust to variance.

**Step 2 — which quantity scales the cost?** For flat/printed/cut signage, the dominant cost drivers scale with area (substrate, ink, print and cut time). For dimensional/fabricated signs (channel letters, monuments), drivers scale with complexity (parts count, perimeter, weld/paint steps) and not area. For install, drivers scale with access difficulty (height, power, permit-adjacent logistics, distance) and not with the sign at all. So no single unit works: the minimal primitive is a per-category unit rate (per sq ft for flat goods, per letter or linear inch for dimensional), plus a separate install line, plus a fixed setup/design charge for the cost that does not scale with quantity.

**Step 3 — fixed vs variable.** Design/prepress/setup cost is incurred once regardless of quantity. Hence quantity breaks: unit price falls as quantity rises because setup amortizes. A schedule is price(q) = setup + q x variable. Customers see this as a discount; it is really arithmetic.

**Step 4 — why not hourly?** Hourly billing makes the customer carry the estimation risk and rewards slowness; a customer comparing bids cannot compare hours. Fixed price transfers risk to the shop, which can pool risk across many jobs (law of large numbers) and which, if it estimates well, earns the spread. So fixed price per job, built from a cost-plus model, is the stable equilibrium for a repeat-job shop. Hourly survives for repair/service where scope is unknowable.

**Step 5 — margin.** Markup on cost must cover overhead (already allocated) plus profit. But the market anchors price on what the customer's alternative costs, so the cost model sets a floor, and competitor/value sets the ceiling. Where ceiling is near floor, don't bid; where far above, price toward value (e.g., a monument at the entrance of a million-dollar community is not priced like its aluminum).

**Step 6 — minimal primitive.** Price = max(floor, value-anchored) where floor = (materials x waste factor) + (area or part-count x production rate) + install line + setup, all x (1 + overhead + margin), with a minimum order charge. For repeat B2B buyers (builders like Lennar), the primitive becomes a rate card per sign type, because it removes estimating cost from both sides.

**Prediction of orthodoxy:** the industry uses per-square-foot rates, multiplier-on-materials rules of thumb, per-letter pricing for channel letters, separate install, minimum charges, and quantity breaks; and warns about underquoting install and not charging for design.

## Corpus answer (searched after derivation)
Industry guides (Graphics Pro, SignShop, Signs101, bookkeeping guides) converge on a bottom-up build: materials x category markup (vinyl ~10x, aluminum/ACM ~3-4x) + estimated hours x *burdened* labor rate (payroll taxes, comp, benefits, non-billable time add 30-50%) + overhead per hour x job hours + install/permits priced separately + target profit. Per-square-foot ($4-$30 typical) is used only as a sanity cross-check. Design/proofing/weeding time is a commonly omitted cost.

Sources: https://graphics-pro.com/education/pricing-signs-and-graphics-profitably/ · https://www.signshop.com/business-mgmt/sales-a-marketing/understanding-sign-pricing/ · https://beancount.io/blog/2026/08/25/custom-sign-shop-bookkeeping-material-markup-labor-burden-installation-pricing-guide

## Delta: **rediscovered**
Same structure: separate buckets, install as its own line, setup/design charged, overhead allocated, margin on top, market check as ceiling. Differences, none contradicting: (a) corpus builds from hours x burdened rate while I led with unit rates (area/part-count) as the estimation primitive; (b) corpus uses category-specific material markups (a market-set value signal) where I used a uniform waste factor + margin; (c) I added the value-anchored ceiling for high-stakes pieces and the B2B rate-card idea, which the sources mention only loosely.

## Commentary
Reasoning reached the orthodox architecture, which validates it, but missed the burdened-labor trap (a practical, not logical, fact) — retrieval adds calibration constants, reasoning adds structure. For B9: rate cards for repeat builders (Lennar) plus install as separate line is consistent with both.
