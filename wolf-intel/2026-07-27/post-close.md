# WOLF Post-Close Recap — 2026-07-27

*Compiled after 16:00 ET close. All figures cross-checked across ≥2 independent sources unless flagged.*

## 1. Index closes

| Index | Close | Chg |
|---|---|---|
| Dow Jones Industrial Average | 52,210.08 | +262.83 (+0.51%) |
| S&P 500 | 7,413.18 | +0.02% (essentially flat) |
| Nasdaq Composite | 24,932.08 | -0.18% |
| Russell 2000 (IWM proxy) | ~$292.36 | +0.41% — **UNVERIFIED as official close**, reads as a live-quote snapshot rather than confirmed settle price |

**Tape character: reversal day.** Futures and cash gapped up on an overnight US–Iran military strike-pause headline — oil collapsed ~6-7% (WTI toward $83-86/bbl) and the 10-year yield eased toward ~4.65% off recent 2026 highs, pushing S&P/Nasdaq up roughly +0.9-1.1% at the open. A midday China-semiconductor headline triggered a sharp, fast chip-sector selloff (described in coverage as "monstrous, motivated, margined" forced selling) that erased almost the entire S&P/Nasdaq gain into the close. The Dow, less semi-exposed and helped by cheaper oil, held its gain and closed the day's clear outperformer.

## 2. Sector heatmap

**Confirmed:** Semiconductors/tech were the unambiguous laggard — NVDA -4.9%, AMD -8.3%, INTC -3.5%, SMH (semi ETF) -4.1% on the session (-9.3% trailing month).

**Gap — flagged, not fabricated:** A clean, session-specific 11-sector leaderboard could not be confirmed. Search aggregators repeatedly served Friday 7/24 sector data (e.g. XLRE +2.2%, XLB +1.9%, XLK -1.4%) mislabeled under today's date headlines. Rather than publish those numbers as today's, this recap treats today's full sector breadth as **unresolved** beyond the semis/tech laggard call. Directionally, the oil-crash/yield-relief backdrop is a plausible tailwind for rate-sensitive groups (financials, real estate, homebuilders) but that is inference, not a confirmed print — see homebuilder section below.

## 3. Brand 9 client tickers — LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

**No individual close/%chg/volume figures are being published for this session.** Two independent research passes hit the same wall: primary quote sources (stockanalysis.com, Yahoo Finance, CNBC, WSJ, MarketWatch, Barchart, Investing.com, Google Finance) returned 403 bot-blocks on fetch, and web-search synthesis produced internally inconsistent numbers (e.g. two different LEN prices in one response) with several results dated 7/20–7/23 despite querying for 7/27. Publishing any of those figures would risk stating fabricated or stale prices as fact — that's a harder error than saying "unavailable."

**What could be verified to primary-source confidence:**
- **TMHC (Taylor Morrison):** No longer trades. Berkshire Hathaway completed its $8.5B all-cash acquisition ($72.50/share) on **July 24, 2026**; NYSE listing terminated, SEC reporting suspended. Confirmed via SEC 8-K, Taylor Morrison IR, PRNewswire, HousingWire. **This ticker should be retired from the Brand 9 watchlist going forward — it is a corporate action, not a daily tracking gap.**
- **MDC (MDC Holdings):** Already delisted since February 2024 (Sekisui House acquisition). **This ticker has been stale on the watchlist for well over a year and should also be retired.**
- **DHI:** Reported Q3 FY2026 earnings last Tuesday (7/21), not today — diluted EPS $3.20 (-5% YoY), revenue $9.2B (flat). Not a today-catalyst; no move attributable to earnings today.
- **Sector data points confirmed but not dated today:** NAHB/Wells Fargo Housing Market Index fell to 34 in July from 36 in June (mid-July release); June new home sales 628k SAAR, +1.6% MoM, -5.6% YoY, median price $398,300 (released 7/24); pending home sales not due until 8/18/2026. None of these are today's catalysts, though they sit in the immediate backdrop.

**Action item for tomorrow's pre-market prep:** the watchlist itself needs pruning (drop TMHC, MDC) and the data pipeline needs a real quote source (brokerage feed / market-data API) rather than open web search — see error analysis below.

## 4. Pre-Market Brief signal post-mortem

