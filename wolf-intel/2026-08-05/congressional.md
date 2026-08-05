# WOLF Congressional Trading Watch — 2026-08-05

## Status: SOURCE ACCESS BLOCKED — no verified filings for this run

This run attempted to scan the last 24h of US congressional Periodic Transaction
Report (PTR) filings across all five specified sources. Every source rejected
the fetch. No filing-level data was retrieved, so **no trades are reported
below** — publishing placeholder or reconstructed-from-memory trades would be
fabricated data and is not done here.

### Sources attempted

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | HTTP 403 (session/consent-gated search form; not fetchable without an authenticated browser session) |
| Senate eFD report API | efdsearch.senate.gov/search/report/data/ | HTTP 403 |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | HTTP 403 |
| Quiver Quantitative | quiverquant.com/congresstrading/ | HTTP 403 (bot-protected) |
| Quiver Quantitative news | quiverquant.com/news/category/congress_trades_automated | HTTP 403 |
| CapitolTrades | capitoltrades.com/trades | HTTP 403 (bot-protected) |
| CapitolTrades RSS | capitoltrades.com/rss | HTTP 403 |
| Unusual Whales | unusualwhales.com/politics | HTTP 403 |
| AltIndex (alt aggregator, attempted as fallback) | altindex.com/congress-trading | HTTP 403 |
| CongressStock (alt aggregator, attempted as fallback) | congressstock.com/trades | HTTP 403 |
| General web search | — | Returned only generic/evergreen pages about the STOCK Act and tracker sites; no filing-level results (name/ticker/date/size) for the last 24h — search indexing does not surface individual PTR filings at that granularity or freshness |

### Why this happened

All of the aggregator sites (Quiver, CapitolTrades, Unusual Whales, AltIndex,
CongressStock) sit behind bot/anti-scraping protection that rejects
unauthenticated automated fetches with a flat 403. The two primary government
portals (Senate eFD, House CHDP) require an interactive session — Senate eFD
gates its search behind a click-through agreement, and both portals are
JS-driven search forms rather than static/GET-able listing pages.

### What this means

- Zero filings scored in this run — not because nothing was filed, but because
  the run could not observe the data.
- STOCK Act drift, homebuilder-ticker, and Brand 9 client-ticker flags all
  stand down for this run — there is nothing to check them against.
- This is a **pipeline gap**, not a "quiet news day."

### Recommended remediation for future runs

1. Provision an authenticated fetch path (API key for Quiver Quantitative's
   congress-trading API, or a headless-browser/MCP tool that can hold cookies
   and pass bot checks) rather than relying on plain WebFetch/WebSearch.
2. If no authenticated path is available, consider dropping this to a
   lower-frequency manual-trigger task rather than a daily automated one, so a
   blocked run doesn't silently look identical to a quiet one.

## Full scored filing list

None — see Status above.

## STOCK Act drift (>45 days late)

None to report — see Status above.
