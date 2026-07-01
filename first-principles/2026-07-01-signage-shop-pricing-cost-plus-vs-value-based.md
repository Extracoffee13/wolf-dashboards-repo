# First-Principles Spike — 2026-07-01

## Question

How should a small custom-signage shop (Brand 9 Signs) price a job:
cost-plus on materials/labor, or value-based on the customer's expected
revenue lift?

## First-Principles Answer (no retrieval)

Start from the trade primitive. A transaction happens when a price `P`
exists such that the buyer's willingness to pay `V` (their perceived value)
satisfies `P <= V`, and the seller's cost `C` satisfies `P >= C`. Any price
in `[C, V]` is *feasible* — trade is efficient whenever `C <= V`, regardless
of where in that interval `P` lands. Where `P` actually lands inside that
interval is a *distributional* question (who captures how much of the
surplus `V - C`), not an efficiency question. That separation is the whole
ballgame: cost-plus and value-based pricing are two different rules for
picking a point in `[C, V]`, and the right rule depends on what you can
observe and what market structure you're in.

**Cost-plus (`P = C * (1 + margin)`)** anchors on `C`, which a signage shop
can observe directly and cheaply: material cost, fabrication hours, permit
fees, install labor. It guarantees `P >= C` (survival) by construction, but
has no mechanism to track `V` at all. That means it systematically leaves
surplus on the table when `V >> C` (a sign that's core to a restaurant
launch might be worth far more to the customer than its BOM+labor suggests),
and it can also kill deals that would otherwise be efficient trades when the
target margin pushes `P` above `V` for a price-sensitive buyer, even though
some lower `P >= C` would have closed.

**Value-based (`P = f(V)`)** tracks the actual size of the pie, so it can
capture more surplus when `V` is high. But it requires estimating `V`, and a
small shop has no access to the customer's internal revenue model — "this
sign will lift foot traffic by X%" is not a number Brand 9 Signs can compute
with any precision. Strict value-based pricing (price as a measured fraction
of ROI) is therefore rarely *implementable* at the SMB level; what's
implementable is a proxy version, using signals correlated with value —
deal is tied to a store launch/opening, sign is the primary brand asset (not
a secondary directional/ADA sign), buyer is a franchise with a pre-set TI
budget line for signage, buyer shows low price sensitivity in the RFP
conversation, no competing quote in hand.

Two structural forces decide which rule dominates for a given job:

1. **Market structure.** When a job is competitively bid against
   like-for-like specs (standard vinyl banners, ADA/code-required signage,
   repeat maintenance), competition compresses the achievable price toward
   `C` regardless of the buyer's true `V` — quoting above the market-clearing
   cost-plus margin just loses the bid. Cost-plus isn't a philosophical
   choice here, it's forced by the game.
2. **Differentiation and information asymmetry.** When a job is a one-off,
   design-led, or tied to something high-stakes for the buyer (a brand
   launch, a flagship storefront), there's no comparable competing bid to
   anchor against, and `V` genuinely varies a lot across buyers. This is
   where value-based (proxy-based) pricing can capture real surplus that
   cost-plus would leave on the table.

**Invariant that never goes away:** cost-plus is not "wrong" even in the
value-based regime — it's the floor. No matter how high `V` looks, `P` must
never structurally sit below marginal cost plus a minimum viable margin,
because a business can't survive on theoretical surplus if realized cash
flow doesn't cover inputs. Value-based reasoning only ever operates on
*where above the floor* to price, never on whether the floor applies.

**Conclusion:** the right answer is neither pure cost-plus nor pure
value-based — it's a segmented/hybrid rule: cost-plus with a healthy margin
as the default for standardized, competitively-bid work (the floor doubles
as the price in this regime because competition compresses the surplus
capture to near `C`); proxy-informed value-based pricing for differentiated,
launch-critical, or design-forward work, bounded below by the same cost
floor. The segmentation variable is competitive exposure + differentiation,
not job size or customer type.

## Corpus Answer

Standard pricing-strategy literature (small-business pricing guides,
consulting-firm blog consensus) converges on exactly this framing:
cost-plus pricing is for predictable-cost, standardized/commoditized
products; value-based pricing is for differentiated offerings where
customer perception of worth diverges from production cost. The dominant
practical recommendation is explicitly hybrid: **"cost-plus pricing
establishes your price floor... while value-based pricing helps you
identify your price ceiling"** — i.e., use both together, segmenting by
customer/offering rather than picking one method company-wide. Value-based
guides also stress segmenting the customer base since perceived value
varies by segment, and note that true value-based pricing depends on being
able to estimate what the offering is worth to the customer — often via
proxies rather than precise ROI calculation.

## Delta Category

**rediscovered**

## Commentary

The independent derivation and the corpus consensus land on the same
structure almost exactly: cost as floor, value as ceiling, segment by
differentiation/competitive exposure rather than by picking one pricing
philosophy globally. The one thing the first-principles pass adds that the
generic corpus framing doesn't spell out as clearly is *why* competitive
bidding forces cost-plus specifically (it's not that standardized products
are inherently cost-plus-priced, it's that visible competing quotes
compress the achievable surplus capture toward `C` regardless of true `V`) —
a mechanism, not just a category label. Confidence in the match: high.
