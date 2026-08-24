# First-Principles Spike — 2026-08-24

## Question

Why should a tax-loss-harvesting engine's wash-sale re-entry window be
symmetric around the sale date, and what length is economically justified?

(Picked because `tax_report.json` in this repo carries a live
`wash_sale_blocklist` for the WOLF/Hartley Capital book — this is not an
academic question, it's a parameter the trading system actually enforces.)

## First-principles answer (no retrieval)

Start from the asymmetry a tax code creates: gains and losses are only
taxed/deducted when *realized*, not when they merely exist on paper. That
asymmetry is exploitable. If an investor can sell a losing position, claim
the deduction, and immediately reconstitute the identical economic
position, they have manufactured a tax benefit with zero economic cost —
the "loss" was never a real change in exposure, only a paperwork event. A
tax authority that wants deductions to track real economic loss-bearing has
to close this off.

So the design problem is: what rule distinguishes "genuinely gave up the
position" from "briefly closed my eyes and reopened it"? Two knobs are
available — *scope* (which repurchases count as "the same position") and
*time* (how long the investor must stay out).

**Why time, not just scope.** Even a rule that only blocks repurchasing the
literal same security doesn't help unless it's paired with a window,
because without one, "sell then immediately rebuy the same ticker" is still
free — the price barely moves in the time it takes to place two orders.
The rule needs a duration long enough that reentry carries genuine price
risk, so the investor is making a real bet, not a costless swap.

**How long is "genuine risk"?** Individual equities commonly run 20–40%
annualized volatility. Price dispersion scales roughly with the square root
of elapsed time, so over N trading days the expected move is roughly
σ_annual × sqrt(N/252). A single day (sqrt(1/252) ≈ 0.06) gives a trivial
~1–2% expected move — not enough deterrent. A window an order of magnitude
longer, on the order of a month (sqrt(21/252) ≈ 0.29, i.e. ~30% of a full
year's move, so several percent expected dispersion) starts to look like a
real bet: the investor risks the stock running away from them before they
can get back in. Going much longer (a quarter or more) stops adding much
deterrence — variance grows sub-linearly on that scale relative to the
opportunity cost imposed — while materially damaging a legitimate
rebalancer's ability to manage a book. So the efficient window, balancing
deterrence against unnecessary restriction, lands in the "few weeks to
about a month" range, not days and not a year.

**Why symmetric (before *and* after).** A rule that only looks forward
("don't rebuy within N days after the loss sale") is trivially routed
around: buy the replacement shares *first*, then sell the original lot for
the loss, netting the same reconstituted position without ever violating a
forward-only rule. To close that hole, the block has to run backward from
the sale date too — you can't have acquired the position shortly before
the loss sale either. So symmetry isn't an aesthetic choice, it's forced by
the fact that "acquire-then-sell" and "sell-then-acquire" are
economically identical maneuvers; a rule blocking only one direction just
relabels the loophole.

**Total window.** If genuine risk requires roughly a month on each side,
and the rule must be symmetric to prevent the pre-positioning workaround,
the natural design is: block reacquisition from about 30 days before the
sale through about 30 days after it — a single continuous window spanning
roughly two months, inclusive of the sale date itself.

**Scope ("what counts as the same position").** A bright-line rule
("literal same CUSIP only") is easy to administer but trivially gamed by
swapping into a near-perfect substitute (e.g., one broad-market ETF for
another with near-identical holdings) — same economic exposure, technically
different security. A looser standard ("substantially similar economic
exposure") closes that gap but is inherently fuzzy and costly to enforce
uniformly. There's no clean first-principles answer here beyond a
tradeoff: administrability pushes toward a bright line; effectiveness
pushes toward a fuzzy standard. A workable middle ground is a
qualitative "substantially identical" test applied case-by-case rather
than a precise formula — accepting that some correlated-substitute
harvesting will remain a legal gray zone.

**Prediction going in:** a symmetric ~30-day-each-side window (~60 days
total), with a fuzzy "substantially identical" scope test, and disallowance
(rather than permanent forfeiture) of the loss as the penalty mechanism.

## Corpus answer

Confirmed via web search of IRS/broker guidance (Fidelity, Schwab, SEC,
H&R Block, Wikipedia):

- The wash-sale window is **30 days before and 30 days after** the sale
  date, **61 days total** including the sale date — a symmetric window,
  exactly as derived.
- It applies to "substantially identical" stock or securities, including
  options/contracts to acquire them, and even purchases inside an IRA —
  determined by "facts and circumstances," i.e. a fuzzy standard, not a
  bright-line list, as derived.
- The penalty mechanism: the loss isn't destroyed, it's **disallowed and
  added to the cost basis of the replacement shares** — deferred, not
  forfeited. This detail was *not* derived from first principles above;
  the reasoning treated "disallow the deduction" as the endpoint without
  asking what happens to the disallowed loss afterward.

Sources: [SEC — Wash Sales](https://www.sec.gov/answers/wash.htm),
[Fidelity — Wash-Sale Rules](https://www.fidelity.com/learning-center/personal-finance/wash-sales-rules-tax),
[Schwab — Wash-Sale Rule](https://www.schwab.com/learn/story/primer-on-wash-sales)

## Delta category: **rediscovered**

The window length (30/30, symmetric, ~61 days), the reason for symmetry
(closing the pre-position loophole), and the fuzzy "substantially
identical" scope standard were all arrived at independently through pure
reasoning about deterrence economics and loophole-closure, before any
search — and they matched the actual IRS rule closely enough that this
counts as a genuine rediscovery, not a coincidence dressed up after the
fact.

One real gap: the *basis-carryforward* mechanism (disallowed loss rolls
into the replacement lot's cost basis rather than vanishing) wasn't
predicted. That's a specific implementation choice — arguably itself
derivable from a "the tax code shouldn't destroy real economic loss
information, only defer its recognition" principle — but the reasoning
above stopped one level short of asking that question. Worth noting for
`tax_report.json`'s `tax_loss_harvest_candidates` logic: any harvested lot
that trips the blocklist should carry its disallowed loss forward onto the
new lot's basis, not discard it.

## Confidence

0.75 — the core numeric/structural result matched the corpus cleanly; the
one miss (basis carryforward) is a real, identified gap rather than a
vague hedge.
