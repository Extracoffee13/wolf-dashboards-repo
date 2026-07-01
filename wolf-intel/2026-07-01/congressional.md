# WOLF Congressional Trading Watch — 2026-07-01

Scan window: last 24h (2026-06-30 → 2026-07-01)

## Result: scan blocked at source — zero verified filings

Every source specified for this scan refused the fetch. This is not a "quiet day"
finding — it is a data-access failure, and it's being reported as one rather than
papered over with invented filings.

| Source | Method tried | Result |
|---|---|---|
| efd.senate.gov (Senate eFD search) | WebFetch `efdsearch.senate.gov/search/` and `/search/home/` | HTTP 403 |
| clerk.house.gov CHDP | WebFetch `disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure` | HTTP 403 |
| clerk.house.gov raw PTR PDF | WebFetch a specific 2026 PTR PDF surfaced via search (`ptr-pdfs/2026/20033725.pdf`) | HTTP 403 |
| quiverquant.com/congresstrading | WebFetch listing page + news category page | HTTP 403 |
| capitoltrades.com/trades | WebFetch | HTTP 403 |
| congressstock.com/trades | WebFetch | HTTP 403 |
| barchart.com politician-insider-trading | WebFetch | HTTP 403 |
| insiderfinance.io/congress-trades | WebFetch | HTTP 403 |
| web.archive.org (fallback snapshot) | WebFetch | Tool cannot reach this host at all |
| Unusual Whales congressional feed | Not attempted directly — indexed pages found via search only, main dashboard is subscriber-gated | n/a |

The agent proxy status was checked (`__agentproxy/status`) and shows no relay
failures — this is the target sites' own bot/anti-scrape protection (Cloudflare-style
403s), not a local network issue.

## What WebSearch surfaced (not usable as filing data)

WebSearch returned indexed page titles and some prose summaries. Titles/URLs
that are plainly real (indexed by a search engine) but **outside the 24h window**
or otherwise unusable as today's filings:

- Nancy Pelosi (D-CA, House) — INTC and UBER trades, both dated **2026-05-29**
  (quiverquant.com trade pages `House-P000197-219` / `-220`). More than a month
  old — not a same-day filing, not in scope for this brief.
- Rep. Tim Walberg (R-MI, House) — a QuiverQuant/NOTUS story on a **STOCK Act
  late-disclosure violation** from a Feb 7, 2025 purchase (~$154K–$560K,
  Boeing/L3Harris/Lockheed/Chevron/ExxonMobil). Old news, already public
  months ago — flagged here only so it isn't mistaken for something new.

Separately, when asked to summarize "recent Pelosi trades," the search
summarizer produced a specific-sounding cluster (Broadcom calls $1M–$5M, 10,000
NVDA shares $1M–$5M, a $250K–$500K Tesla sale) that **directly contradicted**
another claim in the same response ("most recent transaction was 2026-05-29").
That internal contradiction is a strong signal the summary was generated from
general pattern knowledge rather than a real page, so none of those specific
numbers are included as findings anywhere in this report or the public brief.

## STOCK Act drift section

No new late filings (>45 days) verified in this window. The Walberg item above
is old/already-disclosed and not a new drift event.

## Special-flag tickers (homebuilders, Brand 9 clients)

No filings to check against the homebuilder list (LEN, KBH, DHI, PHM, TOL, MTH,
TPH, NVR, BZH, MDC, MHO, TMHC) or Brand 9 client tickers — there's no verified
filing data to check. Note separately: no Brand 9 client ticker list currently
exists anywhere in this repo, so even with filing data, that flag couldn't be
auto-applied yet. That list needs to be added somewhere (e.g.
`wolf-intel/config/brand9-tickers.md`) for future runs to use.

## Recommendation

Senate eFD, House CHDP, CapitolTrades, and Quiver all sit behind bot protection
that a plain HTTP fetch tool cannot pass. A durable fix needs one of:
- A paid/authenticated API (Quiver Quantitative has one) wired in as a proper
  tool/MCP, rather than scraping the public dashboard.
- A headless-browser-based fetch path that can clear Cloudflare-style checks,
  if that's operationally acceptable.
- Direct bulk-download of Senate/House XML/PDF disclosure archives (these
  portals do publish bulk data files on a schedule) rather than the search UI.

Until one of those is in place, this daily scan will keep coming back empty on
the "hard data" side even on days with real trading activity.
