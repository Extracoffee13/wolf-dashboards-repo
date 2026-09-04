# First-Principles Spike — 2026-09-04

## Question

Why do commercial real estate leases commonly use a triple-net (NNN)
structure — tenant pays property taxes, insurance, and maintenance/CAM on
top of base rent — instead of a gross lease that bundles everything into
one rent figure? What's the underlying incentive-design logic?

## First-principles answer (derived cold, no retrieval)

Start from the primitives: a commercial lease is a contract splitting a
capital asset's cash flows between an owner (landlord, bears value risk)
and a user (tenant, gets exclusive use). Any such contract has to allocate
three things — who bears cost variability, who controls the cost driver,
and who has the information to monitor it. The efficient allocation rule
is: put a cost on whoever can control or monitor it most cheaply (the
least-cost avoider), and don't make anyone bear risk they can't act on
without charging them a premium for it.

Apply that to the three N's:

- **Maintenance/CAM** is the most usage-driven cost — wear, cleaning,
  landscaping, parking-lot upkeep. Tenants directly drive this through how
  they use common areas. Bundling it into gross rent removes any tenant
  incentive to economize, and forces the landlord to forecast a
  hard-to-predict cost and price in a risk premium — a premium that
  penalizes low-maintenance tenants to cover high-maintenance ones. That's
  an adverse-selection problem: cost-conscious tenants would rationally
  seek out NNN deals to avoid subsidizing sloppier co-tenants, so a
  landlord offering only gross leases in a multi-tenant building
  systematically loses its best tenants. In genuinely multi-tenant
  properties there's also no way to do a fair gross lease at all, since
  CAM has to be apportioned across tenants by some formula anyway — NNN is
  just that formula made explicit.
- **Taxes and insurance** are largely outside anyone's control (set by
  local government and the insurance market), but the landlord holds the
  insurable/taxable interest and has the better information about the
  building's risk profile. Passing these through doesn't shift control so
  much as it strips a volatile, hard-to-forecast line item out of "rent" —
  which lets rent behave more like a clean return on capital rather than a
  bundle that includes an implicit insurance-against-tax-hikes product
  nobody is actually pricing well.
- **Net effect for the landlord**: NOI becomes predictable and largely
  decoupled from opex shocks, which matters directly for cap-rate-based
  valuation and for lender underwriting (predictable income is worth more
  and finances more cheaply).
- **Net effect for the tenant**: lower headline base rent (no risk premium
  baked in) in exchange for opex exposure — attractive to tenants
  sophisticated enough to audit CAM statements and long-term enough that
  the transparency pays off over the lease term.

This also explains why gross leases persist: for short-term or small,
unsophisticated tenants (e.g., small office suites), the administrative
overhead of auditing CAM and taxes isn't worth it — they buy budget
predictability and pay a premium for it, which is the mirror image of the
NNN trade. And single-tenant, long-term "credit tenant" NNN deals
(sale-leasebacks to REITs) push this to the limit: the landlord becomes
almost a pure financing vehicle holding title, the tenant bears
essentially all the operating risk, and the "rent" is closer to a coupon
payment than a rental price — the lease is functionally a financing
instrument.

## Corpus answer (web search)

Standard industry framing (real estate explainers — LoopNet, Prologis,
Landlord Studio, Aquila Commercial, etc.):

- NNN passes taxes, insurance, and maintenance to the tenant, giving the
  landlord a net income stream "largely insulated from expense
  volatility" and simplifying landlord accounting/overhead.
- Predictable rental income, often locked in for 10–25 years, is valuable
  to landlords partly because it supports cap-rate-based valuation and
  financing, and landlords can also depreciate the building for tax
  shelter on top of that stable income.
- Tenants get a lower base rent than a comparable gross lease as
  compensation for taking on the cost/risk, and directly capture savings
  if actual opex comes in under the landlord's original estimate.

## Delta

**Category: rediscovered.**

The core mechanism — NNN exists to strip volatile, largely
tenant-usage-driven or externally-set costs out of "rent" so landlord
income is predictable (financing/valuation-friendly) and tenant base rent
is lower in exchange for bearing that risk — matches the standard
explainer answer closely. That validates the incentive-design reasoning
chain.

Two pieces of the derivation aren't stated explicitly in the corpus
material found: (1) the adverse-selection argument for *why* multi-tenant
buildings gravitate to NNN specifically (cost-conscious tenants self-select
away from gross leases that would cross-subsidize sloppy co-tenants), and
(2) the "sale-leaseback as financing lease" framing for single-tenant
credit-tenant NNN deals. Neither contradicts the corpus — they're a level
of mechanism underneath it — so this isn't a corpus-error or fully novel
result, just a case where first-principles reasoning fills in the "why"
behind a "what" the standard explainers state as received wisdom. The one
thing first-principles reasoning missed and the corpus caught: the tax
depreciation shelter benefit to the landlord — a tax-code detail that
isn't derivable from pure incentive theory, it just has to be known.

## Commentary

This is a decent test case for the spike format: the surface answer was
fully recoverable from primitives (principal-agent cost allocation +
least-cost-avoider + risk pricing), which suggests real estate contract
structures are genuinely legible from incentive theory rather than being
historical accidents. The miss (tax depreciation) is a useful marker of
where reasoning-from-primitives hits a wall — anything that depends on a
specific jurisdiction's tax code is a fact to look up, not something to
derive.
