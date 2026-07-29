# WOLF Post-Close Recap — 2026-07-29

## Pipeline status (read this first)

- **No pre-market brief found for today.** Searched the full repo history for a dated WOLF pre-market file (any `wolf-intel/` or `wolf-brief/` entry, any commit) — none exists for 2026-07-29, and none has ever existed. Signal post-mortem below is therefore **not possible** — there is nothing to grade against.
- **`wolf_live_data.json` is stale.** Last update timestamp in the file is `2026-06-24T13:43:00`, and the git history of "WOLF live data" auto-commits stops the same day. That's over a month with no live account/position sync into this repo. Treated as **not Alpaca-connected** for this run — no position/P&L pull attempted. Per standing instruction: "no positions tracked this run."
- Recommend Bobby check whether the WOLF pre-market job and the Alpaca live-data sync are still scheduled/running — this looks like a broken pipeline, not a quiet day.

## Index close, 2026-07-29

| Index | Close | Change |
|---|---|---|
| S&P 500 | 7,316.15 | -1.52% |
| Dow Jones | 51,594.14 | -1,153.18 pts / -2.19% (worst day since April 2025) |
| Nasdaq Composite | 24,442.94 | -1.74% (>10% off ATH) |
| Russell 2000 | ~2,948–2,953 | roughly flat/slightly higher — small-caps notably outperformed the mega-cap-tech-heavy indices today |

Driver: FOMC held rates unchanged (as expected) but the bond market read it as behind-the-curve on inflation — 10-year yield jumped +7bp to >4.67%. Separately, US forces intercepted an Iranian attack targeting American troops in the Middle East, pushing oil higher and adding an inflation-risk narrative on top of the rate story. Two shocks stacked on one tape.

## Sector color

- Leaders day-before (7/28) were Communication Services, Consumer Staples, Consumer Discretionary, Health Care, Financials — several at intraday ATHs.
- 7/29 flipped broad risk-off: Tech/semis led losses (chip sell-off "deepening" per coverage), Utilities and Financials also red intraday (notable — utilities acting like a rate-sensitive bond-proxy here, not a safe haven, consistent with the yield spike). Energy readings were mixed across sources (one showed -2.1% even as oil rose on the Middle East headline) — flagging this as unverified/contradictory rather than asserting a clean number.
- Confidence on exact sector-by-sector closing prints is **moderate** — pieced together from intraday snapshots across two article time-stamps, not a single end-of-day sector table. Treat directionally, not to the decimal.

## Brand 9 client tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

Could not independently verify today's exact closing prints for this basket — search results returned mixed-date price snapshots (e.g., LEN quoted anywhere from $81.66–$85.29 depending on source/timestamp) with no reliable same-day confirmation, and no usable ITB (home construction ETF) daily-change figure for 7/29 specifically.

Directional read: with the 10-year back above 4.67% and mortgage-rate-sensitive names already under pressure coming into today (NAHB builder confidence has been softening through July on affordability), today's yield spike is a headwind for the group. Recommend pulling exact closes from the broker/data feed directly rather than trusting this figure — this is the one section of tonight's recap I'd grade **low confidence**.

## After-hours earnings (16:00–16:30 ET reporters)

- **Microsoft (MSFT)** — beat. Azure FY26 revenue topped $100B for the first time; Productivity & Business Processes segment $37.85B (+14.3%) vs. $37.19B consensus. Coverage also flagged a gain tied to Microsoft's Anthropic stake. Tone of coverage: constructive/beat.
- **Meta (META)** — miss. EPS missed, revenue guide came in light, shares fell >5% in extended trading. Capex guidance range was narrowed but the top end of the range was held — market read that as still-elevated AI spend without the top-line to justify it.
- Framing across coverage: both stocks entered the print with ~95%+ "beat" odds priced by prediction markets, so FY27 capex commentary — not the quarter itself — was the actual swing factor. Meta's capex-vs-guide mismatch is what moved it; Microsoft's Azure/Anthropic story is what saved it.

## Tomorrow's setup (2026-07-30)

**Overnight / Asia:** Nikkei closed -1.49% at 61,434 on the 29th as tech selling spread into Asia; watch whether Thursday's Asia session extends that on the back of the Meta miss, or stabilizes on the Microsoft beat.

**Scheduled releases (8:30 ET Thursday):** Q2 GDP (annualized, +2.3% expected vs. +2.1% prior), Initial Jobless Claims (201K expected vs. 187K prior), Core PCE (MoM/YoY), Personal Income & Spending. This is a stacked macro morning — GDP + Core PCE together will do more to move rates than anything sector-specific.

**Earnings:** Apple and Amazon are the two big remaining mega-cap prints this week (coverage groups them with Meta/Microsoft as "the four" investors are watching) — expected after Thursday's close, so a Friday catalyst more than a Thursday one, but worth flagging now since AH tonight (Meta down, MSFT up) sets the tone for how the market prices the next two.

**Tape character:** Reversal/trend-down day — a hawkish-read Fed hold plus a geopolitical oil spike broke what had been a multi-day grind to highs (7/28 saw fresh ATHs in Health Care and Financials). Nasdaq >10% off its high is the headline number to watch — that's a meaningful drawdown, not noise.

**Tomorrow's key question:** Does GDP/Core PCE Thursday morning cool the bond selloff enough to stop the bleeding in rate-sensitive names (homebuilders, utilities), or does a hot PCE print confirm the "Fed is behind" read and extend the Wednesday reversal into a second down day?

## Sources
- [Stock Market Today (July 29, 2026): Dow tumbles 800+ points as Fed holds rates steady — TheStreet](https://www.thestreet.com/stock-market-today/stock-market-today-dow-jones-sp-500-nasdaq-updates-july-29-2026stock-market-today-july-29-2026)
- [Dow plunges, S&P 500/Nasdaq sink as yields rise on Fed's hawkish hold — Yahoo Finance](https://finance.yahoo.com/markets/live/stock-market-today-wednesday-july-29-dow-sp-500-nasdaq-082009165.html)
- [Microsoft Q4 earnings report 2026 — CNBC](https://www.cnbc.com/2026/07/29/microsoft-msft-q4-earnings-report-2026.html)
- [Meta Q2 earnings report 2026 — CNBC](https://www.cnbc.com/2026/07/29/meta-q2-earnings-report-2026.html)
- [Microsoft, Meta Earnings Face a Market Growing Skeptical of AI — Bloomberg](https://www.bloomberg.com/news/articles/2026-07-29/microsoft-meta-earnings-face-a-market-growing-skeptical-of-ai)
- [Russell 2000 Extends 2026 Lead as Tech Stocks Slip — Serrari Group](https://serrarigroup.com/russell-2000-extends-2026-lead-as-tech-stocks-slip/)
- [Core PCE Price Index, GDP, and jobless claims due Thursday — Investing.com](https://www.investing.com/news/stock-market-news/core-pce-price-index-gdp-and-jobless-claims-due-thursday-93CH-4821457)
- [Stock market news for July 28, 2026 — Yahoo Finance](https://finance.yahoo.com/markets/stocks/articles/stock-market-news-july-28-131500501.html)
- [Japan Stock Market Index — Trading Economics](https://tradingeconomics.com/japan/stock-market)
