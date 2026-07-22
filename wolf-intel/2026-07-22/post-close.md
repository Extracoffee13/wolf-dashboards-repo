# WOLF Post-Close Recap — 2026-07-22

## 1. Index close

| Index | Close | Chg |
|---|---|---|
| S&P 500 | 7,498.96 | -0.14% |
| Nasdaq Composite | 25,690.90 | -0.57% |
| Dow Jones | 52,218.58 | -0.01% (flat) |
| Russell 2000 | 2,965.02 | +0.77% |

Source: CNBC/Yahoo Finance live market wraps for July 22, 2026.

Read: large-cap tech was the soft spot, small caps decoupled to the upside. Not a trend day — a rotation day. Dow flat, SPX/Nasdaq red, RTY green is a dispersion signature, not a directional one.

## 2. Macro driver: oil, not earnings, moved the tape intraday

- Brent crude +3.4% to ~$94.13/bbl, WTI +3.0% to ~$86.85/bbl — both six-week highs.
- Driver: 11th consecutive night of US strikes on Iranian military facilities, Strait of Hormuz supply-disruption fears, Houthi threats to Red Sea shipping, and a reported strike on the Caspian Pipeline Consortium terminal in the Black Sea.
- This is the dominant macro story of the session and the reason Energy led while everything rate/growth-sensitive lagged.

## 3. Sector heatmap

**Led:** Energy (+2.83%) — gas utilities +2.9%, precious metals +2.9% (gold/silver equities caught a geopolitical + safe-haven bid alongside the oil spike).

**Lagged:** Information Technology (-2.12%) — application software -2.8% (single names: Pegasystems -16.2%, UiPath -12.8%, unrelated idiosyncratic hits stacked on top of sector weakness). Education & training services also soft (-2.6%).

5 of 11 S&P sectors closed higher, 6 lower — a genuinely mixed tape, consistent with the index dispersion above.

## 4. Brand 9 client tickers — homebuilders

| Ticker | Note |
|---|---|
| LEN | +1.89% to ~$85.29 |
| DHI | +1.04% to ~$151.55 |
| PHM | +0.67% to ~$125.39 |
| TOL | +0.43% to ~$153.19 |
| KBH | No confirmed print this session — data not available via research pass |
| MTH, TPH, NVR, BZH, MDC, MHO | No confirmed same-session data found — flagging as a data-source gap, not a "no move" |
| TMHC | Still under Berkshire Hathaway's ~$8.5B all-cash acquisition (deal announced early June 2026) — trades near deal terms, not on daily fundamentals |

Homebuilders as a group held a modest bid despite the SPX/Nasdaq red day — consistent with the Russell 2000 strength and with reporting that 37% of builders cut prices in June (margin-for-volume trade), i.e., rate-sensitive cyclicals catching a relative bid even as tech de-risked into two mega-cap prints.

**Data-quality note:** could not source confirmed closing prints for KBH, NVR, BZH, MDC, MHO, MTH, TPH tonight — free-data search tooling did not surface same-day closes for the full client list. This is a real gap, not an "all quiet" — worth building a direct data feed for the full B9 client list rather than relying on search.

## 5. Signal post-mortem — WOLF Pre-Market Brief

**No same-day WOLF Pre-Market Brief was found in this repository.** Searched for a `wolf-intel/2026-07-22` pre-market file, git history, and any brief dated today — none exists. `wolf_live_data.json`'s "ACTIVE SIGNALS — TODAY" block (TSLA short, NFLX long) is stale, dated to the April 14, 2026 dashboard snapshot, not today.

Consequence: there is nothing to grade signals against for today's session. This is itself the finding — the pre-market → post-close pipeline has a gap where the morning brief either isn't being written to this repo, or isn't being written to a discoverable path. Recommend fixing the pre-market brief's write path before next session so post-close has something real to score.

No Alpaca connector is available in this session (checked via connector list — empty). Per the last committed `wolf_live_data.json` snapshot: PAPER mode, $100,000 cash, 0 open positions, 0 trades — but that snapshot is from April 2026 and cannot be trusted as today's live state. **No positions tracked this run.**

## 6. After-hours earnings — big print night

- **GOOGL (Alphabet)** — beat on top and bottom line. EPS $9.11 vs. ~consensus, revenue $119.8B vs. $116.9B expected. Cloud revenue +82% YoY. Net income +298% YoY, driven substantially by a ~$99B mark-up on Alphabet's ~14% stake in Anthropic (booked as other income, not operating profit). **Shares reacted flat in the immediate AH print** — market read through the one-time equity gain to core operating results.
- **TSLA (Tesla)** — reported after the close, earnings call at 5:30pm ET. Options market had priced a 6-8% swing. Q2 deliveries were already known (480,126 units, record, +~25% YoY) and largely priced in three weeks ago; the swing variable was auto gross margin, capex, and management commentary on autonomy/Robotaxi/Optimus and FY26 guidance. **Could not confirm the actual print or AH stock reaction** — available sources were still showing pre-earnings preview content as of this scan, meaning the report likely dropped after or right at this research window closed. Flag as unresolved; check first thing tomorrow.
- Also reporting AH: IBM, TXN (Texas Instruments), NOW (ServiceNow), CSX — no confirmed reaction data captured this pass.

## 7. Tomorrow's setup — 2026-07-23

- **Asia open:** Nikkei 225 closed -0.18% at 66,115 today, semiconductor rally fading into the close, investors cautious ahead of GOOGL/TSLA. Notable movers: Kioxia +5.3%, Taiyo Yuden +6.7%, Murata +4% (up); Tokyo Electron -0.9%, SoftBank -0.8%, Fast Retailing -2.8% (down). Watch whether GOOGL's cloud beat / Anthropic mark-up story lifts Asia tech names in the overnight session.
- **Scheduled US data:** Weekly Initial Jobless Claims (Thursday standard release) — last print was 208K (11-week low), a beat/steady number would reinforce the soft-landing case even as oil spikes.
- **Pre-market earnings (Thursday, July 23):** heavy day — Cleveland-Cliffs (CLF), Nokia (NOK), RTX, Lockheed Martin (LMT), American Airlines (AAL), T-Mobile (TMUS), Blackstone (BX), STMicroelectronics (STM), Freeport-McMoRan (FCX), Dow Inc. (DOW), among ~166 companies reporting.
- **Geopolitical catalyst still live:** US strikes on Iran continuing (11 consecutive nights as of today), no near-term talks per Trump comments — oil trajectory is now the single biggest swing factor for risk sentiment into tomorrow.

### Tape character
Rotation/dispersion day, not a trend day: mega-cap tech de-risked into two binary AH prints while energy/small-cap/cyclicals (including homebuilders) caught a bid. No morning-brief levels exist to check "broken vs. held" against — noted as pipeline gap above.

### Tomorrow's key question
**Does GOOGL's cloud beat stabilize mega-cap tech into the open, or does the Iran-driven oil shock override it and pull the tape risk-off regardless of earnings quality?**
