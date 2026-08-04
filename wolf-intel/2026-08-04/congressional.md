# WOLF Congressional Trading Watch — 2026-08-04

## Status: DATA COLLECTION FAILED — no filings scored today

This run could not retrieve congressional trading data. Every configured source
returned an error at the network/tool layer, not a "no filings today" result:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | HTTP 403 |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | HTTP 403 |
| Quiver Quantitative | quiverquant.com/congresstrading | HTTP 403 |
| CapitolTrades | capitoltrades.com/trades | HTTP 403 |
| InvestorLens | investorlens.capital/politicians | HTTP 403 |
| TrendSpider | trendspider.com/markets/congress-trading | HTTP 403 |
| AltIndex | altindex.com/congress-trading | HTTP 403 |
| GuruFocus | gurufocus.com/congress_trades | HTTP 403 |
| CongressStock | congressstock.com | HTTP 403 |
| Unusual Whales | (not attempted — paywalled, and fetch layer already failing) | — |

To rule out source-specific blocking, a control fetch was made against an
unrelated, non-financial domain (Wikipedia, then Reuters). Both also failed
(403 / "unable to fetch"), confirming this is a tool-level outage in this
session's web-fetch capability, not congressional-trading sites specifically
blocking the scan.

**No filing data below is fabricated or inferred.** Per the standing WOLF
mandate, when primary sources can't be verified live, we do not backfill with
remembered/cached knowledge about named members of Congress and represent it
as a fresh scan — that risks misattributing specific trades, sizes, or dates
to real people.

## Action needed
Re-run this scan once web-fetch access is restored. If the outage persists
across multiple runs, the underlying fetch tool (not the source sites) is the
likely fault and should be checked at the harness/proxy level.

## Scored filings (last 24h)
None retrievable this run.

## STOCK Act drift (>45 days late)
None retrievable this run.
