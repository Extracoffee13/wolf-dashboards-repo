# WOLF Post-Close Recap — 2026-08-25

Compiled after 16:00 ET close. Sourced via live web search (no market-data terminal/API in this session); individual figures cross-checked across sources where possible. Confidence flagged explicitly where sources disagreed — see Data Confidence Notes at bottom.

## Index Closes

| Index | Close | Chg |
|---|---|---|
| S&P 500 (SPX) | 7,677.25 | +0.32% (+24.39 pts) |
| Nasdaq Composite | 26,151.30 | +0.66% |
| Dow Jones | 53,577.40 | +0.30% (+160.24 pts) — 3rd straight up day |
| Russell 2000 (RTY) | ~2,995 | -0.76% |

NDX-100 (vs. Composite) not separately confirmed by sources.

## Sector / Breadth

- **Led:** Semiconductors, ahead of tomorrow's NVDA print — MRVL +5.54%, AMD +4.63%, NVDA itself snapped a 7-day losing streak.
- **Lagged:** Small caps — Russell 2000 -0.76% vs. SPX +0.32%, a sharp large/small divergence.
- Nasdaq breadth reportedly negative (~1.5:1 decliners over advancers) despite the index gain — narrow, mega-cap-driven tape, not broad participation.
- VIX +4.76% to 15.85 *despite* the up day — hedging demand building into the NVDA event.
- Could not confirm a clean sector-SPDR (XLK/XLF/XLE/etc.) breakdown specific to today — the only figures found trace mathematically to Monday 8/24's close, not today's. Excluded rather than misattributed.
- Macro: 10Y yield -7bp to 4.625%, second straight down day — supported rate-sensitive names (homebuilders, see below). Oil sold off hard (Brent -3.9% to $88.58, WTI -3.1% to $82.36) on Iran-sanctions-related pressure.

## Brand 9 Client Tickers (Homebuilders)

Sector proxy: **XHB +1.11% to $106.79, ITB +1.01% to $97.72** — homebuilders outperformed the S&P as a group today.

| Ticker | Close | Chg | Confidence |
|---|---|---|---|
| KBH | $62.23 | +2.49% | Well corroborated. No confirmed specific catalyst — reads as broad rate-sensitive/sector strength, not company news. |
| NVR | $6,359.40 | ≈ -0.60% | Well corroborated — the only builder confirmed lower today. |
| MTH | $73.08 | +1.14% | Reasonably confident (Google Finance-sourced). |
| MHO | $137.59 | +1.41% | Reasonably confident. |
| TPH | $34.12 | +0.26% | Reasonably confident. |
| LEN | — | — | **Not confirmed.** Sources gave conflicting prices ($84–88 range); not calling it rather than guessing. |
| DHI | ~$148–149 | ~-0.32% (unconfirmed) | Low confidence — date-ambiguous across sources. |
| PHM | ~$128–129 | ~-1.09% (unconfirmed) | Low confidence — conflicts with the broader homebuilder-ETF strength seen today; possibly stale data. |
| TOL | — | — | Not confirmed with any reliability ($148–154 range cited). |
| BZH | — | — | No data found for today; last confirmed print was 8/10 ($33.06). |
| MDC | — | **Delisted** | Acquired by Sekisui House ($63.00/share cash, ~$4.9B), deal closed April 2024. Folded into Sekisui's "One Company" US structure with Woodside Homes, Holt Homes, Chesmar Homes. |
| TMHC | — | **Delisted** | Acquired by **Berkshire Hathaway** ($72.50/share cash, ~$6.8B equity), signed 5/31/26, shareholder vote passed 7/22/26, **deal completed 7/24/26**. One of Greg Abel's first deals as Berkshire CEO; integrated with Berkshire's Clayton Properties Group. CEO Sheryl Palmer staying on. |

**Action item:** MDC and TMHC are no longer independent tickers. TMHC's delisting is recent (July 2026) — confirm whether any active B9 content/pages still reference it as a tradeable name and update.

## Signal Post-Mortem — Today's WOLF Pre-Market Brief

