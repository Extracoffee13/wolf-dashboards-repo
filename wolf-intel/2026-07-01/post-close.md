# WOLF Post-Close Recap — 2026-07-01 (16:00 ET)

## 0. Data quality note (read first)

This repo has no live market-data feed (no Alpaca API keys, no financial-data MCP tool wired up) and no prior **WOLF Pre-Market Brief** file exists anywhere in this repo's history for today or any prior date. Two consequences:

- **Index/equity closes below come from web search of financial news sites, not a terminal.** Sources disagreed with each other (a live-blog snapshot vs. an EOD wrap gave different S&P/Dow/Russell deltas for the same day). I used the source that reads as a genuine end-of-day wrap (TheStreet) as primary and flagged the conflict rather than silently picking a number.
- **Individual homebuilder ticker closes (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC) could not be verified for today.** Search returned stale (6/24, 6/29) prints, not 7/1 closes. Sector ETF proxies (XHB, ITB) and qualitative sector news are used instead — see §3.
- **No signal post-mortem is possible this run** — there is no Pre-Market Brief artifact in `wolf-intel/` or elsewhere to grade against. Flagged as a pipeline gap, not glossed over.
- **No Alpaca positions/P&L pull.** No Alpaca credentials or MCP tool are configured in this environment. `wolf_live_data.json` in repo root is a stale local snapshot (`last_updated: 2026-06-24T13:43:00`, a week old) — not used as if it were today's data.

## 1. Index closes (SPX / NDX / RTY)

Per TheStreet's July 1 wrap (treated as primary — reads as an EOD article, not a mid-session snapshot):

| Index | Close | % chg |
|---|---|---|
| S&P 500 | 7,483.23 | -0.22% |
| Nasdaq Composite | 26,040.03 | -0.66% |
| Dow 30 | 52,305.24 | -0.03% (intraday record 52,742.66) |
| Russell 2000 | — | **+0.46%** |

**NDX (Nasdaq 100) specifically was not separately confirmed** — Nasdaq Composite used as the closest verified proxy; Composite weakness attributed to chipmaker drag.

A second source (24/7 Wall St live blog) had S&P +0.15%, Dow +0.58%, Russell +0.59% — likely an earlier intraday snapshot from the same day, not reconciled with the close above. Treat the TheStreet figures as the closing print of record until confirmed via a terminal.

Context: Q2 2026 was the strongest quarter since 2020 — Dow +8.9%, S&P 500 +9.6%, Nasdaq +12.8% for H1 2026.

## 2. Sector heatmap

Best-supported reads: **financials led** (XLF cited ~+2.26% intraday) alongside communication services; **tech mixed to weak into the close**, dragged by chipmakers, consistent with Composite underperforming Dow/Russell. Breadth was positive (~65.7% of issues advancing per one source), which sits oddly next to the Composite's -0.66% — read as large-cap semis dragging cap-weighted tech lower while the average stock did fine. Energy, healthcare, staples, discretionary, industrials, materials, utilities, real estate sector-ETF levels (XLE/XLV/XLP/XLY/XLI/XLB/XLU/XLRE) were **not found** — do not treat their absence as "flat," treat it as unverified.

## 3. Brand 9 client tickers — homebuilders (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

**No individual 7/1 closes verified.** What's confirmed:

- **Sector ETFs (as of 6/30, one session stale):** XHB $115.21 (-0.30%); ITB -1.93%.
- **Fitch cut its 2026 homebuilder sector outlook to "deteriorating"** — single-family starts forecast revised to -4.5% (from prior +0.5%); new home sales forecast cut to -2.5% (from prior +1.5%).
- Five major builders' Q1 2026 earnings were down 20–50% YoY (reported earlier in the quarter, not new today).
- **Mortgage rates moved against the group today**: 30-yr fixed 6.39% APR (+3bps day, +11bps week), 15-yr 5.88%, 5/1 ARM 6.48% (NerdWallet).
- One-off: KB Home jumped from $52.73 → $61.51 on 6/24 after a FY26 guidance beat — unknown whether that gain held into 7/1; not reconfirmed.

**Read:** directionally soft-to-negative tape for the group today (rising rates, negative rating-agency revision, ITB down), but this is inference from ETF/macro proxies, not confirmed single-name prints. Flag for tomorrow: get a real data source wired in before making any B9-specific call with confidence.

## 4. Signals from today's WOLF Pre-Market Brief

