# WOLF Post-Close Recap — 2026-08-11

Compiled after 16:00 ET close. Data pulled via web research (no live Alpaca feed available this run — see Positions/P&L section). Cross-source figures for the same index sometimes disagreed by a few tenths of a point; where that happened I've used the most internally-consistent cluster (index level + Dow + sector narrative from the same source set) and flagged the discrepancy rather than silently picking one.

## 1. Index closes

| Index | Close | Chg |
|---|---|---|
| S&P 500 (SPX) | 7,728.20 | -0.32% |
| Nasdaq Composite | 26,445.45 | -0.60% |
| Dow Jones Industrial | 53,791.85 | -0.34% |
| Russell 2000 (RTY) | 3,017.40 | -0.56% |

Note: task asked for NDX specifically — I could not isolate a clean Nasdaq-100 print separate from Composite; used Composite as proxy. Flagging as a data gap to close tomorrow. A second source printed SPX at 7,753.11 (-0.06%) and Nasdaq Composite at 26,605.36 (-0.32%) — materially different from the cluster above. Went with the set that has a coherent sector/news narrative attached (oil/Hormuz story matches Dow+SPX+sector moves); the outlier is noted for the record, not erased.

All three major averages finished red, small-range day — not a trend day.

## 2. Sector heatmap

- **Led:** Energy (oil/gas stocks +1.1%; XLE printed +4.66% in a separate ETF-level pull — large enough spread between the two readings that I don't trust either number in isolation, but direction is unambiguous: energy was the day's clear leader). Financials also positive (XLF ~+0.13%).
- **Lagged:** Travel & leisure -0.8%. Consumer discretionary soft (XLY ~-0.20%).
- **Driver:** No deal to reopen the Strait of Hormuz — Iran holding the line — pushed WTI above $83. Classic geopolitical-oil-shock rotation (energy/financials up, travel/discretionary down) rather than broad risk-off; the indices being only modestly red despite an oil spike above $83 reads as tape resilience, not fragility.
- Traders were also sitting on hands ahead of tomorrow's CPI — positioning caution likely capped both the downside and any dip-buying.

## 3. Brand 9 client tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

Confirmed:
| Ticker | Close | Chg |
|---|---|---|
| LEN | $88.19 | +3.97% |
| DHI | $151.09 | +3.48% |
| PHM | $133.12 | +2.76% |
| KBH | $62.23 | +2.49% |

**Not confirmed today** — TOL, MTH, TPH, NVR, BZH, MHO, TMHC. Search returned quote-comparison page links, not the actual printed numbers. Real gap: next run should pull these from a live quote feed (Alpaca or equivalent) instead of web search, which doesn't reliably surface same-day closes for lower-volume names.

