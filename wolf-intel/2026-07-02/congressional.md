# WOLF Congressional Trading Watch — 2026-07-02

Scan window: last 24h (2026-07-01 00:00 → 2026-07-02, as run)

## ⚠️ Data access limitation (read first)

This run could not directly query the primary sources. Every outbound fetch to
`efdsearch.senate.gov`, `disclosures-clerk.house.gov`, `capitoltrades.com`,
`quiverquant.com`, and `unusualwhales.com` returned `403 Forbidden` — both at
the WebFetch tool layer and at the sandbox's own egress proxy (which reported
"destination host is not allowed by your organization's egress policy for
this session" for every external host tested, including control domains like
`en.wikipedia.org`). This is an infrastructure/network-policy block in this
execution environment, not a signal about trading activity, and per the
proxy's own guidance it should be reported rather than routed around.

Net effect: **no full table scan of last-24h PTR filings was possible this
run.** What follows is the best-effort intelligence recoverable through
indexed web search (snippets only, no page fetch), cross-checked across
multiple independent outlets. Nothing below is fabricated; anything not
independently confirmed by search is flagged as such. Treat this as a
degraded-mode report — recommend restoring allowlisted access to the above
five domains (or a paid API key for Quiver/CapitolTrades) before the next run.

---

## Most recent confirmed congressional trades found (outside strict 24h window)

No PTR was confirmed as *newly filed* within the last 24 hours. The two most
recent confirmed filings surfaced by search are both slightly outside the
24h window but are the freshest verifiable data point as of this run:

| Member | Chamber | Party | Ticker | Type | Trade Date | Filed Date | Days to Disclose | Size Bucket | Score |
|---|---|---|---|---|---|---|---|---|---|
| Nancy Pelosi | House (CA-11) | D | INTC | Buy (200 calls, $50 strike, exp 3/19/27) | 2026-05-29 | 2026-06-23 | 25 | 1M–5M | 5 |
| Nancy Pelosi | House (CA-11) | D | UBER | Buy (200 calls, $50 strike, exp 3/19/27) | 2026-05-29 | 2026-06-23 | 25 | 500k–1M | 5 |
| Mitch McConnell (spouse) | Senate (KY) | R | UBS Group AG | Buy | 2026-06-02 | 2026-06-30 | 28 | 100k–250k | 2 |

**Scoring rationale:**
- Pelosi INTC/UBER — Score 5: textbook known-track-record member, large size, highly liquid names, first disclosed activity since January 2026 (multiple outlets flagged the timing vs. Intel's recent rally). Both compliant (25 days, under the 45-day STOCK Act ceiling).
- McConnell/UBS — Score 2: notable name but standalone trade, moderate size, foreign bank stock with no obvious committee nexus for McConnell. Compliant (28 days).

No homebuilder tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC) appeared in any confirmed filing found this run. No Brand 9 client-ticker match could be evaluated — **this repo has no committed Brand 9 client ticker roster**; recommend adding one (e.g. `wolf-intel/config/brand9-tickers.json`) so this flag can run automatically in future scans.

---

## STOCK Act drift — background context (not newly filed this run)

These are documented 2026 STOCK Act violation/lateness cases active in the
current news cycle. None are confirmed as newly disclosed in the last 24h —
listed here as standing drift risk to watch, per multiple independent outlets
(NOTUS, Forbes, Yahoo Finance, Star Tribune):

| Member | Chamber | Party | Issue | Magnitude |
|---|---|---|---|---|
| Julia Letlow | House (LA-5) | R | 210+ trades disclosed late, some >1 year late | $225k–$3.3M aggregate |
| Kelly Morrison | House (MN-3) | D | Months-late disclosure | 7-figure aggregate |
| Jim Jordan (spouse) | House (OH-4) | R | ~1 month late on Central Bancshares sale | up to $100k |
| Ed Case | House (HI-1) | D | Late-filed trades | not specified |
| Rich McCormick | House (GA-6) | R | Late-filed trades | not specified |
| Linda Sanchez | House (CA-38) | D | Late-filed trades (notable: stock-ban advocate) | not specified |
| John Hickenlooper | Senate (CO) | D | Late disclosure re: Palantir | not specified |
| Mike Rounds | Senate (SD) | R | Late disclosure re: Palantir | not specified |

Broader context: reporting indicates "more than two dozen federal lawmakers"
have been flagged for STOCK Act lateness since mid-2026, and a bipartisan
"Restore Trust in Congress Act" (Gillibrand/Moody) proposing a full trading
ban for members, spouses, and dependents remains pending.

---

## What a full scan would normally cover

Once source access is restored, this report is structured to run the full
pipeline: Senate eFD + House CHDP raw PTR pull → ticker/size/date extraction
→ cross-reference against Quiver/CapitolTrades for corroboration → same
scoring rubric (1–5) and homebuilder/Brand-9 auto-bump rules → STOCK Act
45-day drift check on every row, not just known news cases.

## Recommendation

Escalate to whoever manages this environment's egress allowlist: add
`efdsearch.senate.gov`, `disclosures-clerk.house.gov`, `capitoltrades.com`,
`quiverquant.com`, and `unusualwhales.com` (or provision an API key for one
of the aggregators) so future WOLF congressional runs get first-party data
instead of search-snippet triangulation.
