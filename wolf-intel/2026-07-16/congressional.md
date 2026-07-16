# WOLF Congressional Trading Watch — 2026-07-16

## STATUS: DATA COLLECTION FAILED — NO FILINGS TO REPORT

This run could not retrieve any congressional trading disclosures. Every
mandated and fallback source returned HTTP 403 (Forbidden) to the fetch
tool available in this environment. No filing data below is real; none was
fabricated to fill the template. This file exists to record the failure
honestly rather than ship invented tickers, names, or sizes as if they were
verified filings.

## Sources attempted (all blocked, 403)

| # | Source | URL | Result |
|---|--------|-----|--------|
| 1 | CapitolTrades | capitoltrades.com/trades?txDate=1d | 403 |
| 2 | CapitolTrades (via reader proxy) | r.jina.ai/https://www.capitoltrades.com/trades?txDate=1d | 403 |
| 3 | Quiver Quantitative | quiverquant.com/congresstrading/ | 403 |
| 4 | Senate eFD search | efdsearch.senate.gov/search/ | 403 |
| 5 | House Clerk Public Disclosure | disclosures-clerk.house.gov/PublicDisclosure | 403 |
| 6 | CongressStock.com | congressstock.com | 403 |
| 7 | AltIndex congress tracker | altindex.com/congress-trading | 403 |
| 8 | InvestorLens | investorlens.capital/politicians | 403 |
| 9 | Unusual Whales congress feed | unusualwhales.com/politics/insider_trades | 403 |
| 10 | StockCircle | stockcircle.com/congress-stock-trades | 403 |
| 11 | GuruFocus (Pelosi politician page) | gurufocus.com/politician/7/nancy-pelosi | 403 |
| 12 | Amsflow (Pelosi portfolio) | amsflow.com/data-reports/portfolios/politicians/nancy-pelosi | 403 |
| 13 | PolyTICK (Pelosi analysis blog) | polytick.us/blog/nancy-pelosi-best-stock-trades-2026-analysis | 403 |
| 14 | Benzinga (specific trade article) | benzinga.com/news/politics/26/07/60387909/... | 403 |

Web search (not fetch) worked and surfaced one credible headline — a House
member reportedly buying Brookfield Renewables (BEP) stock six times in
three days while chairing a committee overseeing Latin America policy, and
also buying Voyager Technologies while on House Foreign Affairs — but the
source article itself 403'd on fetch, so the member's name, exact dates,
sizes, and filing date could not be verified against a primary or
near-primary source. Per this repo's standing rule against reporting
unverified financial-intelligence claims as fact, **it is not included as
a scored filing below** — flagging it here only as a lead for tomorrow's
run, to be confirmed against a primary filing before scoring.

## No filings scored today

Nothing met the bar for inclusion (member, ticker, size bucket, and
transaction/disclosure dates all independently confirmed against a
primary or reputable aggregator source). Zero filings scanned, zero
scored.

## STOCK Act drift section

Not assessable this run — no filings retrieved to check the 45-day window.

## Special-flag tickers (homebuilders, Brand 9 clients)

Not assessable this run — no filings retrieved to check against the
homebuilder list (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO,
TMHC) or Brand 9 client list.

## Recommendation

The fetch tool in this environment appears to be systematically blocked
(403) by every congressional-trading data source tried, including sites
with no obvious aggressive bot protection (e.g. GuruFocus, Amsflow),
suggesting an environment/IP-level block rather than a single site's
defense. If this persists across future runs, congressional trading data
collection likely needs either an API key (e.g. Quiver Quantitative's
paid API, which is designed for programmatic access rather than page
scraping) or a different fetch path than the one available here.
