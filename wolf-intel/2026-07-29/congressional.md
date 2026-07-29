# WOLF Congressional Trading Watch — 2026-07-29

## Data access note (read first)

Direct pulls from the primary and aggregator sources named in this task's brief all returned HTTP 403 during today's scan:
`efdsearch.senate.gov`, `disclosures-clerk.house.gov`, `capitoltrades.com`, `quiverquant.com/congresstrading`, `unusualwhales.com/politics`, `congressstock.com`, `barchart.com` (politician insider trading page), and `investorlens.capital`. These portals are JS-rendered/bot-gated and rejected the fetch tool outright — this is a standing capability gap for this watch, not a one-day outage.

In place of a raw PTR pull, this brief is built from real, sourced news coverage (Benzinga, CNBC, NOTUS, Oklahoma Watch, 24/7 Wall St., Yahoo Finance, qz.com) reporting on filings that became public in the last ~1-7 days, with the newest coverage dated **2026-07-28**. Where an exact filing date isn't confirmed by a source, that is stated explicitly rather than estimated. No filing details below are fabricated — every line traces to a cited article. Treat size buckets and dates as reported by the source, not independently verified against the underlying PTR image.

---

## Scored filings

### 1. Sen. Alan Armstrong (R-OK) — Williams Companies (WMB) + ~700 other tickers
- **Chamber/Party:** Senate, Republican
- **Tickers:** WMB (Williams Companies, his former employer — he was CEO), plus Corning (GLW), FedEx (FDX), Home Depot (HD), Phillips 66 (PSX), Pfizer (PFE), and roughly 695 more individual line items
- **Transaction type:** Mix of buys and sells; two compliant trades were a June 24 WMB stock sale ($5M–$25M) and a June 22 WMB options sale (≥$250k). The bulk of the ~700 trades are March 2026 purchases/sales (~$7.66M bought, ~$17.37M sold) executed via a third-party direct-indexing advisor.
- **Size bucket:** 5M+ (aggregate); individual named sells (Corning, FedEx, Home Depot, Phillips 66, Pfizer) in the 50k-100k+ range
- **Days between transaction and disclosure:** March 2026 trades disclosed ~2026-07-24 → **~120+ days late**, more than double the 45-day STOCK Act limit. The two WMB trades (June 22/24) were disclosed within the window.
- **Score: 5** — sitting senator, former oil-major CEO, aggregate size well into 8 figures, in a highly liquid/well-known name (WMB), plus a live STOCK Act compliance story.
- **Source:** [Oklahoma Watch](https://oklahomawatch.org/2026/07/27/sen-alan-armstrong-violated-stock-act-with-700-tardy-stock-disclosures/), [NOTUS](https://www.notus.org/congress/sen-alan-armstrong-violated-stock-act-with-700-tardy-stock-disclosures), [Benzinga](https://www.benzinga.com/news/politics/26/07/60657916/new-senator-makes-700-stock-trades-ditches-old-oil-company-for-magnificent-seven)

### 2. SpaceX (SPCX) post-IPO cluster — 6 House members
- **Members:** Rep. William Timmons (R-SC), Rep. John McGuire (R-VA), Rep. Dan Meuser (R-PA), Rep. Gil Cisneros (D-CA), Rep. Jared Moskowitz (D-FL), Rep. John James (R-MI) — purchases by the members and/or immediate family
- **Chamber/Party:** House, mixed (5R/1D)
- **Ticker:** SPCX (SpaceX, post-IPO June 12, 2026)
- **Transaction type:** Buy (all six)
- **Reported size:** Combined ~$83k–$245k across all six; Timmons individually $50,001–$100,000 (June 15); Cisneros individually $1,001–$15,000 (June 18)
- **Days between transaction and disclosure:** Trades dated June 15–18, 2026; press coverage broke 2026-07-28, i.e. filed at/near the 45-day boundary (June 18 + 45 days ≈ Aug 2). **Not confirmed late**, but cutting it close — worth a recheck once official filing dates are visible.
- **Score: 4** (cluster of 6 members in the same ticker within a 6-day window **and** committee-relevant: Cisneros sits on House Armed Services, which oversees Pentagon/Space Force contracts with SpaceX; Timmons chairs the Oversight subcommittee on military & foreign affairs). No evidence of insider trading per CNBC's reporting — this is a conflict-of-interest optics story, not an allegation of illegality.
- **Source:** [CNBC](https://www.cnbc.com/2026/07/28/spacex-stock-congress-lawmakers-ipo-conflict-of-interest.html), [24/7 Wall St.](https://247wallst.com/investing/2026/07/28/congressman-who-oversees-military-contracts-bought-100000-in-spacex-stock-hes-not-the-only-one/), [qz.com](https://qz.com/congress-lawmakers-spacex-stock-ipo-conflict-interest-072826)

### 3. Sen. Tommy Tuberville (R-AL) — first 2026 disclosures
- **Chamber/Party:** Senate, Republican
- **Tickers:** Includes Tractor Supply (TSCO) and Lockheed Martin (LMT); Westinghouse Air Brake (WAB) sold one day later than the rest
- **Transaction type:** Sell (all disclosed transactions this batch)
- **Reported size:** Not specified in source coverage beyond "multiple" sales; treat as unconfirmed bucket
- **Trade dates:** June 8, 2026 (most), June 9, 2026 (WAB)
- **Days between transaction and disclosure:** Coverage is dated late July 2026 ("recently disclosed"); June 8 + 45 days ≈ July 23 — **likely at or slightly past the boundary**, not independently confirmed.
- **Score: 4** — committee-relevant on both counts: Tuberville sits on Senate Agriculture (Tractor Supply) and Senate Armed Services (Lockheed Martin, a defense prime).
- **Source:** [Benzinga](https://www.benzinga.com/news/politics/26/07/60537231/senator-who-opposes-ban-on-congress-trading-discloses-first-trades-of-2026-heres-what-hes-selling)

### 4. Paul Pelosi (spouse of Rep. Nancy Pelosi, D-CA)
- **Chamber/Party:** House (Pelosi), Democrat
- **Ticker:** AVGO (Broadcom)
- **Transaction type:** Buy — 20 call options, $800 strike
- **Reported size bucket:** 1M-5M
- **Trade window:** Disclosed between June 24 and July 1, 2026 (per Seven Lakes Research); exact trade date within that window not independently confirmed here.
- **Days between transaction and disclosure:** Not confirmed — flagging for follow-up rather than guessing.
- **Score: 5** — known-track-record filer (Pelosi household is the standard "score 5" example in this watch's own rubric), large size, highly liquid AI-adjacent mega-cap name.
- **Source:** [Seven Lakes Research](https://www.sevenlakesresearch.com/p/financial-moves-nancy-pelosis-husband-discloses-significant-trades)

---

## STOCK Act drift section (late-filed > 45 days)

- **Sen. Alan Armstrong (R-OK):** ~700 trades from March 2026 disclosed ~2026-07-24 — roughly **120+ days late**, the most significant compliance story in this scan. Aggregate value $3.24M–$16.05M; Armstrong's office attributed the March batch to a third-party direct-indexing advisor rebalancing his portfolio after entering the Senate on 2026-03-24 (filling Markwayne Mullin's seat). Two of his trades (June 22/24 Williams Companies sale + options sale) were filed within the 45-day window.
- **Sen. Tommy Tuberville (R-AL):** possible boundary-case lateness on June 8/9 trades disclosed in "late July" coverage — not confirmed past 45 days, flagged for recheck once exact filing dates are visible.

No homebuilder-ticker (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC) filings surfaced in today's scan.

No Brand 9 client-ticker matches were checked against a client list — this watch does not have access to a Brand 9 client ticker list to cross-reference; flag for AP if one should be supplied so future scans can check it directly.

## Legislative context (not a filing, but directly relevant to this watch)

The House passed the **Stop Insider Trading Act** on 2026-07-22 (232-198, 13 Democrats joining Republicans), which would bar members of Congress and immediate family from buying new individual stocks going forward, grandfather existing holdings with a 7–14 day advance-sale disclosure requirement, and raise penalties to $2,000 or 10% of the transaction. Reported as likely dead on arrival in the Senate. Worth tracking — passage would directly change what this watch monitors going forward.

## Coverage caveat

This scan is materially incomplete relative to the task's ask for an exhaustive last-24h PTR sweep — the primary portals (Senate eFD, House CHDP) and the aggregators (CapitolTrades, Quiver, Unusual Whales) all blocked automated access today. The items above are real and sourced but represent whatever surfaced in general news search, not a full census of yesterday's filings. Recommend: (1) a durable API key / authenticated route to at least one aggregator if this watch is meant to run daily, or (2) accepting news-search coverage as the standing method and noting the gap each day rather than re-attempting the same blocked URLs.
