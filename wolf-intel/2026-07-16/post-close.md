# WOLF Post-Close Recap — 2026-07-16

Sourcing note: index/sector/earnings figures pulled via live web search against Yahoo Finance, CNBC, TheStreet, Bloomberg, Al Jazeera, FRED, and SEC 8-K filings at write time (post-16:00 ET). Cross-source figures diverged slightly on index closes (aggregation lag across outlets); the numbers below are the values that repeated across independent queries. Alpaca is not connected in this session — no live position/P&L pull was possible this run.

## 1. Index closes (SPX / NDX / RTY)

| Index | Change | Notes |
|---|---|---|
| S&P 500 | **-0.5%** | Broad risk-off in growth/tech |
| Nasdaq Composite | **-1.3%** | Second straight down day for semis |
| Dow Jones | **-0.3%** | Reversed off worse intraday lows |
| Russell 2000 | **-0.30%** to 2,967.22 | Small caps tracked the broader tape down, no standout divergence |
| 10Y Treasury | 4.55% (open 4.54%, high 4.61%) | Roughly flat — today was not a rates-driven move |
| WTI Crude | >$80/bbl, 4th straight up day | Driven by US-Iran escalation, not equity-market fundamentals |
| VIX | reported ~15.67 (-5%) | **Flag: this reading conflicts with a broad down tape — treat as unconfirmed, did not reconcile across sources** |

## 2. Sector heatmap

**Led:** Consumer Defensive +2.56%, Real Estate +1.97%, Healthcare +1.65%, Energy +0.62%, Consumer Cyclical +0.20%
**Lagged:** Technology -2.04%, Basic Materials -1.70%, Communication Services -1.20%, Industrials -1.14%, Utilities -0.18%, Financial Services -0.11%

Read: this was a rotation day, not a uniform selloff. Money came out of AI/semis/mega-cap tech and communication services and went into defensives, real estate, and healthcare. UnitedHealth +7% (earnings beat + raised full-year guidance) did a lot of the heavy lifting for Healthcare's sector print — single-name driven, not a sector-wide re-rate.

Semis/tech driver: Taiwan Semiconductor (TSM) posted a 77% annual earnings gain and still sold off >4%, on skepticism that AI hyperscalers slow capex. That dragged the Nasdaq for a second consecutive session — a valuation/sentiment story, not a fundamentals miss.

Geopolitical overlay: US carried out fresh airstrikes on Iranian missile facilities; reporting that the administration is weighing broadening operations, including a possible move on Kharg Island (Iran's main oil export terminal). That's the direct line to crude breaking back above $80 for a fourth straight session, reversing roughly a third of the Q2 post-truce decline.

## 3. Brand 9 client tickers (homebuilders)

| Ticker | Close | Change | Source confidence |
|---|---|---|---|
| DHI | $151.55 | +1.04% | confirmed |
| PHM | $125.39 | +0.67% | confirmed |
| LEN | $85.29 | +1.89% | confirmed |
| TOL | $153.19 | +0.43% | confirmed |
| KBH | — | no data surfaced | **gap — not found this run** |
| MTH | — | no data surfaced | **gap — not found this run** |
| TPH | — | no data surfaced | **gap — not found this run** |
| NVR | — | no data surfaced | **gap — not found this run** |
| BZH | — | no data surfaced | **gap — not found this run** |
| MDC | — | no data surfaced | **gap — not found this run** |
| MHO | — | no data surfaced | **gap — not found this run** |
| TMHC | — | no data surfaced | **gap — not found this run** |

Notable: the four confirmed builders were all green on a day the S&P was down half a point and Nasdaq was down over a point — that's real relative strength, consistent with Real Estate leading the sector heatmap (+1.97%). This reads like positioning ahead of tomorrow's Housing Starts/Permits release (see §5) rather than a rates call — the 10Y barely moved (4.54% → 4.55%), so this wasn't a duration-driven bid.

## 4. Pre-Market Brief signal post-mortem

**No WOLF Pre-Market Brief file for 2026-07-16 was found in this repo** (checked for pre-market/premarket-named files repo-wide — none exist). This is a genuine capture gap, not a "no signals fired" result — there is nothing to grade fired-vs-not-fired against. Flagging this as the lead error for today rather than fabricating a signal history that doesn't exist. Root cause and fix belong in the lesson below and in praxis-inbox.

## 5. After-hours earnings

**Netflix (NFLX)** reported after the close, call at 4:45pm ET:
- EPS $0.80 vs $0.79 est — **beat**
- Revenue $12.56B vs $12.587B est — **slight miss**, still +13% YoY
- Operating margin 33.4% vs 34.1% in Q2'25 — **margin compression**
- Stock **slid** in the after-hours session on a soft Q3 guide, despite the EPS beat — market trading the forward number, not the print.

No other confirmed 16:00-16:30 ET reporters surfaced in this run's search sweep; the daily earnings-calendar count (35 names) skewed pre-market.

## 6. Tomorrow's setup (2026-07-17)

**Overnight/Asia:** Nikkei 225 fell 2.6% Thursday to below 67,000 on renewed semis selling and Middle East escalation concerns; technicals show a negative RSI divergence against price — a caution flag for a continued uptrend.

**Scheduled releases (Friday):**
- **Housing Starts + Building Permits, 8:30am ET (June data)** — the single most relevant print for the Brand 9 book. May starts were 1,177,000 (-15.4% m/m), permits 1,413,000. This is also FOMC-relevant: a strong June/July housing read cuts the case for a July 29 cut; a weak one adds to it.
- Export/Import Price Index, Capacity Utilization, Industrial Production, Michigan Sentiment (prelim)

**Earnings (pre-market):** Travelers, Truist Financial, Fifth Third Bancorp, Regions Financial — a bank-heavy morning, useful cross-check against today's flat Financial Services sector (-0.11%).

**Tape character today:** rotation/risk-off-in-growth day, not a clean trend day and not a full risk-off day either — Dow only -0.3%, defensives and real estate green. Semis are the epicenter; everything else is downstream of that story plus the Iran/oil overlay.

**Levels vs. this morning's brief:** unable to grade — no pre-market brief on file (see §4).

**Tomorrow's key question:** Does the homebuilder bid survive an actual Housing Starts print, or was today's real-estate/builder strength just a pre-data positioning trade that unwinds on the number?

## 7. Positions / P&L

Alpaca is not connected in this session (no matching connector tool found). No positions or live P&L were pulled this run. The `wolf_live_data.json` file in this repo has a stale snapshot from 2026-06-24 — it was not used or represented as current.
