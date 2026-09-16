# First-Principles Spike — 2026-09-16

## Question

From first principles, why do commercial real estate lenders underwrite a loan
primarily against Debt Service Coverage Ratio (DSCR — net operating income ÷ annual
debt service) rather than Loan-to-Value (LTV — loan amount ÷ appraised value), the
way residential mortgage lending does? And what does that imply about how rising
interest rates actually constrain how much a lender will write, before appraised
values even move?

(Self-generated — backlog was empty. Chosen for direct relevance to Hartley Capital
deal underwriting; not yet covered by prior spikes, which have touched cap rates and
NNN leases but not the loan-sizing mechanics that sit upstream of them.)

## First-principles answer (derived before any search)

Start from what a loan actually is: a promise to repay principal and interest, and a
lender's risk is (probability of default) × (loss given default). Two structurally
different things can make a loan safe: the borrower's ability to keep paying
(a *flow* property), and the collateral's ability to make the lender whole if they
stop (a *stock* property). LTV measures the second. DSCR measures the first. The
question of which one to lean on is really: which failure mode is more likely, and
which number is more trustworthy, for this asset class?

**Where does repayment actually come from?** For a residential mortgage, repayment
comes from the borrower's personal income — a salary, external to the house itself.
The house does not generate cash; it's a consumption/shelter asset. So there is no
natural "coverage ratio" to compute from the asset alone; the lender's real
flow-risk variable is the borrower's personal debt-to-income, and the asset's own
contribution to risk is purely recovery-side — hence LTV (with mortgage insurance
stepping in at high LTV) is the dominant lever.

For commercial real estate, the loan is usually held in a single-purpose entity that
owns only this property, often non-recourse to any other income of the sponsor. There
is no external salary to fall back on. The *only* repayment source is the property's
own operating income — rents in, expenses out. That makes NOI-vs-debt-service the
literal, not metaphorical, question of whether this loan gets paid. DSCR isn't one
proxy among several here; it's the direct measurement of the repayment mechanism.

**Why is LTV specifically untrustworthy for commercial, beyond just "there's a better
number"?** Because commercial appraised value is not an independent signal the way a
home's comp-based appraisal is. Commercial value is computed as `Value = NOI / Cap
Rate` — it is *itself derived from* the same income stream DSCR measures, deflated by
a cap rate that floats with interest-rate sentiment and market mood. So LTV, in
commercial real estate, is a ratio of (loan amount) to (a number partly re-derived
from macro sentiment), not a ratio to a physically stable replacement cost. That
makes LTV a moving, somewhat circular target — a cap-rate compression in a hot market
can make a marginal deal look over-collateralized without the underlying cash flow
having improved at all. NOI, by contrast, is closer to an audited, contracted,
recurring number (signed leases, rent rolls) and much harder to move with sentiment.
A lender who wants to underwrite the *real* asset, not the *market's current mood
about* the asset, should anchor on the flow number and treat the value-based number
as secondary.

**Prediction: DSCR and LTV bind in different rate regimes.** Debt service is
`principal × rate` (via the amortizing payment formula) — it rises mechanically with
interest rates for a fixed loan amount. DSCR = NOI / debt service therefore falls as
rates rise, holding NOI and loan amount fixed. Appraised value also falls as rates
rise (cap rates widen), but more slowly and with a lag, since cap-rate re-pricing is
a market/comp process, not an arithmetic one. So immediately after a rate increase,
DSCR degrades *mechanically and instantly* while LTV degrades *later and more
noisily*. This predicts a regime split: in low-rate environments, the DSCR floor has
slack and the LTV cap is what actually limits proceeds ("leverage-constrained"); as
rates rise, DSCR degrades faster than appraised value falls, so the DSCR floor
becomes the binding constraint first and lenders shrink loan proceeds on the *same*
property at the *same* appraised value purely because debt service on that principal
is now more expensive ("debt-service-constrained"). A borrower refinancing in a
higher-rate environment can get less money for an unchanged, even improving, asset —
not because the collateral is worth less (yet) but because the coupon on the same
principal now eats more of the same cash flow.

**A second-order prediction.** DSCR itself is gameable by loan structure: a lender
could quote a large loan and simply stretch amortization (e.g. 40 years instead of
25) to shrink the annual debt-service payment and pass a DSCR floor without the
underlying loan being any safer in an absolute-dollar sense. A lender who wants a
number immune to that trick would want something that ignores rate and amortization
entirely and measures raw income against raw principal — i.e., `NOI / Loan Amount`
— as a backstop metric independent of how the note is structured. I'd predict such a
metric exists and is used specifically by lenders most exposed to structuring abuse.

## Corpus answer

Search on commercial lending underwriting practice (commercialrealestate.loans,
CREFCOA, Wall Street Prep, Altus Group, PropertyMetrics, 2025–2026) confirms the
structure almost exactly:

- DSCR = NOI ÷ annual debt service; LTV = loan amount ÷ appraised value. Typical
  standards: DSCR minimum ~1.20–1.25x, LTV cap ~65–75%.
- "When the maximum LTV is reached but DSCR requirements aren't met, the loan amount
  will be reduced until the minimum DSCR is obtained... in commercial underwriting
  this is referred to as loan dollars being **debt service constrained, not
  leverage (LTV) constrained**" — this is the exact regime-split predicted above,
  using the same terminology independently arrived at.
- On the gaming prediction: **debt yield** (NOI ÷ loan amount) exists precisely for
  this reason. "Debt yield is based on the loan amount, and thus won't change with
  interest rates or amortization schedules… the debt service coverage ratio changes
  when rates move, amortization schedules shift, or interest-only periods are
  applied." The corpus explicitly attributes its adoption to CMBS lenders after the
  2008 crisis, as a structural backstop against exactly the amortization-stretching
  abuse predicted — a causal detail (the 2008 CMBS origin) the first-principles pass
  didn't have and couldn't have derived, only anticipated the shape of the fix.

## Delta category: **rediscovered**

The reasoning independently reconstructed (a) why commercial lending anchors on
DSCR rather than LTV (no external income source; the asset *is* the repayment
mechanism), (b) the circularity that makes LTV a soft, sentiment-linked number in
commercial real estate specifically, (c) the "debt-service-constrained vs.
leverage-constrained" regime split as rates move — matched almost verbatim in
industry terminology, and (d) the existence and purpose of debt yield as an
amortization-proof backstop metric, before knowing the term existed.

## Commentary

The strongest signal here isn't that the headline answer matched (DSCR primacy is
well-known) — it's that the *derived* backstop metric (predicted from "DSCR is
gameable via amortization, so something loan-amount-only should exist") turned out
to be a real, named, industry-standard ratio (debt yield) with a specific documented
origin story (CMBS, post-2008) that the reasoning had no way to know. That's a
higher bar than matching a well-known headline fact: it's predicting the *existence*
of an unnamed tool from the structural weakness of the tool it would need to patch.
The corpus adds one thing reasoning alone couldn't reach — the historical/regulatory
trigger (2008 CMBS losses) for why debt yield became standard specifically for CMBS
lenders and not yet banks/life companies/agency lenders, i.e., *who* adopted the fix
tracks *who* got burned, not just who could compute it. Useful going forward: when a
first-principles pass predicts "a tool like X should exist to patch weakness Y,"
that's a good moment to search for the tool by its function rather than its name —
it's a higher-value check than re-deriving something already common knowledge.
