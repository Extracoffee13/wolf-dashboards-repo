# First-Principles Spike — 2026-09-17

## Question

The backlog file was missing, so this question was generated fresh, relevant
to Hartley Capital's real-estate strategy work:

> Why do standard real-estate appraisal frameworks split valuation into
> three separate approaches — cost, sales-comparison, and income — instead
> of computing one canonical "value"? And from first principles, which
> approach should dominate for a given asset class?

## First-principles derivation (no retrieval)

Start from what "value" means to a rational, informed buyer under no
duress: it's the price of the cheapest way to obtain an equivalent unit of
utility. A buyer never pays more for an asset than the cost of the best
available substitute. So the question reduces to: what substitutes are
actually available, and do they all price the same way?

There are exactly three distinct substitution strategies available to a
buyer of real property:

1. **Build it.** Acquire the land and construct an equivalent structure
   from scratch. The ceiling this sets is: land value + cost new − any
   depreciation/obsolescence the target asset already carries relative to
   new construction. This is the engine of the **cost approach**.
2. **Buy an equivalent, already-built unit.** If a liquid market of
   near-identical assets exists and trades regularly, the clearing price of
   those trades is a direct, revealed-preference read on value — no need to
   model anything. This is the **sales-comparison approach**.
3. **Buy the cash-flow claim.** If the asset's value to the buyer is
   principally the income stream it throws off (not its use-value as
   shelter or operating space), the buyer is really pricing a bond-like
   claim: discount the expected NOI stream at the opportunity cost of
   capital for equivalent-risk assets. This is the **income approach**.

Three approaches exist, not one, because "the cheapest substitute" is a
different object depending on what market actually exists around the
asset. There is no single formula because the three substitution markets
(construction market, resale market, capital market) don't always overlap
or agree.

**Which one dominates is then a data-availability argument, not a
preference argument:**　

- When a deep, liquid market of near-identical comparables exists but no
  independent income market does (owner-occupied single-family homes — an
  owner-occupant doesn't rent to themselves, so there's no clean NOI to
  observe), sales comparison is both the cheapest and the most accurate
  substitute-price signal. It dominates.
- When the asset's *raison d'être* to any buyer is the income stream — the
  cash flows are the product being sold (multifamily, office, industrial,
  retail with third-party tenants) — buyers underwrite it as a capital
  asset. Income approach dominates because it directly encodes "another
  income stream of equivalent risk-adjusted yield" as the substitute.
- When neither a resale market nor an income market exists — special-
  purpose property with no comparable transactions and no rentable income
  (churches, schools, refineries, brand-new unique developments) — the
  only substitute a buyer can actually construct is to build one. Cost
  approach dominates by elimination, and it also serves as a universal
  ceiling/sanity check on the other two: no rational buyer pays materially
  more than replacement cost + entrepreneurial profit unless the asset sits
  on genuinely irreproducible scarcity (a location, an easement, a
  entitlement that can't be replicated).

**Why reconcile across all three instead of trusting the dominant one
alone?** Each approach has an independent, non-overlapping error source:
cost approach error lives in depreciation/obsolescence estimation
(subjective); sales-comparison error lives in adjusting for
non-identical comparables (subjective); income-approach error lives in cap
rate / discount rate selection and pro-forma durability (highly sensitive
to a single assumed number). These are close to independent noisy
estimators of the same underlying quantity, so triangulating across all
three reduces the variance of the final opinion versus trusting any one —
the same logic that makes averaging independent noisy measurements better
than a single reading, just resolved by appraiser judgment rather than a
formal Bayesian weighting, because the error correlations aren't
precisely quantifiable.

**Implication for Hartley Capital-style underwriting:** for income-
producing commercial assets, income approach should carry primary weight;
cost approach is best used as a ceiling / overheating flag; sales
comparison is most useful not as an independent check but as the source of
the cap rate itself (extracting implied cap rates from recent comparable
trades feeds directly back into the income approach's discount rate — the
two approaches aren't really independent in practice, sales comps
calibrate income's key input).

**A prediction the reasoning generates that goes beyond "reconcile the
three":** when a submarket's income-approach value persistently exceeds
its cost-approach value, that's a live build-vs-buy arbitrage — it should
attract new ground-up supply and mean-revert the gap, *unless* there's a
structural barrier (zoning/entitlement scarcity, construction-cost
inflation outrunning rent growth) blocking that arbitrage, in which case
the premium can persist indefinitely. That reframes the cost/income gap as
a leading indicator of new-supply risk in a given submarket, not just a
reconciliation checkbox.

## Corpus answer (searched after the above was written)

Web search on real-estate appraisal doctrine (Pinal County assessor's
office, McKissock Learning, USPAP practice guides, DataMaster, others)
confirms the standard framing essentially matches the derivation above:

- Sales comparison is the most commonly used approach and "works best for
  residential properties with many comparables."
- Cost approach "works best for new construction or special-use
  properties" and is "commonly used for buildings which do not generate
  income, such as government buildings, hospitals, schools, and churches."
- Income approach is "commonly used for commercial properties such as
  condos, office buildings, shopping centers, and apartments, where the
  income generating potential is carefully measured."
- Standard practice is to run as many of the three as data allows, pick
  the most appropriate as the primary method for the situation, and use
  the others to support/cross-check the final value opinion (reconciliation,
  not selection of a single winner).

No source surfaced in this search framed the cost/income gap as a
supply-arbitrage leading indicator — that framing (last paragraph of the
derivation above) doesn't appear to be standard appraisal-doctrine
language, though it's a fairly direct corollary of the doctrine once you
add a market-clearing argument.

## Delta category: **rediscovered**

The core structure (three substitution markets → three approaches;
dominance decided by which market has liquid data; reconciliation weights
all three because their errors are near-independent) was derived
independently from first principles and matches the standard appraisal
doctrine's asset-class guidance almost exactly, including the specific
examples (owner-occupied residential → sales comparison; income
commercial → income approach; special-purpose/non-income → cost
approach).

## Commentary

This is a case where "no retrieval" reasoning gets you the full textbook
answer for free, because the underlying logic (cheapest-substitute
pricing, reconciling near-independent noisy estimators) is genuinely
load-bearing for *why* the doctrine looks the way it does — the doctrine
isn't an arbitrary convention, it's downstream of market-structure facts
that are derivable without having read an appraisal textbook. The one
piece that didn't show up in the corpus search (cost/income gap as a
supply-arbitrage signal) is the kind of thing that's worth carrying into
Hartley Capital's actual underwriting checklist even though it's not
"standard doctrine" — it's a testable, falsifiable extension rather than a
restatement.
