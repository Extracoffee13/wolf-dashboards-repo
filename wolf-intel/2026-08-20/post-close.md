# WOLF Post-Close Recap — 2026-08-20

## 0. Pipeline status (read this first)

`wolf_live_data.json` last updated **2026-06-24 13:43 ET** — the Alpaca paper-trading feed that powers WOLF's live dashboard has not pushed a single update in **57 days**. No `wolf-intel/` directory existed in this repo before this run, and no WOLF Pre-Market Brief was committed for 2026-08-20 (or any date this repo has record of). There is no Alpaca connector available to this session either — checked `ListConnectors`, only FMP (unauthenticated in this chat) is present.

Net effect: this recap runs on live web market data only. The "signals from today's Pre-Market Brief" and "Alpaca open positions / P&L" sections below are **not gradeable or pullable** — there's nothing to grade against and nothing to pull from. This is the headline finding of the run, not a footnote.

## 1. Indices — close and % change

| Index | Close | Chg |
|---|---|---|
| S&P 500 | ~7,641 | -0.8% |
| Nasdaq Composite | ~26,067 | -1.0% |
| Dow Jones | ~52,759 | -1.3% (-~700 pts) |
| Russell 2000 | — | +0.5% (only major index green) |

Source: aggregated web search of financial press (TheStreet, Yahoo Finance market-live coverage) for 2026-08-20 close. Different outlets' synthesized figures diverged by a few tenths of a point on SPX/Dow — treat the % changes as directionally solid, the exact index levels as approximate, not tick-verified. Small caps (RTY) decoupling positive from the other three is the notable divergence of the day.

## 2. What moved the tape

- **Treasury yields reversed higher**, unwinding the prior session's rally, after Treasury signaled it would lean more on buybacks of long-dated debt rather than curbing issuance — read as a short-term fix, not a durable yield-suppression plan. Rising yields + firmer energy prices reignited inflation worry into the close.
- **Walmart (WMT)** reported before the open: beat on earnings but flagged slowing U.S. sales growth, consumers making "trade-offs" amid high gas prices. Stock fell **>9%**, dragging consumer/retail broadly.
- Housing-adjacent industrials caught it too: **Home Depot -2.85%**, **Sherwin-Williams -2.99%**.
- Fresh housing data was soft: **housing starts -12.4%**, **pending home sales -2.3%** (July) — the housing print behind today's builder weakness.
- Energy firmer on the yield/oil combo (inflation-worry bid), acting as the session's relative-strength pocket alongside small caps.

## 3. Sector heatmap

Directional read for the session: **retail/consumer discretionary** and **housing-adjacent industrials/materials** (HD, SHW) were the clear laggards on the WMT miss + weak housing data. **Energy** held up best alongside the broader inflation-worry bid. Full 11-sector breadth figures could not be pinned to today's session specifically from available sources — the generic sector-heatmap search returned data that read as a longer-window (YTD/1-month) snapshot, not a same-day one, so it's omitted here rather than misattributed. Flagging the gap rather than guessing.

## 4. Brand 9 client tickers — homebuilders

Confirmed same-day moves (via web search, not a live feed):

| Ticker | Close | Chg |
|---|---|---|
| DHI | $148.81 | -0.71% |
| PHM | $130.18 | -0.28% |
| LEN | $86.83 | -0.81% |
| TOL | $148.27 | -0.70% |

KBH, MTH, TPH, NVR, BZH, MDC, MHO, TMHC: no individually-confirmed print found. Group proxy: **XHB (SPDR Homebuilders ETF) -1.77%** on the day — the broader builder complex sold off harder than the four large-caps above, consistent with builders being more rate-sensitive to the yield backup than the mega-cap homebuilders' earnings-driven moves. Do not treat the unconfirmed 8 tickers as "flat" — they're unknown, not zero. NAHB/Wells Fargo Housing Market Index ticked up to 35 from 34 in August — a marginal sentiment improvement that sits awkwardly next to today's much worse starts/pending-sales prints; that tension is worth watching.

## 5. Signal post-mortem — today's WOLF Pre-Market Brief

**N/A this run.** No Pre-Market Brief exists in this repo for 2026-08-20 to grade against. This is the second time this recap has to report a structural gap rather than a signal scorecard (see §0). If the Pre-Market Brief is supposed to be produced by a separate scheduled job, that job also appears dark — same as the live-data feed.

## 6. After-hours earnings (16:00-16:30 ET window)

- **Ross Stores (ROST)** — reported Q2 FY26 after the close (call at 4:15pm ET). EPS $2.66 (includes ~$0.60/sh one-time benefit from IEEPA tariff refunds). Total sales +13% YoY, comps +10% driven by traffic. Operating margin +610bps (405bps of that from the tariff refund; underlying +205bps, ahead of the company's own 130-150bps guide). Headline print is strong; the tariff-refund component means the as-reported beat overstates underlying momentum — worth normalizing before reacting to any AH pop.
- Other names in the AH/pre-market retail earnings wave this week (per calendar search): Target, Lowe's — not confirmed reporting in tonight's specific window from available sources; flagging as unconfirmed rather than guessing at numbers.

## 7. Alpaca positions / P&L

No Alpaca connection available to this session (not in `ListConnectors`; `wolf_live_data.json` is 57 days stale). **No positions tracked this run.**

## 8. Tomorrow's setup (2026-08-21)

**Tape character today:** reversal/risk-off day — yesterday's bond-rally-driven relief reversed, dragging equities down across the board except small caps. Not a clean trend day (RTY diverging from SPX/NDX/Dow is the tell); reads more like a rate-sensitivity repricing than a broad growth-scare.

**Levels vs. the morning:** no Pre-Market Brief exists to check levels against (see §5). Flagging rather than fabricating a "held/broke" read.

**Overnight/pre-market catalysts for 8/21:**
- 8:30am ET — Initial jobless claims, Philly Fed Manufacturing Index
- 9:45am ET — S&P Global Flash PMIs (Manufacturing/Services)
- 10:00am ET — Existing Home Sales (July), Conference Board Leading Index
- Fed: preliminary Jackson Hole-week positioning builds; the main Jackson Hole Symposium itself is the following week (Aug 27-29) per available sources — don't overweight tomorrow as the Fed headline day, but expect Fed-speak chatter into it.

**Tomorrow's key question:** Does the yield backup keep pressuring rate-sensitive sectors (housing, retail) into the jobless-claims/PMI prints, or does a soft claims number revive yesterday's bond-rally trade and give homebuilders + retail a bounce?

## 9. Data-confidence note

This entire recap was built from web search synthesis (no Alpaca feed, no FMP access, no Pre-Market Brief to cross-check). Index-level closing prices should be treated as approximate; % changes and the qualitative narrative (WMT miss, housing weakness, yield backup, RTY divergence) were corroborated across multiple independent sources and are higher-confidence. Anywhere a specific number isn't confirmed, this doc says so instead of filling the gap.
