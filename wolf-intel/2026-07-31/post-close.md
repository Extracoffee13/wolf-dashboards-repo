# WOLF Post-Close Recap — 2026-07-31

*Generated post-16:00 ET. Sourced via web search (no live Bloomberg/IEX tick feed in this run) — see Data Confidence note at bottom.*

## 1. Index closes

| Index | Close | Chg % | Read |
|---|---|---|---|
| S&P 500 (SPX) | ~7,467 | +0.4% | Fourth straight winning month for the Dow; Friday capped a volatile July |
| Nasdaq Composite | — | +1.1% (led the tape) | Best of the three majors, tech/chip-driven |
| Russell 2000 (RTY) | — | +1.37% (per earlier-week read) | Small caps continue to lead 2026 |
| Dow Jones | — | +0.38% | Lagged Nasdaq, dragged by AAPL |

Reporting note: sources disagreed on the exact SPX tick (+0.4% to +0.7% across outlets) — treating +0.4% (Trading Economics-sourced) as the anchor number since it was corroborated twice. NDX/RTY exact closing prints were not independently verified tick-by-tick this run; direction and magnitude are corroborated across 2+ sources each. Flagging this as a data-source gap, not fudging the number.

## 2. Sector heatmap

**Led:** Consumer Discretionary +6.07% (Amazon Q2 beat carried the sector single-handedly). Technology/Semis rallied hard — SOX +8.2%, snapping a five-day losing streak; AMAT +15%, MU +18.4%, MSFT +15.5% (biggest single-day gain in company history, off Wednesday's Q4 beat/Azure growth/$37B AI revenue run-rate).

**Lagged:** Materials -2.71%, worst sector on the day. Broader market saw intraday chop as chip producers gave back some gains and a fresh leg up in long-end yields pressured rate-sensitive groups. Healthcare mixed-to-flat (XLV +0.05%) despite a strong ABBV print lifting sentiment.

**Cross-current:** 10-year Treasury yield surged to a multi-year high (4.737% intraday) — bond pressure was the session's second-order story under the AI-earnings euphoria, and it's the thing to watch bleeding into next week.

## 3. Brand 9 client tickers — LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

No independent tick-by-tick close/volume pull for the full 12-name basket this run — the search layer surfaced sector/ETF-level and single-name commentary but not a clean same-day closing table for all 12. Logging this as a gap rather than guessing individual closes.

What we do have with reasonable confidence:
- **LEN** — traded in an $82.95–$86.00 range as of Thursday 7/30; no confirmed Friday close.
- **DHI** — flagged by BofA as top homebuilder pick (Buy), seen as best-positioned into 2H26.
- **LEN** — BofA at Underperform; **PHM** — BofA Neutral.
- Sector-wide: builders staged their strongest session in months last week off a housing-affordability bill clearing Congress — that tailwind is still the dominant narrative.
- Sector-wide headwind: effective tariff rate on construction materials now >27%, adding an estimated ~$11,000 to the cost of a typical new home — this is the bear case analysts keep coming back to for 2H26.

**Action item for tomorrow's pre-market brief:** wire a direct quote pull (Alpaca market data or another live feed) for the full 12-ticker basket so this section isn't sourced secondhand. This is today's clearest process gap.

## 4. Pre-Market Brief signal post-mortem

No WOLF Pre-Market Brief was found committed to this repo for 2026-07-31 (checked `wolf-intel/`, `wolf-brief/`, repo root — nothing dated today prior to this run). Can't grade signals that were never published. Two possibilities: (a) the brief didn't run today, or (b) it ran but wasn't committed to this repo.

**Named as an error, not smoothed over:** if the AM brief is supposed to fire daily per the WOLF Command Center commitments (09:00 ET pre-market, 16:30 ET post-close), today's AM leg didn't land where this recap could find it. Flagging for the scheduling/cron layer to check the pre-market job actually ran and committed its output.

## 5. After-hours earnings (16:00–16:30 ET window)

The week's headline AH prints landed Wed (MSFT) and Thu (AMZN, AAPL), not Friday — Friday afternoon prints are historically thin since few companies report into a weekend. Recap of the week's moves still setting today's tape:
- **MSFT** (Wed AH, reacted Thu/Fri): beat, Azure strength, $37B AI revenue run-rate; stock +15.5%, biggest single-day gain in company history.
- **AMZN** (Thu AH, reacted Fri): beat, stock +8–13% depending on snapshot (AH pop moderated some into the cash session) — this was the single biggest driver of today's Consumer Discretionary leadership.
- **AAPL** (Thu AH, reacted Fri): beat on EPS/revenue (EPS $1.91 adj vs $1.89 est; rev $109.42B vs $108.65B est) but weak forward guidance citing supply constraints — stock fell today (~-7% on the week's reaction), the one true after-hours miss-on-guidance story, and the reason Dow lagged Nasdaq.
- Earnings Whispers listed ~41 companies reporting AMC today (7/31); no consolidated free list of names/results was retrievable this run (login-gated calendar).

## 6. Tomorrow's setup — Monday, August 3, 2026

Markets are closed the weekend (Sat Aug 1 confirmed); next session is Monday.

**Overnight/weekend catalysts:**
- Asia opened firm Friday tracking the AI-rally handoff (Nikkei +3.78% Friday, semis-led — Sumco +17.5%, Advantest +15.7%). Watch whether that follow-through survives the weekend gap.
- Monday's data: S&P Global Manufacturing PMI (flash, 9:45 ET), Construction Spending for June (10:00 ET), ISM Manufacturing PMI for July (10:00 ET).
- Week ahead is a jobs week — all eyes build toward Friday's July jobs report; Monday's ISM print is the first tell.
- Monday earnings (before open): MAR, TSN, CNH, L, KOS among the larger names. After close: ON, PLTR, VRTX, WMB, SBAC, CLX, FANG, TKO, SNAP and a long tail — full list logged in search results if needed for the AM brief.

**Tape read:**
- Today reads as a **reversal/rotation day**, not a clean trend day: AI-mega-cap strength (MSFT/AMZN) fought a bond-yield headwind and an AAPL guidance miss most of the session, with Discretionary/Tech dragging the tape up while Materials and rate-sensitives lagged. Small caps (RTY) held their 2026 leadership.
- Yields are the story under the story — a 10Y at multi-year highs (4.737% intraday) into a week that ends with the jobs report is the setup risk for next week, not today's AI euphoria.
- Homebuilders: no confirmed break of a specific level today (data gap noted above), but the standing tension — affordability-bill tailwind vs. tariff-cost headwind — is unresolved and is the thing to watch if rates keep climbing.

**Tomorrow's key question:** *Does the Nasdaq/AI-mega-cap bid survive a 10-year yield pushing toward 4.75%, or does Monday's ISM print tip the tape back toward the rate-sensitive sell-off that dominated Wednesday?*

## 7. Alpaca positions / P&L

No Alpaca connector is available in this session (checked via connector registry — not found/connected). Per standing instructions, the position pull is skipped this run. **No positions tracked this run.**

Note: `wolf_live_data.json` in this repo is stale (last updated 2026-06-24 13:43 ET, over a month old) — it should not be treated as current. This is a second standing process gap worth fixing: either wire a live Alpaca MCP connector into this environment, or confirm the local dashboard refresh job is still running and committing.

## Data Confidence note

This recap was built entirely from web search against a live-web index, with no direct broker/market-data API in this session. Index-level and sector-level moves are corroborated across 2+ independent sources each and are reported with reasonable confidence. Single-ticker closes for the full Brand 9 homebuilder basket and a clean AH-earnings-by-name list for today specifically were not retrievable with confidence and are named as gaps above rather than filled in with guesses.
