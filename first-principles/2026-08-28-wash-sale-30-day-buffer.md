# First-Principles Spike — 2026-08-28

## Question

The WOLF Construct's tax-loss-harvesting logic (`tax_report.json`) maintains
a `wash_sale_blocklist` keyed by ticker → date. Is a 30-calendar-day
repurchase blackout the correct first-principles buffer for a systematic
tax-loss-harvesting agent to avoid IRS wash-sale disallowance, and why 30
days specifically rather than 15 or 45? What exactly should the agent be
blocking?

*(No prior backlog file existed; this question was generated from the
repo's own artifacts — it directly governs correctness of code already
running in this Construct.)*

## First-Principles Derivation (no retrieval)

**1. What problem is the rule solving?** Tax law lets a realized capital
loss offset gains/income. Without a guardrail, an investor could sell a
losing position on Dec 31 purely to recognize the loss, then immediately
rebuy the identical exposure on Jan 1 — economically unchanged, but with a
manufactured tax deduction. This is an arbitrage between *accounting
recognition* (a sale triggers a taxable event) and *economic reality* (the
investor never actually left the position). Any tax authority that allows
loss deductions must close this gap or the deduction becomes nearly free
money for anyone holding volatile assets.

**2. What's the right proxy for "economic reality didn't change"?** You
can't directly audit intent, so you need an observable proxy. The two
candidates are (a) time out of the position, or (b) substitution into a
different-but-similar instrument. Time-out-of-market is the enforceable
one: it forces the investor to bear real, unhedged price risk for a stretch
of time. If price is a random walk with nonzero variance, "reinvest after N
days" only manufactures a free tax loss if N is small enough that the
expected adverse move during the gap is negligible relative to the
harvested loss. So the rule *has* to be time-based to be auditable, and N
has to be large enough that market risk during the gap is real, not
cosmetic.

**3. Why symmetric before *and* after the sale?** A investor could
equally engineer the same economic-null trade by buying a hedge or the
replacement position *before* selling the loss leg (e.g., buy 100 more
shares, then sell the original 100-share lot at a loss — net position
unchanged the whole time, loss still harvested). Any window that only
blocks *after* the sale is trivially circumvented this way. So symmetry
(block both directions around the sale date) is a structural requirement
of the proxy, not a policy add-on — this follows deductively from step 2
once you allow buy-then-sell as well as sell-then-buy.

**4. Why 30 days and not 15 or 45?** This part is *not* derivable from pure
mechanism design — it's a calibration/administrability choice, and I flag
it as such rather than pretending to derive a number from nothing. What can
be reasoned about is the shape of the trade-off: too short (e.g. 15 days)
and the "real risk" the investor bears during the blackout is small for
most liquid names, cheapening the guardrail; too long (e.g. 90 days) and it
starts blocking legitimate portfolio rebalancing that has nothing to do
with tax engineering, which would conflict with the law's intent to still
*permit* loss harvesting, just not a costless round-trip. A monthly-scale
window (~1/12 of a year) is a natural administrability unit: it's long
enough that a full statement cycle passes, easy to compute off a calendar
without reference to any per-security volatility model, and short enough
that "wait a month, then re-enter if you still like it" remains a livable
strategy. My prediction, before checking, is that 30 was chosen as a round,
volatility-agnostic calendar unit for enforceability — not tuned per-asset.

**5. What must the agent actually track?** Given (2) and (3), correctness
requires: for every realized loss lot, block repurchase of the *same
security* from 30 days before its buy date... no — from 30 days before the
**sale** date through 30 days after the **sale** date (61-day window
total), not just "30 days after the sale" as a forward-looking blocklist
alone would encode. A blocklist populated only at time-of-sale, looking
forward, silently fails to catch the case where the replacement purchase
happened *before* the loss sale (step 3). Also, "same ticker" is a
necessary but possibly insufficient proxy for "substantially identical
security" — the real test plausibly extends to options/derivatives on the
same underlying, and I'd guess it does *not* extend to a different ETF
tracking a similar-but-not-identical index (since "identical" should mean
identical, not merely correlated — otherwise the rule would be
unenforceable, since most liquid securities are highly correlated with
something).

**6. Prediction summary (pre-corpus):** 61-day symmetric window (30 before
+ 30 after) around the sale date; same-security (and likely same-underlying
derivatives) count as "substantially identical"; a different but correlated
security does not; the disallowed loss is probably not permanently
destroyed but deferred somehow (added to the cost basis of the replacement
lot), because permanently destroying it would double-penalize an investor
who genuinely changes their mind and doesn't touch the position again for
years — deferral is the more coherent design once you assume the rule's
goal is to stop *costless* round-trips, not to punish re-entry per se.

## Corpus Answer (web search, IRC §1091 and standard broker/CPA summaries)

- The window is exactly 61 calendar days: 30 days before the loss sale, the
  sale date itself, and 30 days after — confirmed symmetric.
- "Substantially identical" covers the same stock/security, including
  acquiring a contract or option to buy substantially identical securities;
  a different company or a fund tracking a different index is generally
  not covered.
- The disallowed loss is not lost — it is added to the cost basis of the
  replacement shares, deferring rather than destroying the tax benefit
  (except when the replacement is bought inside an IRA, where it's
  destroyed with no basis step-up — a wrinkle I did not derive and would
  not have predicted from mechanism design alone).
- Attribution rule: a purchase by a spouse or by a corporation you control
  can also trigger the rule on your sale — I did not derive this at all;
  it's a corpus detail closing an entity-shifting loophole my reasoning
  didn't consider.
- The corpus does not explain *why* 30 (vs. 15/45/60) was chosen — it's a
  statutory number (IRC §1091, dating to 1921-era predecessor rules) with
  no first-principles derivation available even in the source material;
  administrability is the standard explanation given informally by
  practitioners, matching my step 4 guess but unverifiable as "the" reason.

## Delta

**Category: rediscovered**, with one flagged gap and one open item.

- **Rediscovered cleanly:** the 61-day symmetric window, the reason for
  symmetry (block pre-buying the replacement, not just post-buying it),
  the "same security" scope of substantially identical, and the deferred
  (basis step-up) rather than destroyed treatment of the loss.
- **Gap I didn't derive:** the IRA basis-destruction wrinkle and the
  spouse/controlled-entity attribution rule. Both are patches for
  loopholes at the *edges* of the mechanism, not part of its core logic —
  which is exactly the kind of detail pure reasoning misses and only
  retrieval catches, because it requires knowing what people actually tried
  to get away with historically, not just what the mechanism implies.
- **Still open / unverifiable:** why 30 days exactly. My administrability
  argument is plausible but the corpus doesn't confirm or deny it — this
  stays a hypothesis, not a rediscovered fact.

## Commentary

The reasoning chain got the *mechanism* right by treating the rule as a
proxy for "did the economic position actually change," and correctly
predicted symmetry and basis-deferral as *structural* consequences of that
framing rather than arbitrary policy choices. What it missed — the IRA
wrinkle, the attribution rule — are anti-abuse patches layered on after
people found the first version's loopholes. That's a fairly durable
distinction: first-principles reasoning is strong at recovering *why a
rule's core shape has to be what it is*, and weak at recovering the
*patches bolted on in response to specific historical gaming*, since those
require knowing what happened, not just what's logically implied.

Practically for this Construct: `wash_sale_blocklist` should be checked as
a symmetric ±30-day window around each realized-loss sale date (not just
forward from the sale), and if the agent ever trades options, it needs to
extend "same ticker" matching to derivatives on that ticker too — both are
concrete follow-ups this spike surfaces for the actual code in this repo.
