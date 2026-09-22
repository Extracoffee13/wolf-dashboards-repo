# First-Principles Spike — 2026-09-22

## Question

The WOLF portfolio (`tax_report.json`) actively tracks tax-loss-harvest
candidates and maintains a wash-sale blocklist. That machinery assumes
harvesting losses is worth the operational overhead. So: **does tax-loss
harvesting create real economic value, or is it just deferring a tax bill
to later — i.e., moving numbers around while adding transaction costs and
wash-sale risk for nothing?** This question was self-generated (the backlog
file was empty) because it's directly load-bearing for the WOLF strategy
this repo runs.

## First-principles derivation (no retrieval)

Start from the primitives: capital gains tax is charged on realized gain
(sale price minus cost basis) at the time of sale, at a rate that depends
on holding period — short-term (≤1yr) taxed at the ordinary-income rate
(37% in this portfolio's report), long-term (>1yr) at a lower rate (20%
here). A realized loss offsets realized gains dollar-for-dollar. The wash
sale rule disallows the loss deduction if you buy a "substantially
identical" security within 30 days of the sale — so harvesting requires
rotating into a *similar but not identical* replacement to preserve market
exposure.

**Naive view:** you sell at a loss, deduct it this year, rebuy similar
exposure at the same (lower) price. Your basis in the new lot is now
lower than your original basis would have been. When you eventually sell
the replacement, the gain is larger by exactly the amount you harvested.
Net effect: zero. You've shuffled a tax liability from "now" to "later,"
paid transaction costs, and taken on 30 days of tracking-error risk versus
holding the actual name you sold. Under this view the WOLF harvesting
logic is busywork.

**Where the naive view breaks:** it treats a dollar of tax paid later as
equal to a dollar of tax paid now. It isn't. Time value of money alone
makes pure deferral positive-NPV: take the tax saved today, invest it,
and by the time the deferred liability comes due you've earned a return
on money that was, in effect, an interest-free loan from the government.
So even "just deferral" is not "nothing" — it's a real, if modest, return
that scales with your discount rate and the length of the deferral.

But there's a second, larger effect hiding in the rate structure itself,
and this portfolio's own numbers expose it: the harvested loss is realized
*short-term* (offsetting short-term gains, or ordinary income, taxed at
37%), while the replacement position — if held over a year before it's
finally sold — produces a *long-term* gain taxed at 20%. You are deducting
at the high rate and eventually paying at the low rate. That's not a
timing effect, it's a permanent rate arbitrage of ~17 points on the
harvested amount, independent of how long you defer. This is the real
engine of value, not the interest-free-loan effect.

Third: deferral is not guaranteed to ever come due. Two off-ramps make it
partially or fully permanent rather than deferred: (a) at death, basis
resets to fair market value for heirs (step-up), so a position harvested
and never sold before death has its embedded liability erased entirely —
deferral converts to permanent avoidance; (b) donating the appreciated
replacement position to charity instead of selling it accomplishes the
same erasure while you're alive. Even short of those, if your marginal
rate in the year you finally sell is lower than it is today (retirement,
a low-income year), "later" is cheaper than "now" for reasons beyond time
value — a second, independent arbitrage.

**Costs that must be netted against this:** the wash-sale-forced 30-day
substitution means you don't hold the exact security you sold — if it
rallies sharply in that window (or your substitute underperforms it),
you eat real economic slippage that has nothing to do with taxes.
Transaction costs (spread, any commission) are real, if usually small,
per rotation. There's also process risk: harvesting sloppily and tripping
the wash-sale rule anyway (buying back too soon, or a "substantially
identical" replacement) nets you all the downside — market exposure gap
or none, plus complexity — with the deduction disallowed. This is exactly
why a blocklist file with cool-down dates per ticker exists in this
repo's own portfolio state: the rule's cost is real enough that a
mechanical guard is worth maintaining rather than trusting recall.

**Conclusion from the primitives alone:** tax-loss harvesting is not
"just" deferral — deferral by itself is already worth something under
any positive discount rate — but its more important source of value is
the short-term/long-term rate arbitrage (deduct high, pay back low) plus
the option value of the deferral becoming permanent via step-up-at-death
or charitable gift. Net value = (time-value-of-deferral benefit) +
(expected rate arbitrage from ST-loss/LT-gain character conversion, or
lower future bracket) + (option value of permanent avoidance) −
(tracking-error cost of the forced 30-day substitute) − (transaction and
process-error costs). It's positive in expectation for a taxable account
with meaningful short-term gains or ordinary income to offset, but it is
a real, bounded, mechanical edge — not free money, and not zero.

## Corpus answer (web search, post-derivation)

Michael Kitces' analysis (and the standard robo-advisor literature from
Wealthfront/Betterment) frames it almost identically: "the true benefit
is not the tax savings from harvesting a loss but merely the benefit of
deferring those gains" as a baseline, with harvesting described as
"mostly a tax deferral machine with a genuinely free kicker" — that
kicker being (1) the short-term/long-term rate arbitrage, (2) the ability
to offset up to $3,000/year of ordinary income directly (a detail beyond
pure capital-gains offsetting), and (3) permanent forgiveness for shares
that get a basis step-up at death or are donated to charity. The corpus
also adds a magnitude caveat I didn't derive as sharply: because the
benefit is bounded by the *economic value of deferring* the tax (roughly
a "return on the float"), rather than by the harvested tax amount itself,
the practical impact is often smaller than the sticker-shock 37%-vs-20%
spread implies unless the account has genuinely large short-term losses
or a very high marginal rate.

## Delta category: **rediscovered**

The chain of reasoning arrived independently at the corpus's core
structure: deferral has real but modest time-value benefit; the actual
engine is short-term/long-term rate arbitrage; step-up-at-death and
charitable giving convert deferral into permanent avoidance; wash-sale
substitution is the friction that makes the whole thing not a free
lunch. I missed one concrete mechanic — the $3,000/year direct ordinary-
income offset — and underweighted the corpus's point that the benefit
size is capped by the deferral's time-value, not by the full rate spread.
Both are refinements of magnitude and a missing special case, not
corrections to the reasoning structure.

## Commentary

This validates that the WOLF harvest-candidate + wash-sale-blocklist
machinery in this repo is chasing a real, well-understood edge rather
than a superstition — but also suggests the size of that edge should be
modeled explicitly (discount rate × expected deferral length + rate
spread × probability of eventual LT realization or step-up) rather than
assumed to equal the face-value tax savings shown in `tax_report.json`.
That would be a natural follow-up spike or, more practically, a one-line
addition to the tax report's own math.