**No WOLF Pre-Market Brief for 2026-07-27 was found in this repository.** A repo-wide search for today's date and for any "pre-market" artifact turned up nothing — the most recent WOLF live-data commits in git history are dated 2026-06-24, over a month stale. This means there is no signal list to grade against for today's session. **Flagging as a pipeline gap, not glossing over it:** either the pre-market brief is being generated and stored somewhere outside this repo, or that leg of the pipeline has been dark since late June. Either way, tomorrow's setup should confirm where (or whether) the pre-market brief is landing before the next post-close run, or this post-mortem section will keep coming up empty.

## 5. Alpaca positions / P&L

**No Alpaca connection available this run — skipped per instructions.** No Alpaca MCP tool was present in this session's toolset. The only portfolio snapshot in-repo (`wolf_live_data.json`) is timestamped 2026-06-24T13:43 — over a month old — so it is not usable as today's P&L and was not treated as such. Note for the loop: **no positions tracked this run.**

## 6. After-hours earnings (16:00–16:30 ET window)

- **Applied Digital (APLD)** — fiscal Q4/FY2026, reported ~4:05pm ET. Revenue $258.75M vs. ~$94.8M est. (large beat, +407% YoY); adjusted EPS $0.04 vs. est. loss of $0.22 (beat). Disclosed 1.4GW contracted IT load (~$36B base lease revenue) and three new 15-year hyperscaler leases (810MW, ~$20.2B). **AH reaction: +3.17% to ~$27.24.**
- **Celestica (CLS)** — Q2 2026, reported after Monday's close; call set for 8:00am ET Tuesday. Guidance $4.15-4.45B revenue vs. ~$4.35B/EPS $2.29 consensus. **AH stock reaction: not found/unverified — not reporting a number.**

## 7. Tomorrow's overnight and pre-market catalysts (2026-07-28)

- **FOMC's two-day meeting begins tomorrow**; the policy decision itself lands **Wednesday 7/29 at 2:00pm ET** (Chair Kevin Warsh press conference) — markets are pricing roughly 65% odds of a hold.
- **Econ data (Tue 7/28):** S&P/Case-Shiller 20-City Home Price Index (9:00am ET, May YoY consensus 3.2% vs prior 3.4%) — directly relevant to the homebuilder book; CB Consumer Confidence (10:00am, consensus 100.5 vs 100.4); JOLTS Job Openings (10:00am, consensus 7.95M vs 8.14M prior); Richmond Fed Manufacturing (10:00am, consensus -8 vs -10).
- **Pre-market earnings (Tue 7/28):** Coca-Cola, Boeing, Corning, UPS, Sherwin-Williams, Illinois Tool Works, Royal Caribbean, Visa, Seagate, Waste Management, Mondelez, Ford, Teradyne.
- **Overnight/Asia watch:** durability of the US–Iran strike pause, and read-through of today's semiconductor selloff into Asian/European chip names (Tokyo Electron, ASML, SK Hynix) at their opens.
- Single-name note carried into tomorrow: Tesla was cut to a $420 price target (from $465) by Deutsche Bank on robotaxi/humanoid-robot delay concerns.

## 8. Tomorrow's setup

- **Levels:** S&P held essentially flat (7,413.18) after erasing a ~0.9% intraday gain — the morning brief's bullish gap-up thesis (if any) would have been broken by the midday reversal; without a recovered pre-market brief for today, this can't be graded level-by-level, but the reversal itself is the notable fact.
- **Tape read for tomorrow:** semis are the swing factor — if the chip selloff extends into Tuesday's open, expect Nasdaq to lead down again; if it stabilizes, the oil-crash/rate-relief tailwind (still intact heading into FOMC) favors a resumption of the early-session bid, particularly in rate-sensitive groups.
- **One-line key question:** *Does the chip-sector selloff stabilize before the FOMC decision Wednesday, or does it drag the broader tape down with it into the Fed?*

---

### Error analysis / lessons for the pipeline (not sugar-coated)

1. **Homebuilder ticker data pipeline failed today.** Open web search + WebFetch could not produce reliable same-day close/volume data for the Brand 9 client list — quote aggregators are bot-blocked, and search synthesis conflated multiple different trading days under today's date. This needs a real market-data source (brokerage API, paid quote feed) to be trustworthy going forward. Publishing guessed numbers would have been worse than publishing none.
2. **No pre-market brief was found to grade against.** Either that pipeline leg isn't writing to this repo or it's been dark since 6/24. Needs confirmation before the next post-close run.
3. **Alpaca live-data feed has been stale since 2026-06-24.** No live connection this session; the in-repo snapshot is too old to use. Watchlist also carries two dead tickers (TMHC, MDC) that should be pruned.