**Flag for the client list itself:** MDC (M.D.C. Holdings) was acquired by Sekisui House in 2024 and delisted — the ticker is dead. It should come out of the Brand 9 tracking list, or get replaced with whatever entity tracks that relationship now (Sekisui House/Sekisui-owned homebuilding ops if relevant to Brand 9's book).

**Read:** the four confirmed names were all firmly green (+2.5% to +4.0%) on a day the broader tape was red — a real, clean divergence. Homebuilders decoupled from the index tape today. Direction consistent with the rate-cut trade following last Friday's (Aug 7) weak jobs report (payrolls -23k vs. +83k expected, unemployment rate down to 4.1%) — lower rates lower the cost of the mortgage that gates every one of these companies' units sold.

## 4. WOLF Pre-Market Brief signal post-mortem

**No pre-market brief artifact exists in this repo for 2026-08-11.** `wolf-intel/2026-08-11/` did not exist before this run, and there's no other file matching a pre-market brief for today's date. This means there is nothing to grade tonight's tape against — no signals to mark fired/missed, no levels to check broken/held.

This is a pipeline gap, not a "no signals today" result — it needs to be fixed before tomorrow's post-close can do real signal accounting. Named directly in the public brief.

## 5. After-hours earnings (16:00–16:30 ET window)

Reporting tonight: SMCI, CRWV, LITE, FLY, CAVA, HRB, and a long tail (166 reports scheduled market-wide today per Earnings Whispers).

- **CoreWeave (CRWV):** ran +3.8% intraday into the print ($91.54) ahead of results (consensus roughly -$1.47 EPS GAAP, $2.56B revenue). One AH quote source showed $87.75 (-0.5%), but that print's timestamp relative to the actual earnings release isn't verifiable from what I pulled — CoreWeave has fallen on all four of its prior public-company earnings reports, averaging a 16.8% drop, so a same-night reversal wouldn't be a surprise, but I don't have a clean confirmed AH reaction number.
- **CAVA:** stock already down ~34% from highs into the print; Wall Street split (Morgan Stanley upgrade vs. Citi cutting target) — no confirmed AH reaction number captured.
- **SMCI, HRB, LITE, FLY:** no confirmed AH reaction numbers captured.

**Honest accounting: this section is incomplete.** Web search doesn't reliably surface AH reaction prints within an hour of the release. Fix for next run: pull AH quotes directly from a market data feed (Alpaca, IEX, or similar) rather than search — this is the second data-pipeline gap of the day, alongside the missing pre-market brief.

## 6. Tomorrow's overnight catalysts (2026-08-12)

- **July CPI, 8:30 ET** — the single biggest catalyst of the week. Consensus ~+3.4% headline. This is what the whole tape is sitting on hands for.
- **PPI** also in the week's data flow (later in the week, not necessarily tomorrow — didn't get exact day confirmed).
- **Pre-market/day earnings:** Cisco (CSCO) and Applied Materials (AMAT) are the named large-caps in the week's earnings queue; didn't confirm which specific day each reports.
- **Asia overnight:** Nikkei 225 futures last around 67,030, off an intraday range of 66,070–67,587 — no clean read on directional bias from what I pulled; treat as noise until the Tokyo open.

## 7. Tape read for tomorrow's setup

- **Tape type:** Range day, not trend. All three indices moved less than 0.6% on a day with a real geopolitical catalyst (oil above $83 on the Hormuz standoff) — that's compression, not indecision. Read as: market is waiting for CPI, not confused about direction.
- **Levels broken/held vs. morning brief:** Can't assess — no morning brief exists for today (see §4).
- **Setup-friendly?** Yes, cautiously — a coiled, low-realized-vol tape into a binary macro print (CPI) is exactly the setup that produces the next real trend day, in whichever direction the print breaks.

**Tomorrow's key question:** Does the homebuilder bid (LEN/DHI/PHM/KBH all +2.5–4% today) survive a hot CPI print, or does it unwind the moment the rate-cut trade it's built on gets called into question?

## 8. Positions / P&L

**No positions tracked this run.** No Alpaca API connection is available in this execution environment (no credentials, no MCP tool surfaced). `wolf_live_data.json` in the repo root is stale — last updated 2026-06-24, six weeks old — and was not used as a stand-in for today's P&L since presenting month-and-a-half-old numbers as tonight's close would be a worse error than omitting the section. Reconnecting a live Alpaca (or equivalent) feed into this pipeline is the top infrastructure fix alongside the missing pre-market brief.

## 9. Summary of gaps to fix (for next run)

1. Publish the WOLF Pre-Market Brief every trading day so post-close has something to grade.
2. Wire a live market-data feed (Alpaca or equivalent) for AH earnings reactions and same-day closes on lower-volume tickers (TOL, MTH, TPH, NVR, BZH, MHO, TMHC) — web search is not reliable for either.
3. Reconnect Alpaca for live positions/P&L — `wolf_live_data.json` needs an active updater, not a June snapshot.
4. Retire MDC from the Brand 9 client ticker list (delisted 2024) or replace with its successor entity.
