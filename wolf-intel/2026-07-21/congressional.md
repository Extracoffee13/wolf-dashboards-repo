# WOLF Congressional Trading Watch — 2026-07-21

## Run status: SOURCE ACCESS BLOCKED

Every primary and aggregator source specified for this watch returned **HTTP 403
Forbidden** on direct fetch today. This is a data-access failure, not a "no
new filings" day — treat the scored list below as **unconfirmed leads**, not a
verified last-24h filing set.

### Source access log

| Source | URL attempted | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | 403 |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | 403 |
| CapitolTrades | capitoltrades.com/trades | 403 |
| Quiver Quantitative | quiverquant.com/congresstrading/ | 403 |
| Unusual Whales | unusualwhales.com/politics | 403 |
| InsiderFinance | insiderfinance.io/congress-trades | 403 |
| CongressStock | congressstock.com/trades | 403 |
| AltIndex | altindex.com/congress-trading | 403 |
| Barchart | barchart.com/investing-ideas/politician-insider-trading | 403 |
| Benzinga (article pages) | benzinga.com/... | 403 |
| Yahoo Finance (article page) | finance.yahoo.com/... | 403 |
| House Rules Cmte announcement page | rules.house.gov/media/announcement/... | 403 |

All of these are direct-fetch (WebFetch tool) attempts; the proxy status
(`__agentproxy/status`) showed no relay-level denials, so the 403s are coming
from the destination sites themselves (bot/anti-scrape protection), not an
org egress policy block. WebSearch (which uses a different backend) still
returned indexed snippets from several of these sites — those are reported
below as **unconfirmed leads**, sourced from search-result summaries rather
than the primary filing pages, and their disclosure dates could not be
verified as falling in the last 24 hours.

## Unconfirmed leads (from WebSearch snippets, not verified against primary filings)

These surfaced in search results referencing Congressional trading activity.
None could be confirmed as filed/disclosed within the last 24 hours (the
transaction dates below are all older than 24h; filing-date confirmation
requires the primary portals, which were inaccessible today).

| Member | Chamber/Party | Ticker | Type | Size (as reported) | Transaction date | Filed date | Days to file | Score* |
|---|---|---|---|---|---|---|---|---|
| Gary Peters | Senate / D-MI | T (AT&T) | Buy | $1,001–$15,000 | 2026-06-29 | unconfirmed | unconfirmed | 2 (unconfirmed) |
| Tommy Tuberville | Senate / R-AL | Tractor Supply (TSCO), Lockheed Martin (LMT), Westinghouse Air Brake (WAB) | Sell | not specified | 2026-06-08 (TSCO, LMT), 2026-06-09 (WAB) | unconfirmed, reported as "first trades of 2026 disclosed" in a July article | unconfirmed — potentially large if true | 4 (unconfirmed — Ag Cmte/TSCO + Armed Services/LMT committee-relevant, known-track-record trader) |
| Nancy Pelosi | House / D-CA | INTC (Intel), UBER | Buy (200 call options each, $50 strike, exp 2027-03-19) | INTC $1M–$5M; UBER $500K–$1M | 2026-05-29 | unconfirmed (reported as "first trades since January 2026") | unconfirmed | 5 (unconfirmed — known-track-record member, large size, liquid names) |

*Scores are illustrative only given the member/ticker/size are third-party
reported but the filing date is not verified as being in this run's 24h
window. **Do not treat this table as today's confirmed filing list.**

## Special flags

- **Homebuilder tickers** (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
  MHO, TMHC): none found in any accessible source today.
- **Brand 9 client tickers**: no client-ticker list exists in this repo to
  check against (searched for `client ticker` / `Brand 9 client` — no
  matches). This flag cannot be evaluated until such a list is added.
- **STOCK Act drift (>45 days)**: cannot be computed — no verified
  transaction-to-filing date pairs available today.

## Legislative context (verified, dated)

- House Committee on Rules held a meeting announced for **2026-07-20**
  covering **H.R. 7008 — Stop Insider Trading Act** and H.R. 6955 — Main
  Street Capital Access Act. This is directly relevant to the congressional
  trading beat (a bill that would restrict members' stock trading) but is
  legislative activity, not a PTR filing. Source: rules.house.gov meeting
  announcement (confirmed via search index; page itself 403'd on direct
  fetch, so full markup details are unverified).

## Recommendation for next run

Today's run could not fulfill the core mandate (scan + score last-24h PTR
filings) because every configured source blocks direct automated fetches.
To fix this durably:
1. Provision a Quiver Quantitative API key (their Congress Trades API is
   built for this — $15–75/mo tiers) instead of scraping the dashboard.
2. Alternatively, script the Senate eFD and House Clerk portals through a
   proper session/cookie flow (they require accepting a search-agreement
   form before returning results) rather than a bare GET.
3. Until one of the above is in place, this watch cannot produce a reliably
   verified daily filing list — it will report source-access status
   honestly rather than presenting unconfirmed search snippets as scored
   intel.
