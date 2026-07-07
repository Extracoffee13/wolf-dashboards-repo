# WOLF Congressional Trading Watch — 2026-07-07

**Window:** last 24h of filings (2026-07-06 through 2026-07-07)
**Status: DATA ACCESS BLOCKED.** No last-24h filings could be independently verified. Full explanation below, followed by the most recent *confirmed* filings found (all older than 24h) as background context, then the methodology and lesson for tomorrow's run.

---

## 1. What happened

Every primary and aggregator source specified in this brief's mandate refused direct automated access:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search | HTTP 403 |
| House CHDP | disclosures-clerk.house.gov/FinancialDisclosure | HTTP 403 |
| House PTR PDF (direct) | disclosures-clerk.house.gov/public_disc/ptr-pdfs/... | HTTP 403 |
| Quiver Quantitative | quiverquant.com/congresstrading | HTTP 403 |
| CapitolTrades | capitoltrades.com/trades | HTTP 403 |
| Unusual Whales | unusualwhales.com/politics | HTTP 403 |
| Benzinga Government Trades | benzinga.com/government-trades | HTTP 403 |
| InsiderFinance, StockActWatch, Barchart, Trendlyne, InvestorLens, CongressStock | various | HTTP 403 (all) |
| GitHub API (commit history check) | api.github.com | HTTP 403 |
| housestockwatcher.com/api | — | DNS did not resolve (domain appears dead) |
| GitHub raw data mirror | timothycarambat/senate-stock-watcher-data | Loaded, but the mirror's data stops at **December 2020** — abandoned/stale, not a live feed despite its description |

This is consistent site-side WAF/bot-detection blocking (not an org egress-policy block — the proxy's own failure log recorded zero relay failures, meaning these requests reached the destination and were rejected there). Web search does surface real, dated coverage of individual filings, but the search index lags actual disclosures by roughly 5+ days — nothing indexed yet from the July 6–7 window.

**No filings are reported below as "last 24h" because none could be confirmed as such.** Fabricating tickers, sizes, or names for a trading-intel feed carries real downside if acted on — so this run reports the gap instead of a guess.

## 2. Most recent *confirmed* filings (for context only — NOT last-24h)

These were verified via independent news coverage (Benzinga, MarketBeat, Sahm Capital cross-referenced) but are 5–6 days old and are **not** in-scope for today's watch window. Carried here only so tomorrow's run has a baseline to diff against.

| Member | Chamber/Party | Ticker | Type | Size | Txn Date | Filed | Days-to-File | Score |
|---|---|---|---|---|---|---|---|---|
| Sen. Gary Peters | Senate / D-MI | T (AT&T) | Buy | $1,001–$15,000 | 2026-06-29 | 2026-07-02 | 3 | 2 |
| Sen. Mitch McConnell | Senate / R-KY | WFC (Wells Fargo) | Buy | $1,001–$15,000 | 2026-06-01 | 2026-06-30 | 29 | 2 |

Scoring rationale: both are standalone, small-bucket ($1k–$15k) trades in liquid financial/telecom names with no apparent committee nexus (Peters — Homeland Security/Commerce; McConnell — Appropriations/Rules), no cluster behavior detected, and no homebuilder or known Brand 9 client-ticker overlap. Neither is late under the 45-day STOCK Act clock.

No STOCK Act drift (>45 days) identified in the confirmed set.

## 3. Special flags

- **Homebuilder tickers** (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC): none observed in confirmed data.
- **Brand 9 client tickers**: no client-ticker list was supplied to this run — flag cannot be evaluated. Needs a ticker list wired into the task config for future runs.
- **STOCK Act drift (>45 days)**: none in the confirmed set above.

## 4. Recommendation for tomorrow's run

1. Route this task through an authenticated data connector (Quiver API key, or a licensed CapitolTrades/Unusual Whales API) rather than raw WebFetch — these sites' WAFs block generic scraper traffic regardless of proxy config.
2. If no API access is available, consider a browser-automation fetch (rendered page, real UA) instead of the raw WebFetch tool, since these are JS-heavy sites behind bot-detection.
3. Supply the Brand 9 client-ticker list as task input so that flag can actually be evaluated.
