# WOLF Congressional Trading Watch — 2026-08-20

**Scan window:** last 24h (2026-08-19 → 2026-08-20)
**Status: DATA ACCESS BLOCKED — no verified filings for this window.**

## What happened

This run could not reach any of the primary or aggregator sources requested in the task spec. Every direct fetch was rejected by the session's egress policy before any page content was returned:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov | `EGRESS_BLOCKED` — host not on session allowlist |
| House CHDP | clerk.house.gov/PublicDisclosure | `EGRESS_BLOCKED` — host not on session allowlist |
| Quiver Quantitative | quiverquant.com/congresstrading | `EGRESS_BLOCKED` — host not on session allowlist |
| CapitolTrades | capitoltrades.com | `EGRESS_BLOCKED` — host not on session allowlist |
| Unusual Whales | (not attempted — same proxy policy applies to unlisted financial-data hosts) | N/A |

Per the proxy's own diagnostic guidance, a blocked host is an organization egress-policy denial, not a transient failure — retrying or routing around it is not appropriate.

As a fallback, general web search (which does not go through the blocked egress path) was run against several queries (site-specific and ticker-specific, including the homebuilder basket). It surfaces only aggregate/historical summaries and platform landing pages — e.g. a mention of Sen. John Boozman trades from **late July 2026** (CVE, JPM, TRV, HD) and a note that DHI has "94 disclosed trades" across 6 members with no date breakdown. Nothing in the search results is dated or granular enough to responsibly attribute a specific ticker/size/date transaction to a specific named member as a *filing made in the last 24 hours*. Publishing invented member-level trade records under real names would be worse than publishing nothing.

**No filings are scored below because none could be verified for this window.**

## STOCK Act drift (>45 days)

No data — same access blocker.

## Special flags status

- Homebuilder basket (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC): no verified activity in window.
- Brand 9 client tickers: no verified activity in window.

## Recommended fix

To make this a real daily feed, the session's egress allowlist needs one of:
- `efdsearch.senate.gov` + `clerk.house.gov` (primary sources, most authoritative but require session/query handling), or
- `capitoltrades.com` and/or `quiverquant.com` (aggregators, easier to parse) added to the network policy for this environment.

Until one of those is allowlisted, this task can only run on search-engine snippets, which are not reliable enough for named, dated, sized trade attribution.
