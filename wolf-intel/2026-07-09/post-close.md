# WOLF Post-Close Recap — 2026-07-09 (Thursday)

## 1. Index closes

| Index | Close | % Chg |
|---|---|---|
| S&P 500 | 7,543.64 | +0.81% |
| Nasdaq Composite | 26,206.89 | +1.30% |
| Russell 2000 | — | +1.22% |
| Dow Jones | 52,487.44 | +0.27% (+139.02 pts) |

Broad-based green tape despite an active-conflict headline day. Small caps (RTY +1.22%) and growth (NDX +1.30%) outran the Dow, which is the classic risk-on skew — but see the geopolitical context below before calling this a clean trend day.

Sources: [TheStreet — July 9 close](https://www.thestreet.com/stock-market-today/stock-market-today-dow-jones-sp-500-nasdaq-updates-july-9-2026), [CNBC live blog](https://www.cnbc.com/2026/07/08/stock-market-today-live-updates.html)

## 2. Sector heatmap

**Led:**
- Semiconductors / Tech — SMH (VanEck Semiconductor ETF) +2.5%. Micron (MU) +4.5%, Sandisk (SNDK) +7.6%. This was the single biggest driver of the Nasdaq's outperformance.
- Homebuilders (ITB) +1.58% at the ETF level — but see the client-ticker dispersion in Section 3. This was not a uniform sector move.

**Lagged / mixed:**
- Energy — crude fell even as the U.S.-Iran conflict escalated: WTI -1.2% to $72.64/bbl, Brent -1.32% to $76.99/bbl. Counterintuitive given fresh U.S. strikes and Iranian retaliation against Bahrain/Kuwait — reads as the market fading the supply-disruption premium, possibly on the Macquarie-style view that this flares and fades rather than closing the Strait of Hormuz.

Note: I do not have a full 11-sector GICS breakdown confirmed to today's date from available sources this run (search results kept returning July 8 sector data). Treat semis-led / energy-soft as the confirmed read; do not over-specify beyond that.

## 3. Brand 9 client tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

| Ticker | Close | % Chg | Note |
|---|---|---|---|
| DHI | $150.16 | +1.11% | |
| TOL | $148.29 | +1.87% | Best performer in the group |
| PHM | $123.94 | +0.81% | In line with SPX |
| LEN | $84.11 | +0.62% | |
| NVR | $6,693.69 | ~flat | Mega-price, low-float name; effectively unchanged |
| TMHC | $71.78 | -0.24% | |
| KBH | $58.68 | -1.84% | |
| MTH | $78.31 | -1.99% | Worst performer in the group |
| TPH | — | — | No independently confirmed quote this run |
| BZH | — | — | No independently confirmed quote this run |
| MHO | — | — | No independently confirmed quote this run |
| MDC | **DELISTED** | — | MDC Holdings was taken private by Sekisui House; deal completed April 19, 2024. It no longer trades under "MDC." This ticker should be dropped from the client list — carrying it is a standing data-quality error I'm correcting now rather than repeating silently. |

**Read:** the ITB +1.58% headline number masks a real split. DHI/TOL/PHM/LEN (the larger, more geographically diversified builders) caught a bid; KBH and MTH (smaller-cap, more regionally concentrated) fell on the same day. That's a large-cap-vs-mid-cap divergence inside the sector, not a sector-wide re-rate. Worth tracking whether it resolves tomorrow.

Data-source caveat: no Alpaca/FMP live quote feed was reachable in this session (see Section 6) — these are web-sourced closing quotes, not a terminal pull. Three of twelve tickers (TPH, BZH, MHO) could not be independently confirmed and are left blank rather than guessed.

## 4. Signal post-mortem — today's WOLF Pre-Market Brief

**No pre-market brief for 2026-07-09 was found in this repository** (checked `wolf-intel/`, `wolf-brief/`, and the full repo for any pre-market artifact dated today — none exists). There is nothing to grade against today's close.

This is itself the finding: the pre-market → post-close grading loop has a gap. Either the pre-market brief was never generated/committed today, or it lives outside this repo. Flagging as a process lesson below — a debrief that can't check its own morning call is a broken loop, not a clean one.

## 5. After-hours earnings (16:00–16:30 ET window)

- **Levi Strauss (LEVI)** — beat on both lines (adj. EPS $0.28 vs. $0.24 est.; revenue $1.56B vs. $1.52B est.), raised full-year guidance and the dividend — and still fell ~5.5% AH. Beat-and-raise-but-sell is a classic "priced in" or guidance-quality reaction; worth watching how it trades tomorrow morning.
- **PepsiCo (PEP)** — reported this morning, not in the AH window: adj. EPS $2.20 vs. $2.21 est. (slight miss), revenue $24.18B vs. $23.95B est. (beat), reaffirmed full-year outlook. Included for completeness since it was the day's headline consumer print.
- Other AH movers referenced in search (AZZ Inc beat and popped, AstraZeneca fell ~8% on a failed Wainua trial) are non-B9-relevant and noted only for completeness, not analyzed further.

I did not get a clean, complete list of all 21 companies that reported today — earnings-calendar sites (Yahoo, Seeking Alpha, Earnings Whispers) were not fetchable directly this session (403s); the above is what surfaced via search snippets.

## 6. Alpaca / positions

No Alpaca connector was available in this session (checked `ListConnectors` — not present; FMP is connected at the org level but not enabled in this chat). The only portfolio data in-repo is `wolf_live_data.json`, last updated 2026-06-24 and holding a materially different book (ACN, AMD, CRM, JPM, MDT, MSFT, NOW — not the B9 homebuilder client list), so it is stale and not representative of "today." **No positions tracked this run.**

## 7. Tomorrow's setup (2026-07-10, Friday)

- **Tape character today:** trend-up day on the surface (SPX/NDX/RTY all green, Dow lagging), but the internals (oil falling on an escalation headline, homebuilders splitting large-cap vs. mid-cap) suggest a market that's rallying through the geopolitical noise rather than confirming a clean risk-on trend. Call it a "grind up, don't trust it yet" day.
- **Levels:** no pre-market brief exists to check levels broken/held against (see Section 4).
- **Overnight catalysts into Friday:** the U.S.-Iran conflict is the live wildcard — U.S. struck Iran again to keep the Strait of Hormuz open, Iran hit back at U.S.-linked sites in Bahrain and Kuwait. Asian markets were mixed on this (steep losses in Tokyo/Seoul, gains in Taipei/Hong Kong) heading into today's session; watch for a repeat or an escalation overnight. No major U.S. macro releases are scheduled for Friday July 10 (this week's FOMC minutes and jobless claims are already behind us); earnings season proper doesn't start until the following week, so headline risk is almost entirely geopolitical, not data-driven.
- **Tomorrow's key question:** does the large-cap/mid-cap homebuilder split (DHI/TOL/PHM/LEN up, KBH/MTH down) resolve into a real trend, or was ITB's +1.58% just beta to a broad risk-on tape that fades if Iran headlines worsen overnight?

## 8. Lessons / process notes

1. The pre-market → post-close signal loop is broken today: no pre-market brief was found to grade. Fix before tomorrow's pre-market run, or this debrief keeps having nothing to post-mortem.
2. MDC Holdings has been delisted (private since April 2024) and should be removed from the standing B9 client-ticker list.
3. Direct fetches to Yahoo Finance, CNBC, and TheStreet were blocked (403) this session; relied on WebSearch snippet aggregation instead. Three of twelve client tickers (TPH, BZH, MHO) could not be independently confirmed as a result — flagged rather than guessed.
