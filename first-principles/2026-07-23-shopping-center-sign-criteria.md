# First-Principles Spike — 2026-07-23

## Question

Why do shopping centers and commercial landlords impose uniform "sign criteria"
(size, style, placement, illumination, materials) on tenants in the lease,
rather than letting each tenant design and install signage freely?

(Selected by the agent — `first-principles-backlog.md` was empty. Chosen for
relevance to Brand 9 Signs' business: sign shops constantly work against
landlord-issued Tenant Design Criteria Manuals, so the "why" behind that
document is directly load-bearing for how B9S scopes and sells jobs.)

## First-principles answer (derived before any search)

Start from the primitives, not the practice:

1. **The facade/site is a shared, single-owner asset used by many independent
   economic agents.** The landlord owns the building and pad; N tenants lease
   space on it. Each tenant's signage decision is made unilaterally, but the
   *effect* of that decision — visual impact, legibility, prestige — lands on
   a shared surface that every other tenant and the landlord also depend on.
   This is a commons/externality structure, not a private-goods structure.

2. **Human visual attention on a given facade is a bounded resource.** A
   driver or pedestrian has a fixed, short window to parse a row of signs.
   If every tenant independently maximizes their own sign's size/brightness
   to win that attention, the *equilibrium* of that uncoordinated game is
   over-investment by everyone (an arms race), not efficient outcomes for
   anyone — my sign competing against a neighbor's escalation is a zero-sum
   fight funded by rising capex on both sides. This is a standard
   tragedy-of-the-commons / prisoner's-dilemma structure: each tenant's
   locally rational move (go bigger) degrades the jointly-owned resource
   (facade legibility, overall image) that determines the property's draw.

3. **The landlord is the residual claimant on the property's aggregate
   value** (rent roll, occupancy, resale cap rate), while no individual
   tenant internalizes that value — each tenant only cares about their own
   storefront. Whenever the party who bears the aggregate cost of an
   externality is different from the parties generating it, and the
   generating parties are too numerous/transient to bargain efficiently
   with each other directly (high transaction costs, tenant turnover), the
   textbook Coasean resolution is: the party holding the unified property
   right sets the rule ex ante by contract, rather than relying on ex post
   tenant-to-tenant negotiation. That rule is the sign criteria, written
   into the lease before the tenant ever designs a sign.

4. **Municipal sign ordinances impose a hard, finite cap** — e.g., max sign
   area per linear foot of frontage, height limits, illumination limits —
   on the *entire* building, not per-tenant. That converts "how much sign
   area exists" into a literal fixed-size commons that must be *rationed*
   across N tenants. A first-come-first-served scramble under a hard cap is
   unstable (last tenant in gets nothing, or the total silently exceeds the
   permit and the landlord — who holds the master CO/permit, not any single
   tenant — eats the code-violation liability). Rationing by an ex-ante rule
   (e.g., allocation proportional to frontage) is the stable solution to a
   fixed-budget allocation problem with many claimants.

5. **Consistent, bounded sign format is also a wayfinding public good.**
   If every sign uses a different scale, mounting logic, and idiom, a
   visitor's cognitive load per additional sign rises, and legibility of
   the *whole* property falls — which hurts foot traffic for every tenant,
   including the ones who "won" the local arms race. A shared visual
   grammar (letter height bands, consistent mounting height, limited
   palette) is what keeps marginal cognitive cost of reading one more sign
   low, which is a property-wide asset, not any one tenant's.

6. **Bargaining power is not uniform across tenants.** An anchor tenant
   (national chain with real draw power) contributes more to property value
   than it costs in externality — the landlord *wants* their strong,
   recognizable branding visible, even if it breaks the criteria, because
   the anchor's pull effect outweighs the visual-consistency cost. A small,
   unknown tenant does not have that offsetting value, so the criteria bind
   tightly for them. This predicts an asymmetry: criteria documents will
   carve out exceptions/riders for anchors and enforce uniformity strictly
   on in-line/small-shop tenants.

