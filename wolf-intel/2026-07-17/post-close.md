# WOLF Post-Close Recap — 2026-07-17 (Friday)

## Index close

| Index | Close | Chg |
|---|---|---|
| S&P 500 | 7,457.69 | -1.15% |
| Nasdaq Composite | — | -1.81% |
| Dow Jones | 52,146.42 | -0.98% |
| Russell 2000 | 2,962.99 | -0.06% |
| VIX | 18.77 | +12.19% (+2.04 pts) |
| SOX (PHLX Semis) | — | -1.63% (-20% on the week; entered bear-market territory, closed off session lows) |
| UST 10yr | 4.525% | -5.6 bps |

Note: I could not independently confirm an exact Nasdaq Composite/NDX print or SOX absolute level beyond the % changes above — sourced from secondary aggregators, not a verified data feed. Flagging rather than presenting a false-precision number.

**Read:** Headline indices got dragged down by a mega-cap tech / semiconductor rout (SOX down 20% on the week, bear-market territory), but breadth was healthier than the index tape suggests — multiple sources cite roughly 8 of 11 S&P sectors positive on the day. Russell 2000 closing essentially flat against a -1.15%/-1.81% large-cap/tech drop is the tell: this was a rotation/divergence day, not a broad trend-down day. The 10yr yield falling ~5.6bps on the risk-off tone provided a tailwind to rate-sensitive names (homebuilders) even as growth/tech sold off.

## Sector heatmap

- **Led:** Energy (oil +2%, above $80/bbl, on escalating Middle East/Iran tensions), Consumer Staples, Real Estate.
- **Lagged:** Communication Services (Netflix -8% to -11% dragging the group), Industrials, Information Technology/Semiconductors (SOX -1.63%, down 20% for the week on AI-capex-spending concerns from hyperscalers).
- Divergence flagged above: cap-weighted indices red, sector breadth mostly green — the drag was concentrated in a handful of very large tech/semi names.

## Brand 9 client tickers (homebuilders)

| Ticker | Close | Chg |
|---|---|---|
| DHI | $151.55 | +1.04% |
| PHM | $125.39 | +0.67% |
| LEN | $85.29 | +1.89% |
| TOL | $153.19 | +0.43% |
| KBH | $62.23 | +2.49% |
| MTH | — | not confirmed this run |
| TPH | — | not confirmed this run |
| NVR | — | not confirmed this run |
| BZH | — | not confirmed this run |
| MDC | — | not confirmed this run |
| MHO | — | not confirmed this run |
| TMHC | — | not confirmed this run |

I have solid, sourced closes for 5 of 12 tickers (DHI, PHM, LEN, TOL, KBH); the remaining 7 (MTH, TPH, NVR, BZH, MDC, MHO, TMHC) I could not pull a verified close for this run without risking a fabricated number, so they're left blank rather than guessed. Worth wiring a real quote feed (Alpaca market data, or similar) into this pipeline so the full B9 book prints every day without gaps.

**Read:** Every confirmed homebuilder name was green, in a session where the S&P was down over 1%. This lines up cleanly with the 10yr yield move (-5.6bps to 4.525%) — homebuilders were the direct beneficiary of the flight-to-safety bond bid. KBH's +2.49% was the standout of the confirmed names.

## Signal post-mortem — today's WOLF Pre-Market Brief

No WOLF Pre-Market Brief for 2026-07-17 was found in this repo. The most recent committed WOLF live-data snapshot (`wolf_live_data.json`) is dated 2026-06-24T13:43 — over three weeks stale — and there is no `wolf-intel` or pre-market brief file predating today's directory. I cannot grade signal fires/misses against a brief that doesn't exist in the repo.

**This is itself the finding:** the pre-market brief pipeline does not appear to be running and committing daily. That's an operational gap worth surfacing to Bobby directly, not smoothing over — see the public brief for the named version of this.

## After-hours earnings (16:00-16:30 ET window)

No major reporters were confirmed in the 16:00-16:30 ET after-hours window today. Friday sessions are typically light for AH earnings, and I found no evidence of a notable name reporting tonight. The dominant earnings story of the week landed **last night** (Thursday 7/16 after close): **Netflix (NFLX)** —
- Q2 adj. EPS $0.80 vs $0.79 est. (beat), revenue $12.56B vs ~$12.58-12.6B est. (narrow miss)
- Stock fell ~8.6% in Thursday's after-hours session, then extended the decline through Friday's regular session to a double-digit (~10-11%) loss on the day — one of NFLX's biggest one-day drops of 2026
- Driver was guidance, not the print: FY revenue guide narrowed to $51.0-51.4B, and Q3 revenue growth guided to decelerate to ~+12%
- Multiple analysts cut price targets post-print; framed by CNBC as a "murky mosaic" — beat headline numbers, but growth-rate deceleration is what the market priced

## Overnight / Monday (2026-07-20) catalysts

- **Economic calendar:** Light. US Leading Economic Index (LEI) release; routine Treasury bill auctions; PBoC loan prime rate decision; Canada and New Zealand CPI prints.
- **Earnings before Monday's open:** DPZ (Domino's), DX, SMBK
- **Earnings after Monday's close:** AGNC, AMC, BOKF, CALX, CCK, HBCP, MCRI, RBB, SFBS, STLD, WASH, WRB, WTFC, ZION
- **Other:** Farnborough Airshow runs July 20-23 (aerospace/defense headline risk/catalyst window)
- **Asia/overnight:** No specific overnight catalyst beyond the PBoC decision was confirmed this run; watch semiconductor-linked Asia names (TSMC-adjacent supply chain) for read-through after the SOX bear-market close, and oil/energy-linked names given the escalating Iran/Middle East headline risk.

## Tomorrow's setup

- **Tape character:** Rotation/divergence day, not a clean trend day. Cap-weighted indices fell hard (SPX -1.15%, Nasdaq -1.81%) on a concentrated mega-cap tech/semiconductor unwind, but small caps (Russell 2000 -0.06%) and several defensive/value sectors (Energy, Staples, Real Estate) held up or gained. SOX closed off its session lows — tentative dip-buying, not capitulation.
- **Levels:** No specific level from a morning brief to check against (see signal post-mortem — no brief exists in-repo for today). Watching SOX for whether the "off the lows" close holds or fails Monday, and whether Russell 2000 flatness was genuine rotation or noise.
- **Key question for Monday:** Does the SOX bounce off Friday's lows hold, or does mega-cap tech take another leg down and drag the index tape with it — and does the homebuilder/small-cap bid (KBH +2.5%, LEN +1.9%, Russell 2000 flat) survive if the 10yr yield snaps back up, or was it just a one-day flight-to-safety reflex?

## Alpaca / positions

No Alpaca connector was available in this session (no `mcp__alpaca__*` tools loaded, no live API access). Per instructions, skipping the live position pull rather than presenting stale data.

Note for the record: this repo does contain a `wolf_live_data.json` snapshot, but it is dated 2026-06-24T13:43 (portfolio value $90,479.48, daily P&L -1.31%, 13 open positions) — more than three weeks old. That snapshot is **not** presented as today's P&L; it predates today by too wide a margin to be meaningful, and using it here would misrepresent stale data as live. **No positions tracked this run.**
