# WOLF Congressional Trading Watch — 2026-08-27

## Data access notice (read first)

This scan **could not reach any of the specified primary or aggregator sources** —
Senate eFD (efdsearch.senate.gov / disclosure.senate.gov), House CHDP
(clerk.house.gov/PublicDisclosure), Quiver Quantitative, CapitolTrades,
Unusual Whales, and every alternate aggregator tried (congressstock.com,
insidertradingtracker.co, trendlyne.com, benzinga.com) — all returned
`EGRESS_BLOCKED` from this environment's network egress proxy. Direct
page-fetch tools are not permitted to reach these domains in this session.

The only channel that worked was indexed web search (snippet-level, no live
page access), which cannot enumerate a complete last-24h filing list and
cannot independently confirm exact PTR filing dates, disclosed size ranges
beyond what's quoted in secondary coverage, or committee assignments. What
follows is **not a comprehensive scan** — it is the one filing that surfaced
across multiple corroborating news sources during the search, presented with
its sourcing caveats. No filing data has been invented to fill out the
requested format.

**Recommendation:** if a comprehensive daily scan is required going forward,
this environment's egress policy needs an allowlist entry for
efdsearch.senate.gov / disclosure.senate.gov, clerk.house.gov, and/or the
aggregator APIs (Quiver/CapitolTrades offer paid API access that may route
differently than the browser-facing domains that were blocked here).

---

## Filings found (partial, search-corroborated only)

### 1. Rep. Nancy Pelosi (D) — House — Bloom Energy (NYSE: BE)

- **Transaction type:** Buy — common stock (~15,000 Class A shares across two
  lots) plus 200 call options, $100 strike, exp. 2027-06-17
- **Transaction dates:** 2026-07-24 and 2026-07-28 (household account)
- **Reported size bucket:** $1M–$5M (multiple outlets cite an aggregate
  ~$4.25M–$14.5M range across the combined equity + options filing;
  treat the upper bound as unconfirmed — PTR ranges are disclosed as
  brackets, not exact amounts, and this session could not pull the
  underlying PTR image to confirm the exact bracket)
- **Filing/disclosure date:** secondary sources place disclosure between
  2026-08-21 and 2026-08-24 (not independently confirmed against the
  primary eFD record — access blocked)
- **Days between transaction and disclosure:** approx. 24–31 days
  (within the 45-day STOCK Act window — **not** a late filing, based on
  available dates)
- **Also disclosed in the same filing window:** an addition to an existing
  Intel (INTC) position, per the same coverage
- **Score: 5** — known-track-record member, large size, liquid/high-profile
  names (BE, INTC)
- **Sourcing:** multiple independent outlets (Yahoo Finance, Seeking Alpha,
  24/7 Wall St, The Globe and Mail, Benzinga headline text) reported this
  consistently; none of them were directly fetchable in this session, so
  this entry rests on search-engine snippet summaries of those articles,
  not on the primary disclosure document.

---

## Special flags

- **Homebuilder tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
  MHO, TMHC):** No new filing touching any of these tickers was identified
  in the accessible window. Background context only: DHI has a long history
  of congressional trading activity (94 disclosed trades across 6 members
  in 2026 per one aggregator's cumulative count), but nothing dated to this
  scan window surfaced.
- **Brand 9 client tickers:** No client-ticker list exists in this repo to
  check against, so this rule could not be applied. If there's a canonical
  list elsewhere, point this task at it and it can be checked directly next
  run.
- **STOCK Act drift (>45 days late):** None identified — the only filing
  found in this session's search was within the 45-day window per available
  reporting.

## Bottom line

Real access to the required sources was blocked end-to-end today. The one
filing surfaced (Pelosi / BE + INTC) is a real, well-covered event, but this
file should not be read as a complete daily congressional trading sweep.
