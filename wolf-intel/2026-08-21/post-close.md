# WOLF Post-Close Recap — 2026-08-21 (Friday)

Generated post-16:00 ET. Source: open web research (WebSearch) — no direct market-data API or Alpaca live feed was available this run. Where outlets disagreed, that disagreement is called out explicitly rather than papered over.

## 1. Index closes

| Index | Close | Chg |
|---|---|---|
| S&P 500 | ~7,673 (est. from +0.42% off Thu's 7,641.16) | +0.42% |
| Nasdaq Composite | — | +0.46% |
| Dow Jones | 52,759.21 range (+~0.5–1%, sources split) | +0.51% to +1% |
| Russell 2000 | 3,005.99 | +0.45% |

**Data quality note:** multiple outlets (TheStreet, Yahoo, CNBC-adjacent search snippets) returned internally inconsistent numbers for today — some search syntheses conflated Thursday 8/20's down-close (S&P -0.9% to 7,641.16, Russell -1.34%, "Nasdaq/S&P slip as Treasury rally fades," chip selloff, Iran tensions) with Friday 8/21's rebound. The headline framing that is consistent across sources is: **Thursday was a broad selloff, Friday was a relief bounce.** Treat the exact S&P point close above as an estimate, not a verified print — flagging rather than presenting false precision.

## 2. Sector heatmap

**Led:** Financials (crypto-adjacent names strong — Robinhood +~14%, Coinbase +~8% — as bitcoin ran +22% on the week), Materials (+2%). Energy and semis cited as pockets of relative strength intraday.

**Lagged:** Consumer Staples (XLP -1.9%), Health Care (XLV -1.9%), Consumer Discretionary (XLY -1.8%). Breadth was weak — one source put it at **9 of 11 sectors red** even as the headline index closed green, i.e. a narrow, cap-weighted bounce, not a broad-based rally. Info tech down >3% on the week, Amkor and Credo named as laggards dragging the group.

## 3. Brand 9 client tickers — homebuilders (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

Reliable, same-day figures could only be pulled for four names (CNBC live-quote snapshot, exact capture timestamp not independently confirmable):

| Ticker | Price | Chg |
|---|---|---|
| DHI | $148.81 | -0.71% |
| PHM | $130.18 | -0.28% |
| LEN | $86.83 | -0.81% |
| TOL | $148.27 | -0.70% |

KBH, MTH, TPH, NVR, BZH, MDC, MHO, TMHC: **no verifiable same-day quote surfaced.** Not fabricating numbers for these — flagging as a gap rather than guessing.

Sector context: 10-year Treasury yield sitting at ~4.70% — per housing-sector commentary, that's exactly the line where "sustained move above is a warning" for homebuilder valuations (vs. a tailwind below 4.30%). The four builders with confirmed quotes were all modestly red on the day despite the broader index bounce, consistent with rates staying pinned near that warning line even as equities rallied elsewhere. This week's bond volatility (long yields briefly topped 5.3%, a 19-year high, on Tuesday) is the more important builder-sector story than any single day's print.

## 4. Signal post-mortem — today's WOLF Pre-Market Brief

**No Pre-Market Brief file for 2026-08-21 was found in this repo.** No `wolf-intel/2026-08-21/pre-market.md` or equivalent exists to grade signals against. Skipping the fire/no-fire table rather than inventing calls that were never made. (Process gap: the pre-market brief needs to actually be written and committed each morning for this section to do its job — flagging for the loop, not covering it up.)

## 5. After-hours earnings (16:00–16:30 ET window)

Search did not surface a confirmed, specific list of companies reporting in the immediate 16:00-16:30 ET window today with beat/miss/guide detail reliable enough to report. Generic earnings-calendar aggregator pages (TipRanks, Earnings Whispers, Seeking Alpha) confirmed "~15 earnings scheduled for Friday, August 21, 2026" but did not resolve to named tickers + results in the sources retrieved. Not fabricating reaction color here.

## 6. Overnight / Monday 8/24 catalysts

- **Econ:** Chicago Fed National Activity Index (July), 8:30 AM ET Monday.
- **Pre-market earnings Monday:** PDD, XPEV, XYF, NCTY, NSSC.
- **After-close Monday:** PICS, TUYA.
- **Macro overhang carried into the weekend:** 10Y yield ~4.70%, this week's bond selloff (long yields briefly >5.3%, 19-yr high) still the dominant cross-asset story; Treasury (Bessent) doubled long-term buyback size ($2B → $4B+ per operation) trying to steady the move — market's early reaction to that was the "claw back some ground" bounce, so the read-through is fragile, not a conviction reversal.
- **Geopolitical:** US-Iran tension ("economic warfare" plan headlines) still an unresolved overnight wildcard for energy/risk sentiment.
- **Crypto:** Bitcoin +22% on the week — if that continues into Monday it keeps financials/crypto-adjacent equities as the marginal leadership group.

## 7. Tape read for tomorrow's setup

Thursday = broad-based selloff (9/11 sectors would've been red-heavy, Iran + chip-selloff driven). Friday = narrow, cap-weighted relief bounce (financials/materials/crypto carrying the index green while breadth stayed mostly negative) on the back of a Treasury buyback-size headline, not a fundamental de-risking of the bond story. **Classification: reversal/relief day riding on thin breadth, inside a still-choppy, rates-driven range week — not a clean trend day.**

Levels: no morning-brief levels exist to check broken/held against (see §4). Absent that, the level that matters most mechanically for the B9 homebuilder book is the 10Y yield's relationship to ~4.70% (headwind) vs ~4.30% (tailwind) — currently sitting right on the headwind line.

**Tomorrow's key question:** Does the 10-year yield actually break back below ~4.70%, letting Friday's narrow bounce broaden out and the homebuilder book stabilize — or does the bond market's volatile week resume and drag Friday's gain back in on Monday?

## 8. Alpaca / positions

No live Alpaca connection was available this session (no Alpaca MCP tool in this environment's toolset). `wolf_live_data.json` in this repo is stale — last updated 2026-06-24, ~2 months old — and is not being treated as a live source. **No positions tracked this run.**
