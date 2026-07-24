# WOLF Post-Close Recap — Friday, July 24, 2026

*Compiled post-16:00 ET. First run of the post-close pipeline — `wolf-intel/` did not exist before this file.*

## Data confidence note

This session has no live Alpaca MCP connection and no direct market-data feed — everything below is web-search synthesis. Search results for this date returned materially inconsistent numbers across sources (e.g. S&P close cited as both +0.05% and -1.2% depending on query/article mix), and most primary quote pages (MarketWatch, WSJ, Google Finance, stooq, Yahoo history) 403'd on fetch. Where sources converged, confidence is marked **high**; single-source or conflicting figures are marked **low** and should be re-verified against a real feed before being traded on.

## Index closes

| Index | Level | Change | Confidence |
|---|---|---|---|
| S&P 500 | ~7,411.98 | +0.05% | Medium — recovering from Thu 7/23's -1.21% (7,408.30) selloff |
| Nasdaq Composite | — | slipped / "hugged the flatline" (sources disagree: -0.6% vs ~flat) | Low |
| Russell 2000 | 2,930.00 | -0.35% | Medium |
| Dow Jones | — | +0.5% to +0.7% (best major average) | Medium |
| VIX | 18.70 (Thu 7/23 print) | +12.4% on Thu; Fri direction not confirmed | Low |

**Week context:** Nasdaq down ~2% on the week, led by a Thursday selloff tied to Iran-related geopolitical risk, an oil spike, AI/chip-spending concerns, and newly effective tariffs. Friday saw oil reverse hard (Brent -5%, back under $100) and blue chips/cyclicals bounce while megacap tech stayed soft — reads as **rotation out of high-beta tech into value/cyclicals**, not a clean broad rally.

## Sector heatmap

Precise Friday (7/24) sector-by-sector closes were not obtainable from available sources. Thursday 7/23's move (last fully-sourced sector breakdown) — flagged as prior-day, not today:

- **Led:** Industrials +1.73%, Health Care +1.26%, Utilities +0.57%
- **Lagged:** Consumer Discretionary -4.61%, Communication Services -3.50%, Consumer Staples -1.39%

Friday's rebound narrative (falling oil, "blue chips rebound," "modest chip comeback") implies partial unwind of Thursday's Discretionary/Comm Services rout, but no verified numbers to confirm magnitude.

## Brand 9 client tickers (homebuilders)

| Ticker | Price | Change | Note |
|---|---|---|---|
| DHI | $151.55 | +1.04% | |
| PHM | $125.39 | +0.67% | |
| LEN | $85.29 | +1.89% | |
| TOL | $153.19 | +0.43% | |
| NVR | $6,155.02 | — | Last confirmed print is Thu 7/23 close; no Fri figure sourced |
| KBH | — | — | Not sourced this run |
| MTH, TPH, BZH, MDC, MHO, TMHC | — | — | Not sourced this run; group is tracked together in the data but no per-name Friday quote surfaced |

All four sourced builders (DHI, PHM, LEN, TOL) printed green Friday — consistent with the broader "cyclicals bounce as oil drops" tape.

**Housing backdrop (macro, not today-specific):**
- NAHB builder confidence: **34** in July — 15th straight month below the 40 threshold, longest such stretch since 2012
- 30-yr fixed mortgage: ~6.45–6.58%
- June new-home sales: +1.6% to a 628k annualized rate — first increase in three months, driven by builder discounting
- 37% of builders cut prices in July (up from 35% in June); incentive use at 63%, 16th straight month ≥60%

Read: builders are buying volume with margin. The Friday bounce in the equities is a rates/oil-relief trade, not a fundamentals reversal — confidence and pricing power are still eroding underneath.

## Signal post-mortem

**No WOLF Pre-Market Brief was found in this repo for 2026-07-24** (searched `wolf-intel/`, `wolf-brief/`, and full git history — nothing dated today). This means there is nothing to grade signals against for today's session. This is a pipeline gap, not a market observation — flagging it rather than papering over it.

The only signal data in-repo is a static demo/placeholder block in `WOLF_Command_Center.txt` (3 example signals — TSLA short, NFLX long, XLU long) dated to an earlier, unrelated snapshot. It is explicitly **not** treated as today's actual output and is not graded here.

## After-hours earnings

Search results returned AXP, VZ, SLB, BAH, and SXT as "reporting July 24," but AXP and VZ are conventionally BMO (before-market-open) reporters, not AH — likely a source/date-list conflation, and Friday afternoons are typically light for earnings by market convention anyway. No verified AH reaction data for any Brand 9-relevant name (no homebuilder reported earnings today). Treat this whole section as **unconfirmed** — do not act on it without a direct earnings-calendar check.

## Alpaca positions / P&L

**No positions tracked this run.** No live Alpaca MCP tool is available in this session. The in-repo `wolf_live_data.json` snapshot is stale (last updated 2026-06-24, one month old) and `scout_state.json` is stale to 2026-06-16 — neither reflects today's account state. Recommend wiring a live Alpaca connector before the next post-close run if position/P&L tracking is meant to be part of this pipeline.

## Tomorrow's setup

- **Tape read:** Reversal/stabilization attempt, not a trend day. Thursday's sharp risk-off (-1.2% SPX, VIX +12%) was partially unwound Friday on falling oil, but Nasdaq/chip weakness persisted into the close — leadership is narrow and fragile.
- **Levels:** No verified intraday level data (opening range, prior support/resistance) available this run — cannot confirm what from this morning's brief broke or held, since no morning brief exists to compare against.
- **Overnight catalysts:** Singapore MAS policy decision expected Mon 7/27 (seen holding steady); BOJ expected to hold rates the week of 7/27; Asian equities were under pressure into the weekend on the same Iran/oil/AI risk-off complex that hit the Nasdaq — watch for follow-through or reversal at the Asia open.
- **Tomorrow's key question:** *Does the Friday oil-relief bounce hold into Monday, or does chip/Nasdaq weakness (down ~2% on the week) drag the tape back down once markets digest the weekend's geopolitical news?* For Brand 9 specifically: *does Friday's builder bid (DHI/LEN/PHM/TOL all green) follow through, or does it fade back into the NAHB-34 / 6.5%-mortgage reality underneath it?*
