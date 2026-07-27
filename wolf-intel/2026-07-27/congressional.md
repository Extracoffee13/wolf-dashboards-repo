# WOLF Congressional Trading Watch — 2026-07-27

## Run status: BLOCKED — no verified filings retrieved

This run could not confirm any actual last-24h Periodic Transaction Report
(PTR) filings. All primary sources returned HTTP 403 (bot-protection /
access-denied) to both the fetch tool and, where checked, are confirmed not
to be a local proxy/network issue (proxy status showed zero relay failures —
the 403s originated at the destination hosts, not our egress).

| Source | URL attempted | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | 403 Forbidden |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | 403 Forbidden |
| Quiver Quantitative | quiverquant.com/congresstrading/ | 403 Forbidden |
| CapitolTrades | capitoltrades.com/trades (also `?txDate=1d`) | 403 Forbidden |
| Unusual Whales | unusualwhales.com/politician-trades | 403 Forbidden |
| AltIndex (secondary aggregator) | altindex.com/congress-trading | 403 Forbidden |
| congressstock.com (secondary aggregator) | congressstock.com/trades | 403 Forbidden |
| Benzinga (news, sanity check) | benzinga.com article on a senator's 2026 disclosure | 403 Forbidden |

General web search (not a structured filings feed) surfaced references to
trading-disclosure news from earlier in the period — e.g. a senator's
first-2026 disclosure of stock sales (transactions dated June 8–9) and a
Pelosi INTC/UBER purchase (traded 2026-05-29, filed 2026-06-23) — but none
of this is confirmed as filed in the **last 24 hours**, and search-snippet
dates are not reliable enough to score or publish as intel. Per task
instructions, no filing is reported below unless chamber, ticker, size
bucket, and both trade/filing dates could be confirmed from a primary or
aggregator source directly — that bar was not met today.

## Filings (scored)

None retrievable this run.

## STOCK Act drift (>45 days late)

None retrievable this run.

## Special-flag tickers (homebuilders, Brand 9 clients)

Not evaluable — no filings retrieved to check against the watchlist.

## Recommendation

The fetch tool is being blocked at the HTTP layer (403) by every target site,
most likely Cloudflare/bot-detection on all five. To make this watch
functional going forward, this needs either: (a) an API key / authenticated
partner feed for Quiver Quantitative or CapitolTrades, or (b) a
browser-automation path (rendered session, not a raw fetch) to clear the
bot-detection challenge. Until one of those is in place, this daily watch
will keep coming back empty rather than reporting real data.
