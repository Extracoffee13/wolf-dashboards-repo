# First-Principles Spike — 2026-09-09

## Question

From first principles, what determines the appropriate capitalization
(cap) rate for a single-tenant, net-lease (NNN) retail property — and how
should it move with (a) tenant credit quality, (b) remaining lease term,
and (c) expected market rent growth?

*Source: backlog was empty/missing, so this question was generated as
relevant to Hartley Capital strategy and real estate fundamentals.*

## First-Principles Answer (derived before any search)

Start from the only fundamental law of asset pricing: price equals the
present value of future cash flows, discounted at a rate reflecting their
risk and timing.

Price = Σ CF_t / (1+r)^t

A cap rate is a shorthand collapsing this into one ratio: Cap Rate =
NOI / Price, i.e. Price = NOI / Cap Rate. If cash flow grows at a constant
rate g forever and the discount rate r is constant, the infinite sum
collapses to the Gordon growth perpetuity: Price = CF₁ / (r − g).
Matching terms: **Cap Rate = r − g**. Everything else is about deriving r
and g for this specific asset class.

**Decomposing r.** r is built from a risk-free rate plus a stack of
risk premiums specific to the cash flow being priced:
r = r_f + illiquidity premium + credit/default premium + re-leasing
risk premium + structural/obsolescence premium + systematic real-estate
premium.

The key structural insight for a *single-tenant* NNN deal: unlike a
multi-tenant property, where idiosyncratic vacancy risk is diversified
away across many leases, a single-tenant property's entire NOI is a bet
on exactly one counterparty. There is no pooling. That makes the
in-term cash flow of a single-tenant NNN lease economically much closer
to a corporate bond (a fixed promise to pay, from one obligor, for a
fixed term) than to a typical diversified real-estate cash flow. The
landlord is effectively holding two claims stapled together: (1) a
bond-like claim on contractual rent for the remaining term, and (2) a
real, uncertain reversionary claim on the building's value/re-leasing
prospects after the tenant's lease ends (or doesn't renew).

Given that framing, each variable falls out mechanically:

**(a) Tenant credit quality.** This prices the bond-like leg. Higher
credit quality (investment-grade, national tenant) → lower probability of
default over the term → smaller credit spread demanded over the risk-free
rate → lower r → lower cap rate, all else equal. The relationship should
be *convex*, not linear: because a single-tenant property has zero
diversification, default isn't a partial haircut, it's a 100% income
stop plus real re-tenanting costs (downtime, tenant improvements, broker
fees, possibly a building reconfigured for one specific use). So the
jump from investment-grade to non-rated/local credit should be
disproportionately large relative to the "true" marginal default
probability difference — investors are pricing tail risk, not just
expected loss.

**(b) Remaining lease term.** Longer remaining term → a larger share of
total value sits in the low-risk, bond-like leg and a smaller share sits
in the uncertain reversionary leg → lower blended r → lower cap rate.
But this should also be convex near the short end: once remaining term
drops below the time it realistically takes to re-lease or reposition
the asset (roughly a few years), the market effectively re-prices the
whole property *as if* it must be re-tenanted soon, and cap rates should
jump sharply rather than glide down smoothly. Term and credit should also
interact multiplicatively rather than additively — long term with weak
credit is not simply "long term is good": it's a long, undiversified bet
on a shaky counterparty, which is arguably worse than a short lease to
the same tenant.

