# First-Principles Spike — 2026-08-10

## Question

Why does the physical sign industry price primarily by square footage rather
than by labor hours or flat cost-plus?

(Selected by AP: `first-principles-backlog.md` was missing from the repo, so
this question was generated fresh, chosen for direct relevance to Brand 9
Signs operations.)

## First-principles answer (derived before any search)

A sign transaction has two parties with different native units of value.
The buyer cares about outcome — visibility, legibility at distance, code
compliance, duration. The producer's actual costs land in totally different
units: sheet material, paint, LEDs, welder-hours, install-crew-hours,
bucket-truck time, engineering stamps, permit fees. No unit is naturally
shared by both sides, so whatever pricing unit wins the market has to be an
*invented* translation layer — and the question is which invented unit
survives competition.

Two candidate units compete: (a) **cost-plus** — sum actual costs per job,
add margin; (b) **a proxy metric** correlated with both cost and value that
can be quoted instantly. Cost-plus is the economically "true" price, but it
fails in a live sales process three ways: it requires fully costing a job
*before* quoting, which is slow and loses deals to competitors who quote
same-day; it invites buyer distrust, since labor hours are unverifiable by
the buyer ("why did it take you 40 hours?"); and it rewards the producer for
taking longer, a perverse incentive misaligned with the buyer's actual
interest in speed.

Square footage wins because it is the cheapest-to-communicate variable that
is simultaneously: (a) roughly linear in material cost for a given
technique — more substrate, vinyl, paint, LED modules; (b) roughly monotonic
with fabrication/install labor for a given technique, since most cutting,
mounting, wiring, and lifting labor scales with physical size; (c) directly
observable and verifiable by both sides without opening up the shop's
internal process — buyer and seller can both measure the same 4'×8' panel
and agree on the number; and (d) *already the buyer's native mental unit*,
because municipal sign codes independently regulate signage by allowable
square footage per linear foot of building frontage. That last point is the
load-bearing one: the regulatory environment forces every buyer to already
be thinking "how many square feet am I allowed," so a pricing unit matching
the regulatory unit costs the buyer zero translation effort. A pricing unit
that piggybacks on a constraint the buyer is already tracking will
out-compete a unit that doesn't, independent of which is more "accurate" to
true production cost.

But square footage is an imperfect linear proxy — cost is not actually
linear in area alone. A push-thru backlit channel-letter sign and a flat
printed aluminum panel of identical square footage carry very different
material and labor costs (electrical, engineering stamp, welding vs.
print-and-mount). A single blanket $/sq-ft rate would either overcharge
simple jobs — losing them to competitors — or undercharge complex jobs —
losing money — so competition should arbitrage a pure single-rate scheme
away.

The predicted stable equilibrium, therefore, isn't "square footage" alone —
it's square footage **crossed with a small number of discrete
complexity/material tiers** (flat non-illuminated vs. routed/backlit vs.
individual channel letters, each at a different $/sq-ft rate), with the
genuinely non-area-scaling cost centers — permits, engineering, site access,
electrical hookup — billed as separate line items rather than folded into
the per-sq-ft number. This is the cheapest structure that preserves the
buyer's one-number mental model while still tracking true cost closely
enough that no competitor can arbitrage the mispricing away.

## Corpus answer (found via web search, after the above was written)

Search confirms both halves of the prediction:

- Square footage is indeed a standard pricing metric, but **not a single
  blanket rate** — pricing is explicitly tiered by sign type/illumination.
  Custom or illuminated signs run $10–$300/sq ft; monument signs are priced
  separately by the International Sign Association at $150–$400/sq ft;
  channel letters are commonly quoted as whole-project ranges ($800–$20,000+)
  because "channel letter pricing varies significantly based on letter size,
  illumination type, materials, and installation complexity **rather than
  being a straightforward per-square-foot calculation for all sign types.**"
  Permits and site preparation are called out as add-on line items, not
  folded into the sq-ft rate.
- The regulatory-alignment claim is confirmed directly: municipal sign codes
  regulate maximum sign area chiefly via **frontage-based ratios** (e.g.,
  one square foot of sign per one linear foot of primary building frontage),
  meaning the buyer's allowable-size ceiling is already denominated in
  square feet before a sign company is ever contacted.

## Delta category: **rediscovered**

The reasoning chain arrived independently at the two load-bearing claims the
corpus actually uses to justify the industry's pricing structure: (1)
sq-ft-as-base-unit-crossed-with-complexity-tiers rather than a single
blanket rate, and (2) the regulatory (frontage-ratio) origin of why square
footage is the buyer's native unit in the first place. Neither was known in
advance — no retrieval occurred before the derivation was written. This
validates the reasoning process rather than surfacing new information.

## Commentary

The interesting part wasn't the conclusion (a competent operator could guess
"sq ft, tiered by complexity" without much thought) — it was that the
*regulatory* explanation for why sq ft specifically (not, say, linear feet
of letter, or lumens of illumination) is the surviving unit only fell out of
asking "what unit does the buyer already have to think in, independent of
any sign company?" That's a transferable move: when a market converges on a
weird-looking pricing unit, check whether an external constraint (code,
tax, contract standard) already forces both sides onto that unit before
assuming it's arbitrary convention.
