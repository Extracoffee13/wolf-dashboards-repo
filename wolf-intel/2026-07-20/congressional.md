# WOLF Congressional Trading Watch — 2026-07-20

## Data access status: BLOCKED

Every primary and aggregator source specified for this scan returned a hard block to automated retrieval during today's run:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | HTTP 403 |
| House CHDP | disclosures-clerk.house.gov/FinancialDisclosure | HTTP 403 |
| Quiver Quantitative | quiverquant.com/congresstrading/ | HTTP 403 |
| Quiver Quantitative (news feed) | quiverquant.com/news/category/congress_trades_automated | HTTP 403 |
| CapitolTrades | capitoltrades.com/trades | HTTP 403 |
| InsiderFinance | insiderfinance.io/congress-trades | HTTP 403 |
| Barchart | barchart.com/investing-ideas/politician-insider-trading | HTTP 403 |
| TrendSpider | trendspider.com/markets/congress-trading/ | HTTP 403 |
| Congress Stock Tracker | congressstock.com/trades | HTTP 403 |
| AltIndex | altindex.com/congress-trading | HTTP 403 |
| Unusual Whales | unusualwhales.com/politics | HTTP 403 |

All of these sites returned 403 Forbidden to the fetch tool (anti-bot/Cloudflare-style protection on JS-driven trackers), not a proxy or network fault — the agent proxy itself reported no relay failures. None of these portals expose a scrapeable feed the current toolset can reach. **No filing-level data for the 2026-07-19→2026-07-20 window could be independently verified against a primary or aggregator source today.**

Because this brief exists to inform real trading/positioning decisions, WOLF is not fabricating tickers, sizes, or dates to fill the table below. A filing list will populate here once source access is restored (browser-based fetch, an authenticated API key for Quiver/Capitol Trades, or a working scrape path).

## What background search *did* surface (NOT verified as last-24h, included for continuity only)

These came from web search snippets of news coverage, not from re-fetching a primary filing. Dates are the underlying trade/disclosure dates reported by the source, not 2026-07-19/20 — they are listed only so tomorrow's run has a baseline to diff against, and none are scored as part of this cycle's filings.

- **Sen. Tommy Tuberville (R-AL)** — reported sales incl. Tractor Supply (TSCO), Westinghouse Air Brake (WAB), and Lockheed Martin (LMT), transactions dated ~June 8–9, 2026, disclosure covered by Benzinga around mid-July 2026. Tuberville sits on Senate Agriculture (TSCO) and Armed Services (LMT) — committee-relevant if confirmed. **Not independently verified today; article itself was also 403-blocked on re-fetch.**
- **Rep. Dan Meuser (R-PA)** / **Rep. Gil Cisneros (D-CA)** — first known congressional SpaceX purchases, dated June 15 and June 18, 2026 respectively, per CNBC (2026-07-03). Meuser sits on House Financial Services; Cisneros on House Armed Services (SpaceX is a major DoD contractor) — committee-relevant if confirmed.
- **Rep. Nancy Pelosi (D-CA)** — most recent trade found in search index dated 2026-05-29, UBER purchase, $500,001–$1,000,000. Stale relative to this window.

## STOCK Act drift (late-filed >45 days) — background, not this cycle's data

Search surfaced ongoing, previously-reported STOCK Act compliance stories that remain relevant context for the "drift" watch but are not new to this 24h window:
- **Rep. Julia Letlow (R-LA)** — disclosed 224 transactions in Jan 2026, 211 of them >45 days late (some over a year), $225K–$3.3M aggregate, per Forbes/NOTUS.
- **Rep. Kevin Hern (R-OK)** — ~10 disclosures reported late, $4.2M–$17.6M aggregate, per Oklahoma Watch (2026-03-10); his office disputes the characterization.
- **Rep. Linda Sánchez (D-CA)** — late-filed sale of Cisco (CSCO), up to $15,000, per NOTUS.

## Scoring

Not applicable this cycle — no last-24h filing set to score. Scoring rubric (member track record / committee relevance / cluster behavior / homebuilder & Brand 9 client-ticker auto-bump / size) remains as specified and will apply once a filing feed is reachable.

## Follow-up for next run

1. Retry with a browser-capable fetch path (headless browser / Playwright) instead of the flat WebFetch tool, since these are all JS-rendered SPAs behind bot protection.
2. If available, use Quiver Quantitative's or CapitolTrades' paid API (key-authenticated requests are less likely to hit the same edge block than anonymous scraping).
3. Senate eFD and House CHDP are the ground-truth sources; both require an authenticated/JS session for search — worth checking whether a direct docs-query endpoint exists that returns raw XML/PDF filing links without the search UI.
