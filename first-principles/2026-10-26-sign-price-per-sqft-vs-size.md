# Why does price per square foot of a custom sign fall as the sign gets larger?

Date: 2026-10-26

## First-principles answer (written BEFORE any search)

Primitives: a sign's price = cost to the shop + margin. Cost splits into three kinds by how it scales with area A.

1. **Area-proportional cost (variable).** Substrate (aluminum, ACM, PVC), vinyl or ink, laminate. Double the area, double the material. This is a floor: price/sqft can never fall below it. Roll goods add a twist: material comes in fixed widths (e.g. 48", 60"), so waste depends on how the piece fits the roll, not on A alone.
2. **Per-job fixed cost (does not scale with A).** Quoting, artwork prep and proofing, file setup, machine setup, RIP/nesting, first-article check, packing paperwork, invoicing, a minimum on any order. A 2 sq ft sign and a 20 sq ft sign need nearly the same human minutes up to the point of production. Spread over A, this cost per sqft is F/A: hyperbolic decay. This is the dominant effect at small sizes.
3. **Perimeter / count-proportional cost.** Edge finishing, framing, hardware, cut paths, hems, mounting holes. Scales with P, which grows as sqrt(A) for similar shapes. So per sqft it falls as 1/sqrt(A), a weaker version of the same decay.

So price/sqft ≈ m + F/A + p/sqrt(A), with m the material+machine-time rate. It falls steeply when A is small, then flattens toward m. It does not fall forever, because at large A new costs appear: bigger pieces exceed machine bed or roll width (seams, tiling), need handling labor, crating, freight, forklifts, installation equipment (lift, crane), and structure (thicker substrate, framing). Those are step functions that raise the curve at some sizes. Expected shape: steep drop, plateau, then a bump or rise at the extremes.

Second force, pricing psychology: customers anchor on total price, not per-sqft, and a shop's margin target is on the job. Shops also discount to win volume because their capacity is mostly fixed (machine hours, labor), so marginal cost of one more sqft is below average cost. Price tiers are the market's way of passing along the F/A saving while keeping a minimum charge.

Prediction: quoted per-sqft rates are tiered by size bands; there is a minimum order charge; material-limited sizes (roll width, 4x8 sheet) mark breakpoints; rates differ by product (more labor-heavy products flatten later).

Confidence in this derivation: high on structure (fixed vs variable), medium on exact shapes.

## Corpus answer
Practitioner consensus (signs101 threads, a sign-painter pricing guide):
- Per-sqft price falls with size; a flat per-sqft rate is considered a mistake. Common method is a sliding scale from a max rate (small) to a min rate (large), e.g. $24 max / $6 min; multiple copies are treated as one large job.
- Setup/handling time does not shrink with size (a 6" sign takes about as long to cut, weed, mask, apply and bill as a 24" one), so shops set a minimum charge from the timed simplest job.
- Minimums trade profit on tiny jobs against losing small first orders that grow into larger accounts.
- Total price still rises with size (materials, installation).
Sources: https://www.signs101.com/threads/square-foot-pricing.60414 , https://signs101.com/threads/minimum-charges.60212 , https://www.signs101.com/threads/printing-prices.160607

Caveat: forum opinion, not authoritative data.

## Delta category: rediscovered

The fixed-vs-variable decomposition, the minimum charge, and the falling-then-flattening rate all match. Gaps in the corpus answer (not novel, but sharper): the corpus gives no functional form; the derivation suggests m + F/A + p/sqrt(A) with the perimeter term, and predicts upward bumps at roll-width / sheet-size / handling breakpoints, which the forum answer does not mention. Untested: whether those bumps show in real B9 quotes.

## Commentary
Reasoning from cost structure alone reproduced the orthodox answer, so it validates using this chain for B9 quote logic. Next step worth testing: fit B9 historical quotes to the three-term form to set tier breakpoints rather than copying a forum's $24/$6.