**Gap:** No dated Pre-Market Brief for 2026-08-25 exists anywhere in this repo. `wolf-intel/` did not exist before this run, and `wolf-brief/` only contains launch-era files from ~May 2026. There is nothing to cross-reference today's signals against.

This reads as a pipeline gap, not a market call: either the Pre-Market Brief job isn't running, or it isn't landing in this repo. Recommend checking whatever cron/dispatch is supposed to write the 09:00 ET pre-market post.

## After-Hours Earnings (16:00–16:30 ET)

**INTU (Intuit)**
- EPS $4.03 vs. $3.54 est — beat
- Revenue $4.4B vs. $4.28B est — beat
- FY27 guide: EPS $22.88–$23.12 vs. $23.83 consensus (**below** — soft), revenue $23.30–$23.50B vs. $21.40B consensus (**above**)
- Reaction: "sell the beat" framing on the weak EPS guide; exact AH % move not reliably confirmed.

**ZM (Zoom Communications)**
- EPS $1.55 vs. $1.48 est — beat
- Revenue $1.277B vs. $1.269B est — beat
- Guide raised: EPS $6.08–$6.12 vs. $6.04 consensus
- Enterprise revenue +7.8% YoY (strongest in 3 years); >$100K customers +8.2% to 4,625
- Reaction: initially down ~4% AH, tapered to roughly -2% as the raise was digested — beat-and-raise still sold, likely priced in.

## Tomorrow's Setup (Wednesday, August 26, 2026)

**Overnight/Asia:** De-risking into the NVDA print — Nikkei 225 -0.55%, Kospi -2.37% (chip-heavy Korea hit hard), Kosdaq -1.23%, ASX 200 +0.29%, Hang Seng/Shanghai roughly flat.

**Scheduled data (8:30 ET unless noted):**
- MBA mortgage applications (7:00 ET)
- Q2 GDP, second estimate (~1.5% annualized consensus) — flagged as the week's single biggest data mover
- Durable Goods Orders, July (~+0.7% consensus)
- Personal Income (~+0.3%) / Spending (~+0.2%) / PCE price index (~+0.1%)

**Pre-market earnings:** ANF (~7:30am), KSS (~$0.58 EPS / $3.32B rev consensus), ~39 companies total reporting Wednesday.

**After Wednesday's close — the dominant catalyst of the week:** NVDA reports Q2 FY27; options pricing a ~6% single-day implied move (~$313B swing at current market cap). CRWD also reports after Wednesday's close.

**Later in the week:** Fed Chair Kevin Warsh speaks Friday at Jackson Hole.

## Tape Character

Narrow, mega-cap/semiconductor-driven grind higher — not a broad trend day. Index-level gains masked negative underlying breadth. Best read as a positioning/wait-and-see session ahead of Wednesday's NVDA print, with falling yields giving rate-sensitive groups (homebuilders) a modest independent bid.

## Tomorrow's Key Question

Does the homebuilder/rate-sensitive bid (XHB/ITB +1% today on falling yields) survive Wednesday's GDP/PCE data and Nvidia's ~$313B-implied move, or does risk narrow entirely to chips into the print?

## Alpaca / Positions

No Alpaca connection available in this session — position pull and today's P&L skipped per instructions. `wolf_live_data.json` in this repo is stale (last updated 2026-06-24) and was not treated as live data.

## Data Confidence Notes

1. LEN, DHI, PHM, TOL, BZH exact closes for today are **not confirmed** — search sources gave conflicting or date-ambiguous figures. Do not treat the DHI/PHM % changes above as reliable; they're included only as low-confidence directional color.
2. Detailed sector-SPDR breadth (XLK/XLF/XLE/etc.) for today specifically could not be confirmed — the only figures found trace to Monday 8/24's close.
3. INTU's exact after-hours % move is unconfirmed — direction (negative, on the soft EPS guide) is well-supported.
4. KBH's specific catalyst for its +2.49% move is unconfirmed — no dated news item found; attributed to broad sector/rate strength.
5. This session's web-fetch access hit egress blocks on most primary finance sites (Yahoo Finance, CNBC, Investing.com, MarketBeat, TipRanks, Stockanalysis.com); all figures above come from search-result snippets cross-checked for internal consistency, not direct page fetches.
