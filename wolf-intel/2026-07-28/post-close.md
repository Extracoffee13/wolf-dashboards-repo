# WOLF Post-Close Debrief — 2026-07-28

Generated post-16:00 ET. Sourced from public wire/market data (CNBC, Bloomberg, TheStreet, Yahoo Finance, 24/7 Wall St.) via web search — no direct exchange or Alpaca feed was available this run (see Data Gaps below). Treat individual price prints as directional/approximate, not tick-accurate.

## 1. Index close

| Index | Close | Change |
|---|---|---|
| S&P 500 (SPX) | ~7,428.78 | +0.21% |
| Nasdaq Composite | ~24,876–24,932 | -0.2% |
| Nasdaq 100 (NDX) | — | -1.8% (now ~10% off its record high — testing correction territory) |
| Russell 2000 (RTY) | ~2,954.15 | +0.21% |
| Dow Jones | — | + (rallied on earnings, falling oil) |

Note the split: cap-weighted Nasdaq 100 got hit hard by semis, while breadth (SPX, RTY, 7 of 11 S&P sectors) was actually fine. This was a rotation day, not a broad risk-off day.

## 2. Sector heatmap

**Led:** Consumer Staples (XLP) +3.7%, Health Care (XLV) +3.0%, Materials (XLB) +2.2%
**Lagged:** Technology (XLK) -3.8% (Philadelphia Semiconductor Index / SOX -6.4%), Energy (XLE) -2.1% (falling oil prices), Utilities (XLU) -1.3%

7 of 11 S&P sectors closed green. The laggard is concentrated and narrative-driven (chips), not systemic.

**Why tech/semis got hit:** Two compounding stories —
1. A Chinese state-backed firm reportedly began mass production of immersion DUV lithography machines, reviving fears that China closes the chipmaking-equipment gap faster than priced in.
2. AI-capex sustainability doubts deepened after Nvidia's ~$750B in disclosed AI-infrastructure deals stoked worries about debt-funded buildout. Sentiment on "the AI trade" has flipped skeptical — Janney's Mark Luschini called it "something of a one-way trade... getting sold unmercifully."

Spillover: SK Hynix -14.65% and Samsung -13%+ in the Asia session (Kospi briefly halted trading); Micron, Nvidia, AMD, Broadcom, Marvell, Semtech all fell in sympathy stateside.

## 3. Brand 9 client tickers (homebuilders)

Data available only for a subset via search; treat as directional.

| Ticker | Close (approx) | Change | Note |
|---|---|---|---|
| DHI | ~$151.55 | +1.04% | Largest-cap builder; beneficiary of rotation out of tech |
| LEN | ~$85.29 | +1.89% | Best mover in the group today |
| PHM | ~$125.39 | +0.67% | |
| TOL | ~$153.19 | +0.43% | |
| MTH | — | — | No reliable data returned this run |
| TPH | — | — | No reliable data returned this run |
| NVR | — | — | No reliable data returned this run |
| BZH | — | — | No reliable data returned this run |
| MDC | — | — | No reliable data returned this run |
| MHO | — | — | No reliable data returned this run |
| TMHC | — | — | No reliable data returned this run |

**Read:** Builders traded as a "rotation beneficiary," not on housing-specific news today — money moving out of semis/tech into rate-sensitive, economically-linked names. This is a sentiment/flow move, not a fundamentals move; the earlier (July ~9) homebuilder pop was a distinct, one-off event tied to the 21st Century ROAD to Housing Act clearing Congress and shouldn't be conflated with today's action. Volume data was not obtainable through search this run — flagged as a gap.

## 4. Signal post-mortem — today's WOLF Pre-Market Brief

**No Pre-Market Brief for 2026-07-28 was found in this repo** (no `wolf-intel/2026-07-28/pre-market*.md` or equivalent, and `wolf-brief/` contains only the original launch materials, no dated daily posts). This means:
- No signals to grade fired/didn't-fire against.
- This is itself the finding: the daily posting cadence promised in the launch post (Pre-market 09:00 / Congressional 09:30 / Consulting 11:00 / Post-close 16:30 ET, every weekday) has not been running. Today's post-close is being generated with no morning counterpart to reconcile against.
- **Action item:** either the Pre-Market Brief generation task is not scheduled/configured, or it ran and was never committed to this repo. Worth checking the automation before tomorrow.

## 5. After-hours earnings

Search results returned a mixed-date cluster of large reporters for the July 27–28 window: Boeing (BA), Coca-Cola (KO), Enphase (ENPH), Ford (F), UPS, Visa (V), Rithm Capital (RITM), PayPal (PYPL), Tilray (TLRY), Bloom Energy (BE) — some before-market, some after. Directionally, BA/KO/PYPL prints were reported as positive reactions. **Caveat:** source snippets did not cleanly separate "today" (7/28) from adjacent days, and no Brand 9 client tickers reported this window (homebuilders aren't earnings-cluster names right now). No high-confidence AH move data to report for the specific 16:00–16:30 ET window requested — flagged as a gap rather than guessed.

## 6. Tomorrow's overnight catalysts (Wed 2026-07-29)

- **FOMC decision, 2:00 PM ET / Powell-successor Kevin Warsh press conference 2:30 PM ET.** This is the whole ballgame tomorrow. Fed funds futures still favor a hold (~64%), but hike odds have repriced sharply — from ~10.7% two weeks ago to ~38% as of July 24 — one of the fastest repricings in recent memory. Warsh, chairing only his second meeting, is viewed as a hawk.
- **Earnings:** ~299 reports scheduled for July 29, including Microsoft (MSFT) and Meta (META) — two of the Mag 7 — reporting this week (Wed/Thu cluster with Apple and Amazon).
- **Asia:** expected to open cautious/quiet after today's chip-driven rout (Kospi halt, Samsung/SK Hynix losses); watch for continuation or stabilization in Korean semis as an early read on risk appetite before the US session.

## 7. Tomorrow's setup

- **Tape type:** Rotation day, not a trend or broad reversal day. Narrow, concentrated tech/semis weakness; broad breadth intact (7/11 sectors green, small-caps and SPX both positive).
- **Levels vs. morning brief:** N/A — no morning brief exists to check against (see Section 4).
- **Key levels to watch:** Nasdaq 100 sits ~10% off its high — a close below that threshold would confirm a formal correction and could accelerate de-risking flows into tomorrow's Fed decision.
- **One-line key question:** *Does Wednesday's Fed decision + Warsh's tone collide with the Microsoft/Meta earnings cluster to reignite the chip-stock rout — or does a hold plus a less-hawkish-than-feared press conference spark a relief bounce back into tech?*

## 8. Positions / P&L

No Alpaca (or other broker) MCP connector is available in this session — could not pull live positions or today's realized/unrealized P&L. `wolf_live_data.json` in this repo contains a portfolio snapshot, but it is stale (last updated 2026-06-24T13:43 — over a month old) and should not be read as today's numbers. **No positions tracked this run.**

## Data Gaps (explicit)

- No live broker/Alpaca connection this run.
- No Pre-Market Brief exists for today to grade signals against.
- Individual close prints for MTH, TPH, NVR, BZH, MDC, MHO, TMHC not retrievable via search this run.
- Volume data not retrievable via search this run.
- AH earnings reaction data for the specific 16:00–16:30 ET window is low-confidence; reported as a gap rather than fabricated.
