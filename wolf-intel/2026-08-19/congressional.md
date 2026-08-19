# WOLF Congressional Trading Watch — 2026-08-19

## Run status: DATA ACCESS FAILURE — no verified last-24h filings

This run could not retrieve real-time filing data. Every primary and
aggregator source specified in the task was unreachable from this
environment:

| Source | Result |
|---|---|
| efdsearch.senate.gov (Senate eFD) | `EGRESS_BLOCKED` |
| disclosures-clerk.house.gov (House CHDP) | `EGRESS_BLOCKED` |
| quiverquant.com | `EGRESS_BLOCKED` |
| capitoltrades.com | `EGRESS_BLOCKED` |
| unusualwhales.com | `EGRESS_BLOCKED` |
| congressstock.com, pelositracker.app, trendspider.com, marketbeat.com, notus.org, benzinga.com, reuters.com (fallback probes) | `EGRESS_BLOCKED` / unreachable |

The `WebFetch` tool returned `EGRESS_BLOCKED` for every domain attempted in
this session, including generic news domains used as a control (reuters.com).
This indicates this execution environment's network egress policy does not
allowlist any of these hosts — not a transient outage on the source side.
Only the built-in web-search tool (which returns short synthesized snippets,
not raw filing data) and GitHub were reachable.

**Because no primary-source data could be verified, no scored filing list is
published below.** Inventing plausible-looking filings, tickers, or size
buckets to fill this table would misrepresent fabricated content as real
STOCK Act disclosures, which this report will not do.

## What was found (background only — NOT a last-24h filing, do not treat as today's scan result)

Cross-referenced via search snippets across multiple independent local-news
outlets (The Vindicator, The Review, Salem News, Morning Journal), NOTUS,
Yahoo Finance, Benzinga, and Quiver Quantitative's own news feed (page
content itself unreachable, headlines/snippets only):

- **Rep. Michael A. Rulli (R-OH-6)** filed a disclosure on **2026-08-07**
  covering 32 trades, of which 22 were filed past the STOCK Act's 45-day
  deadline (some transactions dating back to late 2024). Reported tickers
  per snippets: PLTR, PFE, GOOGL, AMZN, AAPL, META, MSFT, NVDA, ORCL, KO —
  attributed to a Merrill Lynch managed account per his office's
  explanation.
  - This filing is **12 days outside** the last-24h scan window for this
    run and is *not* scored against this run's criteria. It's noted here
    only because it surfaced repeatedly and independently in search results
    and is a live, ongoing STOCK Act enforcement story worth the desk's
    awareness. Verify directly against the House Clerk filing before citing
    exact dollar amounts or per-transaction dates — none of that detail was
    independently confirmed here, only ticker list and violation framing.

## STOCK Act drift section

Not populated this run — no primary-source late-filing data was accessible
to confirm days-between-transaction-and-disclosure for any filing.

## Special flags (homebuilders, Brand 9 client tickers)

Not evaluated — no filing data was retrieved to check against the
homebuilder ticker list (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
MHO, TMHC) or Brand 9 client tickers. Note separately: no "Brand 9 client
tickers" list exists anywhere in this repo as of this run, so that flag has
no defined list to check against even when data access is restored —
recommend someone add one (e.g. `wolf-intel/config/brand9-client-tickers.txt`)
if this flag is meant to be operative.

## Recommendation

This task needs either (a) an environment/session with broader network
egress allowlisting the Senate eFD, House Clerk, and at least one
aggregator domain, or (b) a data source reachable via an API key/MCP
connector rather than raw HTTP fetch of these sites. Flagging for the
operator rather than silently producing a placeholder-only report.
