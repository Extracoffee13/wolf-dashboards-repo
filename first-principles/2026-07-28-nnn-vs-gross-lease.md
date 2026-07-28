# First-Principles Spike — 2026-07-28

## Question

From first principles, why do commercial real estate leases predominantly
use triple-net (NNN) structures rather than gross leases — and when should
a landlord retain operating-cost risk instead of passing it to the tenant?

Relevance: Hartley Capital strategy touches CRE deal structuring directly;
Brand 9 Signs also operates as a tenant/landlord counterparty in leased
retail and industrial locations, so the incentive logic behind lease form
is a load-bearing primitive for both.

## First-Principles Answer (derived before any search)

A lease is a contract that allocates two separable things: a rental income
stream, and exposure to the variability of operating costs (property tax,
insurance, maintenance/repair, utilities). Treat them separately, because
the efficient owner of the income stream is not necessarily the efficient
bearer of the cost-variance risk.

**Who should bear a risk?** A risk should sit with whichever party can (a)
control or mitigate it, (b) forecast/price it most cheaply, or (c) absorb
it at lowest cost (via diversification or capital access). This is the
standard risk-allocation logic behind any efficient contract, not specific
to real estate.

**Landlord vs. tenant capabilities.** The landlord holds the asset across
many tenants and years, has specialized knowledge of the building's
systems, and is the only party positioned to make long-horizon capital
decisions (roof, structure). The tenant controls its own day-to-day usage
— hours of operation, occupancy density, equipment load — which is the
actual driver of variable costs like utilities and wear-and-maintenance.

**The moral hazard problem with gross leases.** Under a gross lease the
landlord absorbs cost variance while the tenant controls the behavior that
drives much of that variance. Cost driver and cost bearer are decoupled —
a tenant has no price signal to discipline usage (leaving HVAC running,
etc.), because the marginal cost of that behavior doesn't land on them.
Pushing operating costs onto the tenant (net lease) re-couples control and
consequence.

**But this doesn't fully explain NNN dominance by itself** — a landlord
could in principle charge a gross rent that prices in expected cost
variance and pocket the spread, betting that variance nets out across a
portfolio of many buildings and tenants (an insurance-style pooling
argument). This works for *idiosyncratic* risk (a burst pipe in Building A
is uncorrelated with one in Building B). It does *not* work for
*systemic* risk: property tax reassessment cycles, insurance-market
hardening, and regional utility rate hikes tend to hit a landlord's whole
portfolio simultaneously if concentrated in one metro or region. Owning
more buildings doesn't diversify away a correlated, market-wide cost
shock — so retaining that risk under a gross lease is simply an unpriced
bet the landlord is forced to take, not a diversification benefit.

**Financing pressure compounds this.** A lender underwriting the building
wants a stable, bond-like income stream to size a debt-service coverage
ratio against. Variable opex risk sitting on the landlord's side makes the
net operating income noisy and harder to lever. Converting the lease to
NNN turns base rent into something closer to a fixed coupon: cost overruns
no longer touch debt service. So the case for NNN isn't purely about
landlord-tenant incentive alignment — it's also about making the income
stream financeable/securitizable at scale (this is presumably why
"sale-leaseback with a net lease REIT" is a recognizable deal pattern:
the REIT is functionally a bond buyer wrapped in a real estate wrapper).

**Predictions from the reasoning, before checking the corpus:**
1. NNN should dominate single-tenant, build-to-suit assets where the
   tenant fully controls usage and the landlord is essentially a passive
   financing vehicle.
2. NNN should correlate with creditworthy tenants who can absorb opex
   volatility without financial distress.
3. Gross leases should persist where transaction costs of metering/
   splitting costs among many small, high-churn tenants exceed the
   risk-transfer benefit (small multi-tenant strip retail, coworking,
   executive suites) — landlord bundling (one utility bill, shared HVAC)
   is cheaper than itemizing.
4. NNN prevalence should rise when opex (insurance, taxes) is a large and
   rising share of total occupancy cost, since that's exactly the
   non-diversifiable risk landlords most want off their books.

## Corpus Answer (found after searching)

Search confirms the core mechanism: NNN "solves" landlord exposure to
unpredictable tax/insurance/repair cost growth by transferring that risk
to the tenant, and this shift was historically driven by cost volatility
making landlord income unstable and hard to underwrite. The dominant
framing in the net-lease REIT literature is explicitly financing-centric:
net lease income is described as "bond-like," and "bondable NNN leases"
are the standard vehicle for sale-leaseback deals where a REIT or
insurance company acts as a passive, debt-like capital provider to a
creditworthy corporate tenant. Gross leases are described as the
multi-tenant default where the landlord absorbs expense variance and
recovers it (if at all) through a single blended rent, consistent with
the small-tenant/high-metering-cost prediction.

Sources:
- [The Benefits and Risks of Triple Net Leases — NAIOP](https://www.naiop.org/research-and-publications/magazine/2017/summer-2017/marketing-leasing/the-benefits-and-risks-of-triple-net-leases/)
- [Triple Net Lease (NNN): An Operator's Playbook — Thesis Driven](https://thesisdriven.com/guides/triple-net-lease)
- [Triple Net Lease (NNN): Costs & Risks for CRE Investors — LoopNet](https://www.loopnet.com/cre-explained/finance/understanding-the-triple-net-lease/)
- [Net Lease Real Estate: Unlocking a $13.4 Trillion Opportunity — J.P. Morgan Asset Management](https://am.jpmorgan.com/us/en/asset-management/institutional/insights/portfolio-insights/alternatives/net-lease-real-estate/)
- [Net Lease REITs — Hoya Capital](https://www.hoyacapital.com/reit-sectors/net-lease)
- [Benefits of investing in a triple net lease over bonds — Dennis Piper](https://blogs.oregonstate.edu/piperde/2022/04/28/benefits-of-investing-in-a-triple-net-lease-over-bonds/)

## Delta Category: **rediscovered**

The reasoning chain (risk should sit with whoever controls it → gross
leases create a moral-hazard mismatch → pooling only works for
idiosyncratic, not systemic, cost risk → financing demand for a bond-like
income stream) landed on the same mechanism the corpus gives, independent
of vocabulary. The corpus even supplies the exact phrase the reasoning was
groping toward without having seen it: "bondable NNN lease."

One piece — the idiosyncratic-vs-systemic-risk distinction as the reason
portfolio diversification *fails* to justify landlords retaining opex risk
— wasn't stated as such in the sources pulled. It's a standard portfolio-
theory idea applied to a niche it's rarely made explicit for in real
estate writing, so it sits at the edge between "rediscovered" and "novel"
without full corpus coverage to confirm either way.

## Commentary

The financing angle (NNN as bond-ification of real estate cash flow) was
the piece I was least sure of before searching, since it's an argument
about capital markets demand rather than landlord-tenant incentives per
se — and it turned out to be the dominant framing in the actual net-lease
REIT literature, more prominent there than the moral-hazard framing. That's
a useful calibration: when reasoning about "why does contract form X
dominate," the capital-markets/financeability angle deserves at least as
much weight as the bilateral-incentive angle, and probably should be
checked first in real estate specifically, since so much of the sector's
structure is downstream of what's levered easily.
