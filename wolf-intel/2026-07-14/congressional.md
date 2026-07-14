# Congressional Trading Watch — 2026-07-14

## Run status: BLOCKED — no verified filing data collected

This scan could not reach any of the required sources. Every outbound fetch
in this session returned `HTTP 403 Forbidden`, including a neutral control
request to `https://example.com` with no financial-data relevance. That
control failure indicates the block is an environment/network-policy
restriction on this session's outbound fetch tool, not site-specific bot
defense on the intel sources themselves.

Sources attempted and their result:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | 403 |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | 403 |
| Quiver Quantitative | quiverquant.com/congresstrading/ | 403 |
| CapitolTrades | capitoltrades.com/trades | 403 |
| Unusual Whales | unusualwhales.com/politics | 403 |
| Control (non-financial) | example.com | 403 |

A general web-search tool (distinct from the fetch tool) remained available
and was used as a fallback. It returned only high-level, dated aggregator
summaries and marketing copy — no queryable, per-filing records (member,
ticker, transaction type, exact size bucket, transaction date, filing date).
None of that summarized content met the bar for a scored filing entry below,
so none is reported as a filing.

**No filings are listed below. This reflects a data-collection failure, not
a finding of zero congressional trading activity in the last 24 hours.**
Treat this run as void rather than as evidence of a quiet trading day.

## Filings (last 24h)

*(none — see run status above)*

## STOCK Act drift (>45 days late)

*(not evaluated this run — no filing data available)*

## Special-flag tickers status

Homebuilder tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO,
TMHC) and Brand 9 client tickers could not be checked against any filings
because no filings were retrieved.

## Recommendation

Before the next scheduled run, confirm this session's network egress policy
allow-lists the fetch tool to reach: `efdsearch.senate.gov`,
`disclosures-clerk.house.gov`, `quiverquant.com`, `capitoltrades.com`, and
`unusualwhales.com`. If the fetch tool itself is broken independent of
policy (it failed on a non-financial control URL), that also needs fixing
before this routine can produce real output.
