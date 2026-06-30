# WOLF Post-Close Recap — 2026-06-30

## Index close

| Index | Level | Chg % |
|---|---|---|
| SPX | 7,499.36 | +0.79% |
| Nasdaq Composite | 26,213.72 | +1.52% |
| Russell 2000 | 3,024.37 | +0.46% |

Today closed out Q2 2026 — the best quarter for the S&P 500 and Nasdaq in six years, despite the geopolitical overhang from the Iran conflict earlier in the quarter. The tape carried over yesterday's record-high session (Dow closed at a fresh record Monday 6/29) into a continued tech-led "relief rally" today. Early session prints were choppier than the close suggests — SPX was flat-to-up low single digits and the Dow was briefly red intraday before the move higher into the close.

**Confidence note:** index closing levels above are sourced from aggregator snapshots (Yahoo/CNN/Trading Economics), not a direct exchange feed. Intraday commentary pulled from a separate article showed materially different (much smaller) early-session moves — treat the closing print as the reconciled number, the intraday color as directional only.

## Sector heatmap

Leaders into today's close: **communication services, consumer discretionary, technology** — continuing Monday's leadership (Alphabet's Dow inclusion replacing Verizon, Tesla +8.5%, Amazon +3.2%, Meta +2.2% on 6/29; today's QQQ futures/early tape extended that, +1.1% premarket on the index).

No reliable same-day sector-by-sector % breakdown was retrievable (Finviz and other heatmap sources returned 403s through the proxy). Treat sector leadership as directionally carried from yesterday's session rather than independently confirmed for today — **flagging as a data gap**, not asserting precision we don't have.

## Brand 9 client tickers — close

