# WOLF Congressional Trading Watch — 2026-07-10

## Coverage note (read first)

Direct automated access to the primary sources was blocked for this run:

- `efdsearch.senate.gov` — 403 (search portal requires interactive session/CAPTCHA)
- `disclosures-clerk.house.gov` — 403
- `capitoltrades.com` — 403 (bot-protected)
- `quiverquant.com/congresstrading` — 403 (bot-protected)
- `unusualwhales.com/politics` — not directly fetchable
- Public mirror datasets (`house-stock-watcher`, `senate-stock-watcher` S3 buckets) — 403

Findings below were reconstructed from search-indexed snippets of secondary sources (MarketBeat instant alerts, Quiver Quantitative news headlines) that surfaced in the last 24-48h of indexing. **This is a partial sample, not a full sweep of all PTRs filed in the window.** Treat coverage as low-confidence/incomplete — real filing volume in a 24h period is typically 10-40+ transactions across both chambers, and this run surfaced 2 verifiable ones. No homebuilder-ticker or confirmed Brand 9 client-ticker filings were found beyond the one NVDA hit noted below.

## Filings found

### 1. Sen. Sheldon Whitehouse (D-RI) — NVDA — SELL
- Chamber/Party: Senate, Democrat
- Ticker: NVDA (NVIDIA Corporation)
- Transaction type: Sale
- Reported size bucket: $15,001–$50,000
- Transaction date: 2026-06-30
- Disclosure date: 2026-07-08
- Days to disclosure: 8 (within 45-day STOCK Act window — no drift)
- **Score: 4** — auto-bumped from baseline 2 (standalone, mid-size) because NVDA is a current Brand 9 portfolio holding (`wolf_live_data.json`). Whitehouse sits on Environment & Public Works and Budget, not a semiconductor-relevant committee, so no committee-relevance bump independent of the client-ticker flag.
- Source: MarketBeat instant alert (marketbeat.com/instant-alerts/sen-sheldon-whitehouse-sells-off-nvidia-corporation-nasdaqnvda-stock-2026-07-10/), corroborating search snippet.

### 2. Rep. John McGuire (R-VA) — BLK — SELL
- Chamber/Party: House, Republican
- Ticker: BLK (BlackRock, Inc.)
- Transaction type: Sale
- Reported size bucket: $1,001–$15,000
- Transaction date: 2026-07-07
- Disclosure date: 2026-07-08
- Days to disclosure: 1 (within 45-day window — no drift)
- **Score: 2** — standalone, smallest reporting bucket, no committee nexus identified (McGuire sits on Armed Services and Budget; BlackRock is not a defense contractor), not a homebuilder or confirmed client ticker.
- Source: MarketBeat instant alert (marketbeat.com/instant-alerts/rep-john-mcguire-sells-off-shares-of-blackrock-nyseblk-2026-07-10/).

## STOCK Act drift (>45 days between transaction and disclosure)

None found in this sample. (Caveat: given the partial-sample nature of this run, absence of a late filer here is not evidence there wasn't one filed in the last 24h — it means none surfaced in the accessible secondary-source snippets.)

## Cluster / committee-relevance check

- No 3+ member cluster on a single ticker observed in this sample.
- No Energy/Defense committee members observed trading oil majors or defense primes in this sample.
- No homebuilder-ticker (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC) filings found.

## Recommendation for tomorrow's run

Given today's near-total blockage of primary/aggregator sources, consider provisioning an authenticated data path (e.g., a licensed Quiver Quantitative / Unusual Whales API key, or a headless-browser fetch path with session cookies) rather than relying on unauthenticated WebFetch, which is being bot-walled across every major aggregator.
