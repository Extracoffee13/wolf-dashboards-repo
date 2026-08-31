# WOLF Post-Close Recap — Monday, August 31, 2026

## 1. Index closes

| Index | Close | Chg |
|---|---|---|
| S&P 500 | 7,711.76 | -0.3% |
| Nasdaq Composite | 26,402.42 | -0.5% |
| Dow Jones Industrial Avg | 53,885.10 | -0.9% (-464 pts) |
| Russell 2000 | — (level not confirmed) | -1.39% |

Dow snapped a five-day win streak. Small caps (Russell 2000) took the worst of it, consistent with a rate-shock tape rather than a broad growth-scare — small caps carry the most floating-rate/balance-sheet sensitivity to the move in yields below.

Note: two wire sources gave slightly different S&P prints (7,686.14 vs 7,711.76) for the same session — used the more detailed/later source (7,711.76, -0.3%) as primary. Flagging the discrepancy rather than silently picking one; worth a source-of-record decision before this becomes a recurring wobble in the index table.

## 2. What drove the tape

- US and Iran traded fire for the first time in a month — the session's dominant headline, hit risk assets from the open.
- Crude oil pushed above $85/bbl on the escalation, feeding through to inflation-expectations trades.
- The 10-year Treasury yield topped 4.75% intraday, its highest print since January 2025, after three straight up sessions.
- Fed Chair Kevin Warsh's Jackson Hole remarks (Friday) were read as hawkish — he said inflation isn't meaningfully slowing and reaffirmed the 2% target commitment. Markets moved September rate-hike odds to ~57%, up sharply from ~40% a week ago.
- Net read: this was a rates-and-geopolitics day, not an earnings or growth-scare day. Ten of eleven S&P sectors closed red.

## 3. Sector heatmap

| Sector | Direction | Note |
|---|---|---|
| Energy | Led | Oil >$85 on Iran escalation |
| Technology (XLK) | Led, +3.2% | Mega-cap strength offset the "AI stocks weak" narrative some wires ran — treat as the session's one real divergence, worth watching if it holds or reverses tomorrow |
| Communication Services (XLC) | Lagged, -1.1% | |
| Health Care (XLV) | Lagged, -1.1% | |
| Consumer Staples (XLP) | Lagged, -1.4% | Weakest of the eleven |
| Small caps / Russell 2000 | Lagged hardest, -1.39% | Rate-sensitivity, not sector-specific |

10 of 11 sectors were red; Tech was the sole green sector on the day. That combination (broad red tape, one mega-cap-driven exception, small caps worst) is the fingerprint of a rates/duration shock, not a risk-off-everything day.

## 4. Brand 9 client tickers — homebuilders (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

**Data gap, named plainly:** exact per-ticker closes and volume for the twelve names were not retrievable through this run's search tools — no live market-data feed or broker connection is wired into this session (see §6). What is confirmed and directly relevant to this group:

- The 10-year yield closing above 4.75% (highest since Jan 2025) and September hike odds jumping to ~57% is a direct headwind for homebuilders — this is the most rate-sensitive equity group on the tape, more so than small caps generally.
- Builder confidence was already reported at an 18-month low earlier this cycle (June reading of 32, lowest since Dec 2022), with ~37% of builders cutting prices — the group was soft going into today's yield spike, not starting from strength.
- Directional call, not a confirmed print: expect the homebuilder complex (XHB/ITB and the twelve names) to have closed lower today, likely underperforming the S&P, given the yield move. This needs verification against an actual price feed before it goes in front of a client — flagging as inferred, not observed.

**Action item:** wire a real quote source (Alpaca market data, or a free delayed feed) into the WOLF pipeline so this section stops being inferred from macro proxies. Right now the homebuilder section — the one section B9 clients actually care about — is the weakest-sourced part of this report.

## 5. After-hours earnings (16:00–16:30 ET window)

No earnings reports of note were identified for companies reporting in the 16:00–16:30 ET window today. No AH reaction to report.

## 6. Alpaca / positions

No Alpaca connection is wired into this session — skipping the position and today's-P&L pull. No positions tracked this run. (The repo's `wolf_live_data.json` and `scout_state.json` are stale, dated late June 2026 — they are not live for this session and were not used as a substitute.)

## 7. Signal post-mortem vs. today's WOLF Pre-Market Brief

**No pre-market brief for 2026-08-31 was found in this repo** (`wolf-intel/2026-08-31/` was empty before this file, and `wolf-brief/` contains only unrelated launch-collateral files). Without a stored pre-market call, there is nothing to grade signals against — no "fired / didn't fire" comparison is possible for today.

This is itself worth naming rather than quietly working around: if the pre-market brief is supposed to land in this repo before the open, it didn't today, which means today's post-close has no baseline to mark itself against. That's a process gap, not a market observation — see the PRAXIS lesson below.

## 8. Tomorrow's setup — Tuesday, September 1, 2026

- **Tape character today:** trend day, not a range or reversal day. The move was driven by one macro thread (Iran → oil → yields → hike odds) that pushed steadily through the session; 10-of-11 sectors red and small caps/rate-sensitives underperforming is the signature of a directional, not choppy, session.
- **Levels:** no morning-brief levels exist to check breaks/holds against (see §7).
- **Overnight/pre-open catalysts:** ISM Manufacturing PMI releases at 10:00 ET tomorrow (Sept 1 is the first business day of the month) — direct read-through to the rate-hike debate that drove today's tape. Continued Iran headline risk is the standing wildcard; watch Asia's open for how the region prices the weekend/Monday escalation before the US cash open.
- **Tomorrow's key question:** Does the 10-year holding above 4.75% keep grinding the homebuilder bid lower, or does tomorrow's ISM print give the Fed (and the market) room to walk the hawkish tone back?

## 9. Process notes for tomorrow

1. No pre-market brief existed for today in this repo — confirm whether that pipeline is supposed to write here, and fix it before the next cycle so signal grading is possible.
2. No live market-data or Alpaca connection is available in this session — the homebuilder ticker-level section (§4) and the position/P&L section (§6) are the two weakest parts of this report as a direct result. Both need a real data source wired in, not macro inference.
3. Two wire sources disagreed on the S&P close (see §1) — worth picking one source of record.
