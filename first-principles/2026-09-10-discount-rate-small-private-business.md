# First-Principles Spike — 2026-09-10

## Question

What discount rate should actually be used to value a small, founder-operated
business (e.g. a signage fabrication shop like Brand 9 Signs, or a target for
Hartley Capital) when there is no public equity, no observable beta, and the
owner/buyer is undiversified with respect to the investment? Is CAPM/WACC
even the right tool, and if not, what replaces it?

## First-principles answer (derived before any search)

Start from the bedrock: a discount rate exists because a dollar promised
later is worth less than a dollar in hand now, for three separable reasons —
(1) pure time preference / opportunity cost (money now can be put to other
use), (2) expected inflation eroding purchasing power, and (3) uncertainty
that the promised dollar arrives at all or arrives at the size promised. A
discount rate is just the exchange rate between a *certain* dollar today and
an *uncertain* dollar at some future date, and it should be exactly as large
as the compensation a rational capital-holder requires to accept that
uncertainty — no more, no less.

CAPM is one specific theory of how to price that uncertainty. Its move is to
say: an investor holding a large, diversified portfolio can eliminate
firm-specific (idiosyncratic) risk for free, just by holding many
uncorrelated assets — the ups and downs average out. What survives
diversification is only the portion of a stock's variance that moves with
the whole market (systematic risk, measured by beta). Since idiosyncratic
risk is "free" to eliminate, a diversified market won't pay you extra return
for bearing it — only systematic risk gets priced. WACC then just blends
CAPM's cost of equity with the after-tax cost of debt, weighted by a stable
target capital structure, assuming the firm can tap public-ish capital
markets at going rates.

Now test whether the premises hold for a small, founder-operated signage
shop being valued for acquisition:

1. **No price series, so no beta.** Beta is literally a regression
   coefficient of observed returns against market returns. A private
   company generates no daily price, so there is nothing to regress. Any
   beta used has to be borrowed from public comparables — and there are
   almost no pure-play public signage fabricators, so the borrowed beta is a
   noisy proxy from an adjacent industry (building products, commercial
   printing) with a different scale, product mix, and leverage. Re-levering
   it for the target's capital structure adds another layer of approximation
   on top of an already-mismatched proxy. The tool's core input is
   fabricated, not measured.

2. **The buyer is not diversified.** CAPM's whole justification for
   ignoring idiosyncratic risk depends on the buyer holding it as one
   sliver of a large portfolio. But the actual capital-holder here — a
   founder-operator, or a control-buying firm like Hartley Capital taking a
   concentrated position — is *not* diversified with respect to this asset.
   It may be the largest single position in their book, illiquid, and
   unhedgeable: they cannot sell 2% of their stake next week if a customer
   walks. If the premise ("the marginal investor is diversified") is false
   for the actual buyer, the conclusion ("only systematic risk is priced")
   doesn't transfer. Idiosyncratic risk — one key customer, one key
   fabricator/welder whose departure stalls production, a landlord who
   doesn't renew a shop lease — is real, undiversifiable *to this buyer*,
   and therefore has to be priced somehow, even though textbook CAPM says
   to throw it away.

3. **WACC's capital-structure and market-access assumptions don't hold
   either.** A small operator's financing is lumpy and personal —
   SBA loans, personally guaranteed bank lines, seller notes — not a stable,
   market-priced blend of public debt and equity. Treating that as a
   "market" cost of debt overstates precision.

So the CAPM/WACC machinery is being asked to answer a question whose
premises it was not built for. What has to replace it, reasoned from the
same first principle (compensate exactly for the uncertainty actually
borne, by the party actually bearing it), is a rate built by *addition*
rather than by *regression*: start from the same risk-free rate (opportunity
cost of doing nothing), add a broad equity risk premium (compensation for
holding business risk generally, since some of the shop's risk clearly does
correlate with the economy — a recession hits sign orders too), then add
explicit, itemized premiums for the risks that a diversified-market rate
would have thrown away but this buyer cannot: a size/illiquidity premium
(small, unsellable stakes empirically demand higher promised returns), and a
company-specific premium for the concrete idiosyncratic exposures — customer
concentration, key-person dependence, weak financial controls/no audited
statements. Each premium should be independently defensible, not a single
fudge factor.

One more consequence follows from principle (3), risk correctly priced once:
if the *cash-flow forecast* already downgrades for a risk — say, you
probability-weight revenue for a 20% chance the biggest customer leaves next
year — then adding a *full* customer-concentration premium to the discount
rate on top of that double-counts the same risk twice, once in the
numerator and again in the denominator, and systematically undervalues the
business. Risk should be priced in the cash flows or in the rate, not
redundantly in both for the same specific event.

Separately, if the question is really "what hurdle rate should Hartley
Capital use to decide whether to allocate capital here," that's a different
first-principles frame entirely: the right rate is the opportunity cost of
Hartley's *next-best alternative use of the same capital*, not an
entity-specific risk-return estimate for the target in isolation.

## Corpus answer

Standard valuation practice for private/closely-held companies confirms
almost exactly this reasoning. It's called the **build-up method**: start
from the risk-free rate, add the equity risk premium, then stack additional,
independently documented premiums (size premium — commonly sourced from
Duff & Phelps/Ibbotson data — industry risk, and a company-specific risk
premium), because CAPM's beta is unreliable or unobservable for private
firms with no share price, forcing appraisers to borrow beta from
imperfect public comparables. The literature explicitly frames this as
CAPM-augmented-with-risk-premiums versus build-up-from-observable-premiums,
and treats build-up as the standard, defensible choice for small private
companies precisely because each component is separately sourced from
published market data rather than a fabricated single beta.

The undiversified-investor point is also directly addressed in the
valuation literature via Damodaran's concept of **"total beta"** — beta
divided by the correlation of the stock with the market, used to capture
total risk (systematic + firm-specific) rather than just market risk, for
an owner who cannot diversify away. Damodaran himself has cautioned that
this is a theoretical extreme ("you never have that kind of buyer in the
real world") and that real private-company investors sit somewhere between
fully diversified and fully undiversified — a refinement more precise than
the binary framing in my own derivation.

I did not find a source explicitly confirming/denying the double-counting
point (pricing the same specific risk in both the cash-flow forecast and
the discount-rate premium) in this pass, though it is consistent with the
general valuation principle that risk should be reflected once, not twice.

## Delta category: **rediscovered**

## Commentary

Independently arrived at the standard answer: reject CAPM/WACC for a small
private target because its core premises (observable beta, a diversified
marginal investor, market-priced capital structure) don't hold, and replace
it with an additively-built rate stacking risk-free + equity premium + size
+ company-specific premiums — which is exactly the textbook "build-up
method." Also independently derived the undiversified-investor argument for
why idiosyncratic risk must be priced here, which converges with Damodaran's
"total beta" concept, though the corpus's treatment is more nuanced (a
spectrum of diversification, not a binary) than my framing. The
double-counting-risk observation and the "hurdle rate = opportunity cost of
the allocator's next-best alternative" reframing weren't directly
contradicted or confirmed by the search pass — worth a follow-up spike
specifically on whether/how professional appraisers guard against
double-counting risk between cash-flow haircuts and discount-rate premiums.