**N/A — no Pre-Market Brief exists in this repo for 2026-07-01 (or any date).** Nothing to grade. This is the actual finding to act on: the Pre-Market Brief needs to write its calls to `wolf-intel/{date}/pre-market.md` (or equivalent) so Post-Close has something to mark against. Recommend fixing this before tomorrow's cycle — otherwise every Post-Close run repeats this gap.

## 5. After-hours earnings (16:00–16:30 ET window)

- **Constellation Brands (STZ)** reported Q1 FY2027 the evening of **June 30**, not July 1: EPS $3.43 vs. $3.21 est. (beat, +6.85%); stock reportedly rose >1% in reaction, carrying into the 7/1 session.
- **No AMC reporter was confirmed specifically for 7/1 16:00–16:30 ET.** A Benzinga earnings-calendar list for 7/1 (General Mills, FactSet, MSC Industrial, UniFirst, Bassett Furniture, Culp, Greenbrier, Franklin Covey) could not be fetched to confirm BMO/AMC split or results — do not assume any of these reported after today's close without confirming.

## 6. Tomorrow's overnight catalysts (into 2026-07-02)

- **Nonfarm Payrolls releases Thursday 7/2** (moved up a day ahead of the July 4th holiday) — consensus +172,000. This is the marquee catalyst, landing before Thursday's open.
- **ISM Manufacturing PMI (released today, covers June): 53.3%**, down 0.7pt from May's 54%; New Orders 56%; Prices Index fell sharply to 73% from 82.1% — a cooling-inflation-pressure read inside an otherwise still-expansionary print.
- **Asian markets / overnight futures for 7/2: not found** — searches returned only stale late-June data. Do not treat as "quiet" — treat as unverified.
- **Fed:** new Chair Kevin Warsh made his international debut at the ECB's Sintra Forum (with Lagarde, Bailey, Macklem); declined to pre-signal a July move, called inflation "too high" while acknowledging AI's disinflationary potential.
- **Oil/geopolitics:** reports of a provisional US–Iran peace deal; oil trading back near pre-war levels — read as risk-supportive if it holds.

## Tomorrow's setup

- **Tape character:** Mixed/rotational, not a clean trend day — small caps and financials firm (Russell +0.46%) while cap-weighted tech lagged on chip weakness. Positive breadth (~66% advancers) alongside a red Composite print is a rotation signature, not a risk-off one.
- **Levels:** No pre-market brief exists to check breaks/holds against — can't answer this sub-question this run.
- **Key question for 7/2:** Does the small-cap/financials bid survive the NFP print (consensus +172k, released Thursday morning instead of Friday because of the holiday), or does chip-driven tech weakness broaden out?
- **Secondary question:** Does the homebuilder tape stabilize, or does the Fitch downgrade + rising mortgage rates (6.39% 30-yr) keep leaning on ITB/XHB into next week?

## P&L / positions

Skipped — no Alpaca connection configured in this environment (no API keys, no MCP tool). `wolf_live_data.json` in the repo root is a stale snapshot from 2026-06-24 and is not represented here as current.

## Sources

- [TheStreet — Stock Market Today, July 1, 2026](https://www.thestreet.com/stock-market-today/stock-market-today-july-1-2026-nasdaq-futures-slip-after-strongest-quarter-since-2020)
- [24/7 Wall St — live blog, July 1, 2026](https://247wallst.com/investing/2026/07/01/stock-market-live-july-1-2026-sp-500-spy-lower-as-investors-wait-on-the-fed-and-fresh-economic-data/)
- [CNBC — Kevin Warsh at ECB Sintra Forum](https://www.cnbc.com/2026/07/01/kevin-warsh-ecb-forum-live-updates.html)
- [ISM Manufacturing PMI release, June 2026](https://www.prnewswire.com/news-releases/manufacturing-pmi-at-53-3-june-2026-ism-manufacturing-pmi-report-302814991.html)
- [NerdWallet — mortgage rates](https://www.nerdwallet.com/mortgages/mortgage-rates)
- [National Mortgage News — Fitch 2026 homebuilder outlook](https://www.nationalmortgagenews.com/news/2026-homebuilder-outlook-shifts-to-deteriorating-fitch)
- [Benzinga — earnings scheduled July 1, 2026](https://www.benzinga.com/news/earnings/26/07/60211381/earnings-scheduled-july-1-2026)
- [Constellation Brands IR — Q1 FY2027 results](https://ir.cbrands.com/news-events/press-releases/detail/340/)
- [FXStreet — Nonfarm Payrolls economic calendar](https://www.fxstreet.com/economic-calendar/event/9cdf56fd-99e4-4026-aa99-2b6c0ca92811)
