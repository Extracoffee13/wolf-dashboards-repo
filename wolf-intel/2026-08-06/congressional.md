# WOLF Congressional Trading Watch — 2026-08-06

## Data access note (read first)

This run hit hard access limits and the list below is **not a complete 24h scan**. Every direct fetch to a primary or aggregator source returned HTTP 403:

- Senate eFD (`efdsearch.senate.gov`) — 403
- House CHDP (`disclosures-clerk.house.gov`) — 403
- CapitolTrades (`capitoltrades.com`) — 403
- Quiver Quantitative (`quiverquant.com/congresstrading`, news feed) — 403
- CongressStock, Trendlyne, InsiderFinance, AltIndex trackers — 403

These sites appear to block the fetch tool's request signature outright (not a login wall — even public list pages 403'd). No Unusual Whales access was available either. What follows is reconstructed from web-search snippets (mostly Benzinga writeups) that had already indexed specific filings — it is **not exhaustive** and should not be read as "these are the only trades filed this week." Search did not surface any filings freshly reported in the literal last 24h (Aug 5–6); the two verifiable, dated filings below were reported Aug 3.

No Brand 9 client-ticker list exists in this repo, so that auto-bump rule could not be evaluated — flagging as a gap, not a "none found."

## Filings found (verifiable, with dates)

### 1. Rep. April McClain Delaney (D-MD-06, House)
- **Ticker:** BWXT (BWX Technologies)
- **Transaction:** Buy
- **Size bucket:** 100k–250k to 500k–1M (reported range $200,032–$900,000 spans buckets — Benzinga did not give the exact sub-bracket)
- **Transaction date:** 2026-07-24
- **Disclosure date:** 2026-08-03
- **Days to disclose:** 10 (within 45-day STOCK Act window)
- **Score: 2/5** — Sizeable buy, but this session could not confirm Delaney sits on a committee with BWXT nexus (BWXT is a naval-reactor/DOE nuclear contractor). Not a homebuilder or confirmed client ticker. Standalone, no cluster corroboration found. Scored conservatively pending committee-assignment confirmation.

### 2. Sen. Sheldon Whitehouse (D-RI, Senate)
- **Ticker:** LOW (Lowe's Companies)
- **Transaction:** Sell
- **Size bucket:** 1k–15k
- **Transaction date:** 2026-07-20
- **Disclosure date:** ~2026-08-03
- **Days to disclose:** ~14 (within 45-day window)
- **Score: 1/5** — Small size, standalone, no committee nexus (Whitehouse sits on Judiciary/Budget/EPW/Finance; no clear Lowe's tie).

## Unconfirmed / lower-confidence leads (context only, not scored)

Surfaced via search but without solid date/size confirmation this run — carrying forward as watch items, not filings:

- **Rep. David Taylor** — reported buys in IBP (Installed Building Products) and CVX (Chevron). IBP is building-products-adjacent but is *not* on the homebuilder auto-bump list (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC). CVX would be committee-relevant if Taylor sits on Energy — unconfirmed.
- **Rep. Greg Stanton** — search indicated new filed trades, no ticker/size/date recovered.
- **SpaceX cluster** (late June/early July 2026, so outside this 24h window but relevant standing pattern): at least 6 House members disclosed SpaceX purchases within days of its IPO, including Rep. Gil Cisneros ($1,001–$15,000, txn 6/18, filed 7/2) — Cisneros sits on House Armed Services, which oversees Pentagon/Space Force contracts. This is the kind of committee-relevant cluster the daily scan is built to catch; noting it since it's still live in search results and may resurface in follow-on filings.

## STOCK Act drift (>45 days)

None found among the confirmed filings above (10 and ~14 days respectively). No visibility into the broader filing set to check for outliers this run.

## Homebuilder ticker check

No confirmed filings this run touch LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, or TMHC.

## Brand 9 client ticker check

Could not run — no client-ticker list found in this repo. Needs to be added (e.g. `wolf-intel/config/client-tickers.md`) for future runs to evaluate this rule.

## Recommendation for tomorrow's run

The 403s were consistent across every source in the brief, including plain list pages with no auth wall — worth checking whether the fetch tool's outbound requests need a different user-agent/referrer, or whether these sites categorically block this environment's egress. Until resolved, this feed will keep under-reporting.
