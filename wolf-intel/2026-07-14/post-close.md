# WOLF Post-Close Recap — Tuesday, July 14, 2026

Compiled after 16:00 ET close. All levels below sourced live via web search (no live market-data feed or Alpaca connector was available this run — see Data Sources note at bottom).

## 1. Index Closes

| Index | Close | Chg |
|---|---|---|
| S&P 500 (SPX) | 7,543.59 | +0.38% |
| Dow Jones (DJIA) | 52,508.27 | +0.02% (+9.63 pts) |
| Nasdaq Composite | 26,107.01 | +0.9% |
| Russell 2000 (RTY, via IWM) | ~$294.48 (IWM) | +0.34% |

Session was CPI-driven. June CPI printed -0.4% m/m (cons. -0.2%) vs May's +0.4%, dragging the y/y rate to 3.5% (cons. 3.8%, prior 4.2%) — the biggest monthly decline in six years, led by a ~10% drop in gasoline. Core CPI was flat m/m (cons. +0.2%), core y/y 2.6% (cons. 2.9%). Shelter cooled sharply too, +0.1% m/m. Treasury yields fell sharply on the print; futures-implied odds of a September Fed hike eased to 63% from >75% the day before — note this cycle the Fed is still in a hiking posture, not cutting, so "cooler CPI" reads as "less hawkish," not "dovish pivot."

## 2. Sector Heatmap

**Led:**
- Energy / basic resources — standout, +2.4%; oil & gas +1.3%
- Semiconductors — SMH +2.5%, rebounding off the prior session's selloff
- Financials — S&P financials sector +~0.25%, mixed under the hood (see bank earnings below)

**Lagged:**
- Industrials/Tech-adjacent hit by IBM's guide-down (see below), which weighed on the Dow specifically
- Healthcare — Biogen -8.6%, Stryker -6.5% on earnings-related weakness

## 3. Brand 9 Client Tickers (Homebuilders)

Confirmed live prints:

| Ticker | Close | Chg |
|---|---|---|
| DHI (D.R. Horton) | $150.16 | +1.11% |
| PHM (PulteGroup) | $123.94 | +0.81% |
| LEN (Lennar) | $84.11 | +0.62% |
| KBH (KB Home) | $55.53 | +1.40% |
| TOL (Toll Brothers) | $101.06 | change vs. today's open not independently confirmed |

**Not confirmed this run** (data unavailable via search — flagging rather than guessing): MTH, TPH, NVR, BZH, MDC, MHO. Do not treat as flat; treat as unknown.

**TMHC (Taylor Morrison)** is a special situation, not a live read on builder sentiment — Berkshire Hathaway announced a $8.5B all-cash take-private on 5/31/26, so the stock trades near the deal price with muted beta to the group.

Sector proxy: XHB (SPDR homebuilders ETF) was ~$107.91 intraday (~2:55pm ET) vs. prior close $108.61, i.e. modestly softer even as DHI/PHM/LEN/KBH ticked green — a data conflict worth flagging, not resolving with a guess. Possible explanations: XHB's basket includes suppliers/retailers (not just builders) that lagged, or the intraday print predates the final leg into the close. Confirm at tomorrow's open.

Backdrop unchanged and still the dominant multi-week story: 30Y fixed ~6.65%, and tariff-driven effective rates on construction materials >27%, estimated at ~$11,000 added cost per new home. Builders are still buying down rates/absorbing incentives to move entry-level inventory — margin story, not volume story.

## 4. Signal Post-Mortem

**No WOLF Pre-Market Brief was found in this repository for today's date (2026-07-14).** Checked `wolf-intel/`, `wolf-brief/`, and full git history — no pre-market file, no signals log, nothing dated today prior to this run. This is a process gap, not a market call: there is nothing to grade (fired/didn't-fire) because no calls were made. Flagging for the loop: the post-close job depends on a pre-market artifact existing to diff against, and today it didn't.

## 5. After-Hours Earnings (reporting today)

- **JPMorgan (JPM)** — reported *before* the open today (not AH), $6.14 EPS vs. $5.59 est., $16.9B Q2 profit. Stock +2.8% intraday / some sources +1.49–2.8% depending on print time.
- **Goldman Sachs (GS)** — beat, stock +7.4–7.6%.
- **Citigroup (C)** — softer results, -5.77%.
- **Wells Fargo (WFC)** — softer results, -3.31%.
- **IBM** — issued a preliminary Q2 guide-down (soft software/infrastructure demand), stock -25.1%. Single biggest index-level drag of the day and weighed disproportionately on the Dow given IBM's price weighting.
- **CrowdStrike (CRWD)** +9.4%, **NetApp (NTAP)** +6% — AH/earnings-adjacent gainers.
- **Biogen (BIIB)** -8.6%, **Stryker (SYK)** -6.5% — earnings-related losers.

Note: search results returned a longer list of names scheduled for today/this week (ASML, BLK, PGR, CAG, ELV, JNJ, PNC, CTAS, MTB, BNY, FHN, MS, and others) without individually confirmed reaction data for each — not itemized above to avoid asserting moves that weren't independently verified.

## 6. Tomorrow's Setup (Wednesday, July 15, 2026)

- **Fed Chair Kevin Warsh** testifies before the Senate Banking Committee at 10:00 ET — first live commentary opportunity post-CPI, watch for any recalibration of hike-odds language.
- Yahoo/Econoday flagged ~66 economic events and ~25 earnings reports scheduled for 7/15 — did not get a clean pre-market-specific earnings list this run; check Yahoo/Earnings Whispers calendar directly before the open.
- Asia overnight: Nikkei 225 ~67,743.50 (+0.74% as of last read), Hang Seng ~24,214 (+0.2%) — both read as of Monday's/Tuesday's close, not a live Tuesday-evening print; treat as directional context only.
- **Tape character:** today reads as a broad, orderly risk-on day on a clean macro catalyst (cooler CPI) with idiosyncratic single-name noise (IBM, bank earnings dispersion) layered on top — not a trend day driven by one dominant theme, more of a "good macro print + earnings season churn" range day. Semis and energy led; the Dow's flatness is almost entirely an IBM-weighting artifact, not a signal about industrials broadly.
- **Levels:** no pre-market brief exists to check breaks/holds against (see Section 4).

**Tomorrow's key question:** Does the softer-than-expected CPI print translate into a genuine pullback in September hike odds (now 63%, was >75%), or does Warsh's testimony push the market back toward pricing a hike — and does the homebuilder group's modest bid today survive a rate-sensitive tape if that testimony leans hawkish?

## 7. Positions / P&L

No Alpaca connector is available in this session (checked `ListConnectors` — not installed/connected). Per instructions: **no positions tracked this run.** The `wolf_live_data.json` file in this repo has stale paper-account data from 2026-06-24 and was not used, since instructions call for current-day P&L only.

## Data Sources

All figures above from live web search (no dedicated market-data MCP tool was enabled in this session). Two article fetches (TheStreet, 24/7 Wall St homebuilder piece) returned HTTP 403 and could not be read directly — relied on search-result summaries instead. Where a figure could not be independently confirmed, it is flagged as unconfirmed rather than estimated.
