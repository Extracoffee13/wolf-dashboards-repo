# How should a custom sign be priced? (Brand 9 Signs)

Date: 2026-10-14

**Process caveat:** the web search was run BEFORE this derivation was written down (sequencing slip in the automated run). The derivation below uses only first-principles primitives, but it is contaminated by having seen the corpus summary. Treat the delta category as weak evidence.

## Question
From first principles, how should a signage shop set the price of a custom sign?

## First-principles answer
Primitives: a shop is a bounded-capacity machine converting inputs (material, hours of scarce skilled labor, machine time, space) into a product a buyer values. The seller must stay solvent and earn a return; the buyer pays at most their alternative.

1. Price floor = what it costs the shop to *produce and replace* the sign: materials consumed + labor hours x fully loaded labor rate (wage + taxes, insurance, idle/non-billable time) + machine time.
2. Overhead exists whether or not this job is sold (rent, software, owner time, insurance). It must be recovered from billable hours, so it is allocated per billable hour: overhead / expected billable hours. Billable hours, not total hours, are the denominator, so utilization drives the rate.
3. Risk: estimates err, remakes happen, collections slip. Add a contingency proportional to uncertainty (install, outdoor, novel jobs get more).
4. Return: capital and owner risk need a margin above total cost, otherwise the shop only breaks even.
5. Ceiling = buyer's alternative (competitor quote, cost of no sign, value of the lost traffic). Price lives between floor and ceiling; cost-plus sets the floor, value sets where in the gap you land. When capacity is the binding constraint, price by opportunity cost of the hour (what the next-best job would have paid), not average cost.
6. Materials are low-skill pass-through but carry handling, waste and sourcing risk, so they take a markup that differs by material; labor-heavy items should price on hours.

So: P = max(floor, opportunity cost of capacity) up to buyer's ceiling, where floor = (materials x (1+waste/handling)) + burdened hours x shop rate + contingency + margin. Install, permits and travel are separate line items because their cost drivers differ.

## Corpus answer
Sign-industry sources ([Signs of the Times pricing principles](https://signsofthetimes.com/pricing-principles/), [Sign pricing primer](https://signsofthetimes.com/a-sign-pricing-primer/), [Signs101 thread](https://www.signs101.com/threads/how-much-to-charge-per-square-inch.150266/latest), [Beancount job-costing guide](https://beancount.io/blog/2026/07/17/custom-sign-shop-bookkeeping-job-costing-guide)): Material + Labor + Overhead = Total Cost, plus profit (traditionally 20-30% of cost); fully loaded labor runs 30-50% above wage; material markups vary by substrate (claims of ~10x vinyl, 3-4x aluminum/ACM, single-author); rules of thumb (double materials + triple labor, or labor x4-5) for ballparks only; install and permits itemized separately.

## Delta: rediscovered
Cost-build-up structure, burdened labor, overhead per billable hour, separate install lines all match. Not in the corpus summary I saw: explicit opportunity-cost pricing under capacity constraint and the value ceiling (the corpus is cost-plus-centric; some sources may cover value pricing, not checked).

## Commentary
Actionable for B9: track billable-hour utilization, since it sets the overhead rate. Per the claims-truth gate, no figures here are B9 numbers; the markup multiples are unverified third-party claims.
