# WOLF Congressional Trading Watch — 2026-07-06

**Status: DATA ACCESS FAILURE — no verified filings retrieved.**

This run could not source real congressional PTR filings for the last 24
hours. It is reported here rather than filled in with invented names,
tickers, or sizes, because fabricated filing data in an intel feed is worse
than no feed at all.

## What was attempted

| Source | Method | Result |
|---|---|---|
| Senate eFD (efdsearch.senate.gov) | WebFetch | HTTP 403 |
| House CHDP (disclosures-clerk.house.gov) | WebFetch | HTTP 403 |
| Quiver Quantitative (quiverquant.com/congresstrading) | WebFetch | HTTP 403 |
| CapitolTrades (capitoltrades.com) | WebFetch | HTTP 403 |
| Unusual Whales congress feed (unusualwhales.com/politics/insider_trades) | WebFetch | HTTP 403 |
| Barchart politician insider trading | WebFetch | HTTP 403 |
| GovTrades | WebFetch | HTTP 403 |
| Trendlyne US politician tracker | WebFetch | HTTP 403 |
| InsiderFinance congress trades | WebFetch | HTTP 403 |
| PelosiTracker.app | WebFetch | HTTP 403 |
| CongressStock.com | WebFetch | HTTP 403 |
| senatestockwatcher.com | WebFetch | DNS resolution failure |
| Senate Stock Watcher open-data mirror (GitHub, `timothycarambat/senate-stock-watcher-data`) | WebFetch | Reachable, but the dataset is a stale archive last updated ~2020 — not usable for a 2026-07-06 scan |
| WebSearch (general queries for recent filings/news) | WebSearch | Returned only generic background/overview links (STOCK Act explainer, year-old CNN piece, 2025 report retrospectives); no per-filing detail for the last 24h surfaced |

Every live tracker site returned a clean HTTP 403 (not a proxy error — the
agent proxy status check showed zero relay failures, so these are
origin-side bot-protection blocks, consistent with Cloudflare/PerimeterX
gating on all of them). No credentialed/API path to any of these sources is
configured in this environment.

## Scoring rubric (for reference, unused this run)

- **5**: known-track-record member (Pelosi, Tuberville, Crenshaw cluster) trading large size in a liquid name
- **4**: committee-relevant trade (e.g., Energy committee buying an oil major, Defense committee buying a defense name)
- **3**: cluster behavior — 3+ members trading the same ticker in the same week
- **2**: notable but standalone
- **1**: noise — small size, unrelated committee
- Auto-bump to 4+: any homebuilder ticker (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)
- Auto-bump to 4+: any Brand 9 client ticker (no client-ticker list was found in this repo to check against — see note below)
- STOCK Act drift: separate section for any filing disclosed >45 days after the transaction date

## Notes for next run

- No Brand 9 client ticker list exists anywhere in this repo (`b9-about-motion-preview.html` is marketing copy, not a ticker list). If a client-ticker watchlist exists elsewhere, it needs to be added to this repo so the auto-bump rule is checkable.
- To make this scan actually work, this environment needs either: (a) an allowlisted outbound path / different fetch mechanism that isn't blocked by these sites' bot protection, or (b) API credentials for one of the aggregators (Quiver Quantitative and Unusual Whales both offer paid APIs intended for programmatic access, which would likely bypass the browser-facing 403s).
- No filings section, no scored list, and no STOCK Act drift section are populated below because there is nothing verified to put in them.

## Filings (last 24h)

_None retrieved — see status above._

## STOCK Act drift (>45 days late)

_None retrieved — see status above._