**Predicted concrete features of the practice**, derivable purely from the
above, before checking any source: landlords will (a) retain sign *approval*
rights over shop drawings prior to permit submission, (b) specify allowed
sign types and a max area formula tied to frontage, (c) restrict
color/material/illumination to a limited palette, (d) require tenant-funded
install and end-of-term removal/restoration, and (e) write anchor-tenant
carve-outs as separate exhibits. None of this requires reading a single
lease — it falls out of shared-asset economics, fixed-budget rationing, and
heterogeneous bargaining power.

## Corpus answer (found after searching)

Retail real-estate practice confirms this almost point for point, though the
practitioner literature states it as business/aesthetic doctrine rather than
deriving it:

- Landlords reserve sign-approval rights because non-conforming signage can
  "look physically unpleasing or be harmful to the reputation of the
  property" — i.e., the externality/reputation argument (Law Insider,
  franchise/retail lease commentary).
- Most shopping centers formalize this as a **Tenant Design Criteria Manual
  (TDCM)** specifying letter height, materials, mounting method,
  illumination type, and color — matching the predicted "bounded visual
  grammar" feature.
- Signage is regulated at **two layers**: the property's own private,
  contractual sign criteria, and the municipality's public sign ordinance —
  both must be satisfied, confirming the "fixed regulatory budget +
  privately imposed rationing on top" structure.
- Pylon/monument signs in particular are described as scarce: "there are
  often more tenants than sign panels available," and tenants are warned
  not to assume they'll get a panel — direct confirmation of the
  fixed-resource rationing dynamic.
- Anchor tenants are explicitly documented as getting more leeway: "if a
  tenant demands the right to have an identification sign on a center's
  pylon sign, landlords may need to give strong tenants more leeway on many
  of the conditions required" — confirming the bargaining-power asymmetry
  prediction.

Sources:
- [Signage Provisions in Commercial Leases — Hollander Real Estate Law](https://hollanderpllc.com/2024/08/signage-provisions-in-commercial-leases/)
- [Shopping Center and Multi-Tenant Signage — Lee's Signs](https://www.leessign.com/blog/shopping-center-multi-tenant-signage)
- [Keep Control over Tenant's Sign on Shopping Center's Pylon — The Habitat Group](https://www.thehabitatgroup.com/keep-control-over-tenants-sign-on-shopping-centers-pylon/)
- [Tenant's Signage Rights Sample Clauses — Law Insider](https://www.lawinsider.com/clause/tenants-signage-rights)
- [Pylon Sign Sample Clauses — Law Insider](https://www.lawinsider.com/clause/pylon-sign)

## Delta

**Category: rediscovered** (with a secondary novel angle)

The first-principles derivation landed on the same operative practice the
corpus documents — approval rights, uniform design manuals, two-layer
(private + municipal) regulation, panel/area scarcity, and anchor-tenant
carve-outs — without having read any lease-law source first. That's a clean
rediscovery.

The one thing the practitioner corpus doesn't do, which the derivation adds,
is *why* in economic terms: it never frames sign criteria as a Coasean
response to a commons/externality problem, or the uncoordinated-escalation
game theory of why unrestricted signage tends toward mutually wasteful
over-investment. The corpus states these rules as landlord preference /
aesthetic control / "reputation" without deriving the underlying incentive
structure. That framing gap is real but modest — it's an explanatory layer
on top of an already-known practice, not a new practice or a corpus error.

## Commentary

Directly useful for Brand 9 Signs: when a TDCM feels arbitrarily restrictive
to a client, the honest explanation isn't "landlord being picky," it's
"you're one claimant against a fixed, shared sign budget, and the rules
exist to keep everyone's sign legible against everyone else's." That's a
better sales/expectations conversation than treating criteria as pure
bureaucracy — and it predicts where a client *can* push (making a case that
their brand adds anchor-like value) versus where they can't (routine in-line
frontage with a hard municipal area cap).
