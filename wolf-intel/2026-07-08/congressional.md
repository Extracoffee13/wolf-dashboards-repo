# Congressional Trading Watch — 2026-07-08

## Scan status: BLOCKED — no verified filings for this run

Every primary and aggregator source attempted for this scan returned a hard block
(HTTP 403) or was otherwise unreachable. This is a **data-access failure, not a
quiet news day** — the difference matters for a receipts-public product, so this
report says so plainly instead of filling the table with guesses.

### Sources attempted, all blocked

| Source | URL | Result |
|---|---|---|
| Senate eFD search | efdsearch.senate.gov/search/ | 403 |
| Senate Public Disclosure | disclosure.senate.gov | not reachable via automated fetch |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | 403 |
| Quiver Quantitative | quiverquant.com/congresstrading, quiverquant.com/news/* | 403 (all paths) |
| CapitolTrades | capitoltrades.com/trades, bff.capitoltrades.com (API) | 403 |
| Benzinga Government Trades | benzinga.com/government-trades, /topic/congress-trades | 403 |
| Unusual Whales politics | unusualwhales.com/politics | 403 |
| TrendSpider congress tracker | trendspider.com/markets/congress-trading | 403 |
| StockActWatch | stockactwatch.com/politicians | 403 |
| GuruFocus congress trading | gurufocus.com/congress_trading.php | 403 |
| senatestockwatcher.com | — | DNS does not resolve (site appears defunct) |
| senate-stock-watcher-data (GitHub mirror) | raw.githubusercontent.com/timothycarambat/senate-stock-watcher-data | Reachable, but **last entry is 2021-03-10** — this community mirror stopped updating years ago and is not a live source |

Every congressional-trading-specific site blocked the automated fetch (consistent
403 across ~9 distinct domains, including sites with very different hosting stacks),
which points to bot/WAF protection at each site rather than a local network issue —
confirmed clean via the proxy status check.

### What could be surfaced (unverified, background only — NOT scored, NOT counted as today's filings)

General web search turned up a handful of real politician/ticker pairings from
recent news indexing, but without confirmed filing dates, exact amounts, or
confirmation these fall in the last 24h. Listed here for awareness only —
**do not treat as today's PTR data**:

- Rep. Josh Gottheimer (D-NJ) — partial sale, ABT, $1,001–$15,000 (dated ~2026-05-27 per search snippet, well outside any 24h window)
- Sen. Markwayne Mullin (R-OK) — prior 2026 purchases spanning NVDA, MPWR, MCK, AMKR (Jan–Mar 2026 window per search snippets); a separate headline references a Mullin trade in Chevron/Raytheon tied to a "Maduro capture" news event, exact date unconfirmed
- Headline fragments only, no dates/amounts recoverable: Rep. Daniel Meuser (SPCX), Rep. Ed Case (PG), Sen. David McCormick (BITB), Rep. Nancy Pelosi (NVDA), Sen. John Boozman (CEG), Rep. Mark Alford (AMZN), Rep. David Taylor (JPM), Rep. Gilbert Ray Cisneros Jr. (WTW), Rep. Lloyd Smucker (PRU)

None of the above can be responsibly scored 1–5, sized, or checked against the
45-day STOCK Act clock without a verified filing date and PTR amount — doing so
would mean inventing numbers.

### Homebuilder / Brand 9 client ticker check

Not run — cannot screen filings that could not be retrieved. No auto-bump flags
issued for this date.

### STOCK Act drift section

Not run for the same reason. No late-filing determinations can be made without
verified transaction and disclosure dates.

## Recommendation

This scan needs a durable fix, not a retry tomorrow with the same tools:
- A paid/authenticated API key for Quiver Quantitative or CapitolTrades (both offer
  developer APIs that bypass the anti-bot layer hit here) would make this reliable.
- Failing that, efd.senate.gov and the House Clerk portal are the two sources
  Congress is legally required to publish to — worth investigating a scheduled,
  properly-headered scraper or a maintained third-party mirror (the GitHub mirror
  used here died in 2021 and would need a live successor).
