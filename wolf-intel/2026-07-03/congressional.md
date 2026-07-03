# WOLF Congressional Trading Watch — 2026-07-03

**Coverage window:** last 24h of filings as of 2026-07-03
**Status: NO VERIFIED FILINGS — DATA PIPELINE BLOCKED**

## What happened

This run attempted to scan the five requested sources for PTR filings from the last
24 hours: Senate eFD, House CHDP, Quiver Quantitative, CapitolTrades, and Unusual
Whales. Every direct source was unreachable from this execution environment, and no
scored filing list was produced. Rather than fabricate member names, tickers, or
trade sizes to fill the template, this report documents the outage so the gap is
visible instead of silently papered over with invented data.

## Sources attempted and result

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov | Blocked — proxy returned 403 on CONNECT (org egress policy denial, confirmed via proxy status endpoint, not a site-side bot block) |
| House CHDP | disclosures-clerk.house.gov | Blocked — same 403 CONNECT denial |
| Quiver Quantitative | quiverquant.com/congresstrading | Blocked — same 403 CONNECT denial |
| CapitolTrades | capitoltrades.com/trades | Blocked — same 403 CONNECT denial |
| Unusual Whales | unusualwhales.com/politics | Blocked — same 403 CONNECT denial |
| Barchart politician tracker | barchart.com | Blocked — same 403 CONNECT denial |
| WebSearch (fallback) | n/a | Returned only indexed/historical snippets (e.g. late-May Pelosi UBER/INTC PTRs, older Letlow/Walberg/Bresnahan late-filing stories) — nothing datable to the last 24h with confidence, and snippet-only text isn't sufficient to assign a member+ticker+size+date with the accuracy this brief requires |
| GitHub open-data mirrors (attempted alternative) | `timothycarambat/senate-stock-watcher-data` | Reachable, but abandoned — latest transaction date in the dataset is 2020-12-02. Not usable for current filings. |
| Apify Congress Trading API (attempted alternative) | `johnisanerd/Apify-Congressional-Trading-Data-Scraper` | Requires a paid Apify account/API key this environment doesn't have. Not usable without provisioning. |

**Diagnosis:** the sandbox's outbound network policy denies CONNECT to all five
requested source domains at the proxy level (confirmed identical `403` /
`connect_rejected` responses via `/__agentproxy/status`, distinct from a site
returning 403 to a normal browser). This is an infrastructure/allowlist gap, not a
transient site outage — retrying the same hosts will not help. See lesson in
today's PRAXIS_INBOX entry for the recommended fix.

## Scoring rubric (unchanged, for reference — not applied today)

- 5: known-track-record member trading large size in liquid name
- 4: committee-relevant trade
- 3: cluster behavior (3+ members, same ticker, same week)
- 2: notable but standalone
- 1: noise

Auto-bump to 4+: homebuilder tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH,
MDC, MHO, TMHC) or Brand 9 client tickers.

## STOCK Act drift section

Not applicable this cycle — no filings were retrieved to check disclosure lag against
the 45-day statutory window.

## Recommendation for tomorrow's run

1. Request an egress allowlist exception for `efdsearch.senate.gov`,
   `disclosures-clerk.house.gov`, `www.capitoltrades.com`, `www.quiverquant.com`, and
   `unusualwhales.com` (or a documented proxy/API route to them), **or**
2. Provision an API key for a paid structured-data provider (e.g. the Apify
   Congress Trading API found during this run) that can be reached from this
   environment, **or**
3. Have an external process push a daily filings JSON/CSV into this repo (or an
   allowed host) that this task can read instead of live-scraping blocked sites.

Until one of those lands, this daily task will keep coming up empty rather than
publish invented trades.
