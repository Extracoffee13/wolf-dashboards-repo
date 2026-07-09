# WOLF — Congressional Trading Watch
**Date:** 2026-07-09
**Window:** last 24h of PTR filings
**Status:** ⚠️ NO VERIFIED FILINGS — SOURCE ACCESS BLOCKED

## Summary

This run could not confirm any specific Periodic Transaction Reports (PTRs)
filed in the last 24 hours. Every primary and aggregator source attempted
returned `403 Forbidden` to automated fetch, and the one open-data mirror
that did respond turned out to be stale (last populated January 2021). No
filing data below should be treated as "today's activity" — there isn't
any that could be verified this run.

This is a **tooling/access gap**, not a "quiet news day" finding. Treat the
scored list section as empty pending a working data path.

## Sources attempted and results

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/home/ | `403 Forbidden` |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | `403 Forbidden` |
| House PTR PDF (direct, via search-indexed link) | disclosures-clerk.house.gov/public_disc/ptr-pdfs/2026/20033725.pdf | `403 Forbidden` |
| CapitolTrades | capitoltrades.com/trades (+ internal API guess) | `403 Forbidden` |
| Quiver Quantitative | quiverquant.com/congresstrading/ | `403 Forbidden` |
| Congress Stock Tracker | congressstock.com/trades | `403 Forbidden` |
| InsiderFinance | insiderfinance.io/congress-trades | `403 Forbidden` |
| Unusual Whales | unusualwhales.com/politics | not directly fetchable; only search snippets available (no per-filing data surfaced) |
| Congress Tier List | congresstierlist.com | `403 Forbidden` |
| GitHub open-data mirror: `senate-stock-watcher-data` | raw.githubusercontent.com/timothycarambat/senate-stock-watcher-data | Reachable, but **dataset ends January 2021** — abandoned, not usable for a 2026 daily watch |
| `housestockwatcher.com/api` | — | DNS resolution failed (`ENOTFOUND`) — domain appears dead |
| GitHub API directory/commit listings | api.github.com/repos/... | `403 Forbidden` (likely unauthenticated rate limit) |

Confirmed via `curl $HTTPS_PROXY/__agentproxy/status`: zero relay failures logged,
so these are genuine 403s from the destination sites (bot/scraper protection),
not a local proxy/TLS problem.

## Web search cross-check

General web search surfaced only background/stale material, nothing datable
to the last 24h:
- Nancy Pelosi's most recent PTR indexed by search discloses Paul Pelosi
  call-option purchases in INTC and UBER (200 contracts each) — but the
  underlying transaction date is **2026-05-29**, well outside this window,
  and the filing itself is not independently re-verifiable here since the
  House PDF link 403'd on fetch.
- Sen. Markwayne Mullin's most recently surfaced disclosures in search
  results date to **January/March 2026** (MPWR, MCK buys; AZO, INTU sells,
  UNH buy) — also stale relative to this window.
- No CapitolTrades/Quiver snippet returned specific member+ticker+date rows
  for 2026-07-08 or 2026-07-09.

None of the above should be scored as "today's filings" — they're listed
only to show what the search layer could and couldn't surface.

## Scored filings (last 24h)

*(none — see Status above)*

## STOCK Act drift (>45 days late)

*(not assessable this run — no filings retrieved)*

## Special-flag watchlists (for reference, not triggered this run)

- **Homebuilders:** LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC
- **Brand 9 client tickers:** no client-ticker list found in this repo
  (searched for `brand9`/`brand 9`/"client ticker" across `.md`/`.json`/`.yaml`).
  If a client-ticker file should exist, point WOLF at it so this flag can
  actually run.

## Recommendation

To make this watch functional going forward, one of:
1. An authenticated API key for Quiver Quantitative or a similar paid
   congressional-trading data provider (their raw sites block generic
   scraping/fetch tools), or
2. A maintained open-data mirror (the `senate-stock-watcher` /
   `house-stock-watcher` GitHub projects are dead as of this check — a
   live replacement would need to be identified), or
3. Direct, authenticated access to efdsearch.senate.gov / House CHDP
   (both require session/JS interaction that a plain fetch can't do).

Until one of those is in place, expect this file to report the same access
failure each day rather than real filings.
