# WOLF Congressional Trading Watch — 2026-07-17

## Status: SCAN FAILED — no verified filing data captured

This run attempted to scan the last 24h of US Senate + House periodic
transaction reports (PTRs) per the standing brief. Every data source
listed in the task, plus several fallbacks, returned HTTP 403 (blocked)
or served stale/dead data. No filing-level data in this report should be
treated as real — none was successfully retrieved, and none is included
below.

## Sources attempted

| Source | Result |
|---|---|
| efdsearch.senate.gov (Senate eFD search) | 403 Forbidden |
| disclosures-clerk.house.gov/PublicDisclosure (House CHDP) | 403 Forbidden |
| disclosures-clerk.house.gov/public_disc/ptr-pdfs/... (direct PTR PDF) | 403 Forbidden |
| quiverquant.com/congresstrading | 403 Forbidden |
| api.quiverquant.com (public API endpoint, no key) | 403 Forbidden |
| capitoltrades.com/trades | 403 Forbidden |
| capitoltrades.com/trades/{id} (single deep-linked trade) | 403 Forbidden |
| bff.capitoltrades.com (CapitolTrades backend API) | 403 Forbidden |
| unusualwhales.com/politics | 403 Forbidden |
| congressstock.com/trades | 403 Forbidden |
| govtrades.com/congress-stock-tracker | 403 Forbidden |
| insiderfinance.io/congress-trades | 403 Forbidden |
| hillsignals.com/latest | 403 Forbidden |
| congresstierlist.com | 403 Forbidden |
| investorlens.capital/politicians | 403 Forbidden |
| yourreprecord.org/tools/stock-trades | 403 Forbidden |
| r.jina.ai read-proxy of capitoltrades.com | 403 Forbidden |
| GitHub `senate-stock-watcher-data` (aggregate/all_transactions.json) | Reachable, but dataset is stale — latest record is dated **2020-12-02**. Project is defunct. |
| GitHub `house-stock-watcher-data` (S3-hosted all_transactions.json) | 403 Forbidden |
| Web search (snippet-level) | Reachable, but returns only headline/summary text, not structured per-filing data (member, ticker, size, dates). Confirmed real activity exists (e.g. CapitolTrades reportedly logged 48 trades across 37 issuers on 2026-07-13, and a single trade — Rick Larsen buying Amphenol Corp (APH) — surfaced as a search snippet), but none of this is verifiable at the field level required for scoring. |

## Why no filings are listed

The scoring methodology in the standing brief requires, per filing: member
name, chamber, party, ticker, transaction type, size bucket, transaction
date, and disclosure date — verified from a primary or reputable aggregator
source. Search-snippet fragments (e.g. the Rick Larsen/APH mention) are not
sufficient to responsibly assign a 1–5 score, a committee-relevance flag,
or a STOCK Act drift calculation, since the size bucket and exact dates
were not retrievable. Rather than fabricate or infer those fields,
this report is being filed as a **failed scan**, not a zero-activity day.

## Homebuilder / Brand 9 client ticker check

Not evaluated — no filing data was retrieved to check against the
homebuilder ticker list (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
MHO, TMHC) or the Brand 9 client ticker list.

## STOCK Act drift section

Not evaluated — no filing data retrieved.

## Recommendation

Direct scraping of Senate eFD, House CHDP, and every major aggregator
(Quiver, CapitolTrades, Unusual Whales, and smaller trackers) is being
blocked at the network layer for this agent (uniform 403s, including on a
third-party read-proxy). The known-good open datasets (`senate-stock-watcher`,
`house-stock-watcher`) are abandoned and frozen at 2020-era data. To make
this watch reliable going forward, WOLF needs one of:
1. A paid API key for Quiver Quantitative (they offer a documented REST API
   that is likely allow-listed separately from the scraped web frontend), or
2. Browser-automation access (e.g. a Chrome MCP connector) that can render
   and interact with these sites like a real browser session, or
3. An explicit egress allow-list entry for efdsearch.senate.gov and
   disclosures-clerk.house.gov, which are the actual primary-source filing
   systems and the most likely to be exempted from anti-bot network policy.