| Ticker | Price | Chg % | Note |
|---|---|---|---|
| LEN | $90.74 | +0.28% | |
| DHI | $164.23 | n/a | +28.9% trailing 12mo; July 21 earnings on deck, Street modeling -10.7% EPS y/y |
| PHM | $117.71 | -0.58% | |
| TOL | $164.14 | +1.27% | |
| MTH | — | — | **No confirmed same-day quote.** Last verified print was 6/24 ($82.39) — stale, not reported |
| TPH | $46.95 | -0.04% | |
| NVR | ~$6,814 | — | Last verified print was 6/25; today's close not independently confirmed |
| BZH | $27.23 | +0.26% | |
| MDC | **DELISTED** | — | **MDC Holdings is not a tradeable ticker.** Sekisui House completed its $4.9B acquisition (cash-out, $63.00/share) in April 2024; the entity now operates as Sekisui House U.S. This name should come out of the watchlist — it's been a dead ticker for over two years |
| MHO | — | — | **No data retrieved.** Search did not surface a same-day quote |
| TMHC | $71.78 | -0.24% | **Trading as merger arb, not a housing proxy.** Berkshire Hathaway (Greg Abel's first big deal as CEO) agreed 5/31/26 to acquire Taylor Morrison for $72.50/share cash (~$8.5B enterprise value, ~$6.8B equity value), deal expected to close H2 2026. TMHC is now pinned just under the deal price — its day-to-day moves reflect arb spread/deal-risk, not homebuilder fundamentals. Recommend flagging this distinction every time TMHC appears in the watchlist going forward |

**Watchlist hygiene flag:** 2 of 12 names (MDC, TMHC) are no longer clean homebuilder-cycle proxies — one is dead, one is a pending take-private. Worth a watchlist cleanup pass rather than continuing to report them at face value.

## Catalyst context — homebuilders

This week's homebuilder narrative has two pulls in opposite directions:
- **Bullish:** tariff exemptions for Canada/Mexico lumber were reported as a "major win" per NAHB, with DHI, NVR, LEN, PHM, and DFH all posting outsized gains on the news (DHI +4.6%, NVR +4.2%, PHM +3.6%, LEN +2.4% — these moves come from a Nasdaq-syndicated wire story; exact date within the past week could not be pinned down because the source article 403'd on fetch, so treat as "this week," not confirmed as today specifically).
- **Bearish:** the NAHB/Wells Fargo Housing Market Index fell to 35 in June (from 37 in May) — current sales conditions down 2pts to 38, buyer traffic flat at a weak 25. 35% of builders cut prices in June (up from 32% in May); incentive usage ticked to 62% (from 61%). Affordability stress is not improving even as the stocks rally on tariff relief.

That divergence — stocks up on policy relief, underlying demand still soft — is the central tension for the homebuilder cohort heading into Q3.

## Signals from today's WOLF Pre-Market Brief

**No pre-market brief artifact was found in this repo for 2026-06-30.** Searched `wolf-brief/`, `wolf-intel/`, and the full repo for any file dated today or matching a pre-market-brief naming pattern — none exists. This means there is nothing to grade signal hit/miss against for today's session.

This itself is the finding worth naming: either the pre-market brief pipeline didn't write to this repo today, or it writes somewhere this recap job doesn't have visibility into. Worth checking the upstream pre-market job directly rather than assuming silence means "no signals fired."

## Alpha Hathaway / earnings after the close

**Nike (NKE)** — reported after the bell.
- Beat both lines: EPS $0.72 vs $0.13 est.; revenue $10.972B vs $10.859B est.
- Caveat: the EPS beat was inflated by a one-time 52-cent benefit tied to expected IEEPA tariff recovery — strip that out and the underlying beat is much smaller.
- AH reaction: muted/mixed despite the headline beat. Stock is down ~42% over the trailing year on North America and China demand weakness; market wants evidence of a durable turnaround, not a one-off tariff-recovery boost, before re-rating.

**Constellation Brands (STZ)** — also scheduled to report after the bell (est. EPS $3.21, rev $2.40B). Actual results were not confirmed via search at time of writing — **not reporting a number we don't have**. Check back at open for AH price action and the actual print.

## Macro / rates context

New Fed Chair **Kevin Warsh** (took over from Powell at the start of 2026) ran his first June FOMC meeting with a notably hawkish tilt: task forces announced on Fed communication/policy-setting changes, and the median dot now shows **1-2 hikes** in 2026 — a reversal from the prior expectation of 1-2 cuts. Energy supply uncertainty (consistent with the Iran-conflict overhang from earlier in Q2) is cited as the complicating factor on the inflation side.

This matters directly for the homebuilder cohort: a hawkish Fed under a new, untested chair is a headwind for the rate-sensitive trade just as builders are trying to ride a tariff-relief bounce. That tension is this week's real story for B9 clients, more than any single day's tape.

## Alpaca / positions

No live Alpaca connection in this session — pulling positions/P&L was skipped per the "otherwise skip" instruction. **No positions tracked this run.**

Separately worth flagging: `wolf_live_data.json` in this repo shows a `last_updated` of 2026-06-24T13:43 and the git history shows no commits to that file since then (last commit `d87e1be`, 6 days ago as of this run). The intraday live-data pipeline that was running every 5-10 minutes through late June appears to have gone dark — that's a gap worth someone checking on independent of this recap.

## Tomorrow's setup (Wed 7/1/26)

- First trading day of Q3. ISM Manufacturing PMI releases at 10:00 ET — first real data point of the new quarter and a read on whether the tariff/energy cost pressure shows up in the factory survey.
- Overnight: watch Asia open for follow-through (or fade) on the tariff-relief / risk-on tone; no major scheduled Asia catalysts identified independently this run.
- Tape character: today reads as a **continuation/trend day** layered on top of yesterday's record close — not a reversal, not pure chop. The open question is whether that trend survives the first hawkish-Fed data point of Q3.

**Tomorrow's key question:** Does the homebuilder bid (tariff relief) survive a soft ISM print and Warsh's hawkish dot plot, or does the rate-sensitive trade roll over the moment real data pushes back?
