# First-Principles Spike — 2026-07-27

## Question

From first principles, how should Brand 9 Signs price a custom job (e.g. an
illuminated channel-letter sign or monument sign) — cost-plus, value-based,
or market/competitive pricing — and why do these three methods diverge in
practice?

*(Backlog was empty; question generated fresh, chosen for direct relevance
to Brand 9 Signs operations.)*

## First-Principles Answer (derived before any search)

**Primitives.** A sign is a durable capital good a business buys to perform
one function: convert anonymous foot/vehicle traffic into store visits by
communicating identity, location, or offer. The seller (Brand 9 Signs)
incurs observable costs — materials, fabrication labor, design/engineering,
permitting labor, installation labor and equipment, overhead, and
liability/compliance risk (electrical code, structural wind load). The
buyer's willingness to pay is bounded above by the expected value the sign
creates for their business over its life (or the cost of the best
substitute, whichever is lower), and below by nothing — a buyer will always
prefer to pay less.

**Three pricing philosophies, restated as bounds, not competing "correct"
answers.**
1. *Cost-plus* (price = cost × (1+margin)) is a **floor**: below marginal
   cost, the job destroys value for the seller and shouldn't be taken at
   any price. It says nothing about what the buyer would actually pay.
2. *Value-based* pricing is a **ceiling**: it prices toward the economic
   value created for the buyer (incremental revenue from visibility, or —
   more measurably — avoidance of a concrete cost like a lease-covenant
   default penalty or a franchise brand-standard violation).
3. *Market/competitive* pricing is the **empirical resolving mechanism**
   between floor and ceiling: it's what emerges when buyers can gather
   multiple comparable quotes, which forces price down toward
   cost-plus-with-thin-margin for any spec that's easy to compare across
   vendors.

None of the three is "the" correct method for a business as a whole — they
are different tools that dominate under different competitive conditions.

**Why they diverge.** Two information asymmetries drive the split:
- The seller knows true cost; the buyer usually doesn't. So cost-plus is
  best used as an *internal* discipline (every job must clear a minimum
  margin) rather than a customer-facing pricing philosophy.
- The economic value of a sign is very hard to measure in the general case
  (you can't run a controlled experiment on incremental foot traffic per
  client), so *pure* value-based pricing is rare for ordinary retail
  signage. It becomes tractable — and lucrative — exactly when the "value"
  collapses into something concrete and large relative to sign cost: a
  landlord-mandated signage deadline with a monetary lease-default penalty,
  a franchise rebrand compliance deadline, or a rush job blocking a grand
  opening. In those cases the relevant "value" isn't diffuse revenue lift,
  it's a hard number (the penalty avoided, or the opening-day revenue at
  stake), which is exactly measurable enough for value-based pricing to
  work.

**Derived decision rule.** Segment by two signals, not by picking one
company-wide method:
1. Always compute the cost-plus floor per job — a hard accept/reject gate.
2. For commodity-like specs (standard channel letters, standard box signs)
   where buyers can and do collect 3 competing quotes, price near the
   market band — competition will erode any premium anyway, and the real
   margin lever is operational efficiency (crew utilization, shop
   throughput), not price.
3. For jobs where competition is thin (Brand 9 Signs is the
   franchise-approved vendor, holds the permitting relationship, or is the
   only shop with UL-listed electrical capacity for the spec) *and* the
   buyer faces a large, quantifiable cost of not having the sign in time
   (lease penalty, franchise non-compliance fine, grand-opening revenue),
   price toward that quantified ceiling, not toward cost-plus.
4. Urgency and single-supplier status are therefore the two signals that
   tell you which pricing regime applies to a given job — they function as
   a practical proxy for "is this a differentiated, high-stakes sale or a
   commodity one," which is otherwise hard to assess directly.

This reduces to price discrimination across jobs based on competitive
intensity and stakes, rather than a single storefront price list.

## Corpus Answer

Standard B2B pricing-strategy literature (Nagle-style "economic value to
customer" framework, and current industry commentary) converges on the same
structure: cost-plus is explicitly framed as a floor/internal-control
mechanism, not a strategic pricing method, and is discouraged as the primary
basis for differentiated offerings. Value-based pricing is presented as
superior specifically for differentiated, hard-to-compare offerings, and is
described as working "when three things line up: the economic impact is
measurable, the customer can perceive it, and the problem is material
enough to drive buying behavior" — which matches this spike's
"value collapses into something concrete and large" condition almost
exactly. Cost-plus/competitive pricing is explicitly recommended instead
for standardized goods and transparent/public-tender situations, matching
the "commodity spec, buyer can collect competing quotes" branch derived
above. Industry sources also cite a ~50%+ persistence of cost-plus in
practice despite its inferiority for differentiated work, attributed to
measurement difficulty of value — the same information-asymmetry
explanation given here for *why* the divergence exists, not just *that* it
exists.

Sources consulted: nibusinessinfo.co.uk ("Cost-plus versus value-based
pricing"), Vistaar ("Value-Based Pricing: Align Prices with Customer
Value"), Priceagent ("Value-based pricing vs. Cost-plus pricing"), CRV
("B2B Pricing Models and Strategies for Founders").

## Delta Category: **rediscovered**

The first-principles chain arrived independently at the standard
floor/ceiling/market-resolution framing and, more specifically, at the same
"measurable + perceivable + material" gating condition the corpus uses to
decide when value-based pricing is viable — without having read that
framework going in. The added value of the first-principles pass isn't a
new answer; it's a concrete, checkable operationalization for Brand 9 Signs:
use *single-supplier status* and *quantifiable buyer urgency/penalty* as
the two observable signals for routing a given job to value-based vs.
market pricing, rather than treating pricing as a single company-wide
policy choice.

## Commentary

The reasoning chain treated "cost-plus vs. value-based vs. market" as a
false trilemma from the start (three bounds/mechanisms, not three
competing answers), which is what let it converge on the corpus's structure
without having seen it. The one thing the corpus adds that the derivation
didn't originate independently is the empirical stat (1% price improvement
→ 6-14% more operating profit) and the observation that cost-plus
persists despite being suboptimal in >50% of B2B manufacturers — a
real-world adoption-lag fact, not a reasoning result, and exactly the kind
of thing first-principles reasoning can't produce and retrieval is for.