**(c) Expected rent/market growth.** Directly from Cap Rate = r − g,
higher expected g lowers the cap rate for a given r. But in an NNN
structure, most operating-cost growth risk is contractually shifted to
the tenant (that's what "net" means), so g during the lease term is
mostly mechanical — fixed step-ups or a CPI-linked formula written into
the lease — rather than organic market appreciation. Real, uncertain
market rent growth only becomes economically relevant again at the
reversion point, where it affects the size and risk of the second
(real-estate) leg of the claim.

**Synthesis.** Cap Rate ≈ [weight_term-certain × (r_f + tenant credit
spread)] + [weight_reversion × (r_f + real-estate/re-leasing risk
premium)] − [contractual escalator rate, weighted by term-certain share,
plus assumed market rent growth, weighted by reversion share]. This
predicts the ranking: credit quality dominates, then remaining term
(with convexity at both a very-short-term cliff and a credit/term
interaction), then escalation structure — with "real estate quality"
(location, alternate-use value) mattering more the shorter the remaining
term, because more of the bet is on what happens *after* this tenant.

## Corpus Answer (found via search, after the above was written)

Live 2026 net-lease market data and industry sources confirm this
decomposition almost exactly:

- Cap rates for single-tenant net-lease assets in 2026 range from the
  mid-4% area for trophy ground leases to the high-7%/low-8% area for
  weaker credit or short-term assets; investment-grade net lease cap
  rates are holding near 6.80%.
- **Credit:** industry practice explicitly prices the credit leg "as
  approximately the corporate-bond OAS for the same rating and duration,
  adjusted upward 50–100 bps for the operating-asset nature" — i.e. the
  exact bond-decomposition framing derived above, down to treating it as
  a spread-over-Treasury problem.
- **Term:** documented same-tenant comparables show large, convex swings
  with remaining term — e.g. Walgreens at 6.75% cap with 15–19 years
  remaining vs. 9.25% with under 5 years remaining; CVS 6.35% (15–19 yrs)
  vs. 8.45% (<5 yrs). Hundreds of basis points of movement within the
  *same* tenant, confirming term is priced independently of credit and
  with a convex/cliff-like jump at the short end.
- **Rent growth:** confirmed as contractual — fixed bumps or CPI-linked
  escalators baked into the lease, known to the owner in advance, exactly
  as the "mechanical g during term" framing predicted.
- General framing statement from the corpus: cap rates "fairly price
  tenant credit, lease term, guaranty strength, rent bumps, real estate
  quality, and replacement risk" — the same variable list derived above.

Sources: [NNN Cap Rates 2026: Current Rates by Tenant](https://investmentgrade.com/nnn-cap-rates-2026/),
[Investment-Grade Net Lease Cap Rates Hold Near 6.80%](https://investmentgrade.com/investment-grade-net-lease-cap-rates-q1-2026/),
[Single-Tenant Triple Net Lease: Credit & Cap Rate Decomposition](https://apers.app/learn/asset-classes/retail/net-lease-single-tenant-credit-cap-rate-decomposition),
[Triple Net Lease (NNN): An Operator's Playbook](https://thesisdriven.com/guides/triple-net-lease)

## Delta

**Category: rediscovered**

The reasoning chain (Gordon growth → r − g → bond/reversion decomposition
→ convexity at credit floor and term cliff → mechanical vs. market
growth) landed on the same structure institutional net-lease pricing
actually uses, including the specific "price the credit leg like a bond
OAS" move that a domain specialist would reach for by pattern-matching
rather than re-deriving. That the corpus independently uses the same
bond-decomposition language is a strong validation signal, not just a
coincidence of vocabulary — it means the underlying economic logic
(concentration risk removes diversification benefit, therefore the whole
asset degenerates toward a single-obligor credit instrument) is the
*actual* mechanism practitioners are pricing, not a post-hoc story.

## Commentary

The convexity claims (short-term cliff, credit/term interaction) were
predicted but not directly quantified by the search snippet — the
Walgreens/CVS comparables show the *direction and rough magnitude*
(hundreds of bps) but not enough term granularity to confirm the shape
of the curve between "long" and "under 5 years." That's the one place
first-principles reasoning went further than what the corpus search
surfaced — worth a follow-up spike with actual cap-rate-vs-term
regression data if this framework ever needs to be operationalized for
an underwriting model rather than reasoned about qualitatively.
