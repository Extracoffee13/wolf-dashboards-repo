# WOLF Post-Close Recap — 2026-08-24 (Monday)

## Data access note (read first)

Two structural gaps hit this run and shaped what follows:

1. **No WOLF Pre-Market Brief was found in this repo for 2026-08-24.** There is no `wolf-intel/2026-08-24/pre-market*.md` (or equivalent) to grade signals against, so the "which signals fired / error analysis" section below is a placeholder, not a real post-mortem. If a pre-market brief is being generated elsewhere and not committed to this repo, that's the fix — WOLF can't self-grade what it never wrote down.
2. **No Alpaca connector is available in this session** (`ListConnectors` returned nothing for Alpaca/trading). Per the free-data-only WOLF mandate, the local `wolf_live_data.json` snapshot in this repo is stale (`last_updated: 2026-06-24T13:43:00`, i.e. two months old) and was not used as live data. Positions/P&L: **no positions tracked this run.**

Market levels/sector/catalyst data below came from web search against Yahoo Finance / TheStreet / CNBC / financial-news aggregator snippets — direct `WebFetch` to Yahoo Finance, CNBC, MarketWatch, Google Finance, TradingEconomics, StockTitan and TheStreet was blocked by this session's network egress proxy, so figures are cross-checked across multiple search snippets rather than pulled from one live terminal feed. Treat index-level figures as good-to-two-decimals; treat anything below (especially per-ticker homebuilder moves) as directional, not tick-accurate.

---

## Index closes (2026-08-24)

| Index | Close | Chg % |
|---|---|---|
| S&P 500 | 7,652.86 | -0.28% |
| Nasdaq Composite | 25,980.19 | -0.76% |
| Dow Jones Industrial | 53,417.16 | +0.26% |
| Russell 2000 | ~2,997.88 | -0.66% |

Dow diverged positive while SPX/Nasdaq/RTY fell — a defensive/value rotation day, not a broad risk-off day. The divergence is the tell: mega-cap industrials and value held while growth/chip-heavy names got hit.

## Sector heatmap

**Led:** Materials (~+2.7%), Consumer Staples (~+1.3%), Financials and Communication Services (both ~+1%+). 8 of 11 S&P sectors closed higher.
**Lagged:** Utilities (~-1.6%), Technology — dragged hard by a semiconductor selloff: Micron -5.8% to -6.9% (reports differ on the exact print), SanDisk ~-10.9%, AMD >-3%, Broadcom >-2%, Marvell also lower.

Read: this was a narrow, chip-specific drawdown inside an otherwise green tape, not a market-wide risk event. Memory/AI-infra names (MU, SNDK, WDC) are in their own bear-market-within-a-bear-market on oversupply/pricing worries plus a Samsung dividend surprise that spooked the crowded memory trade.

## Macro drivers today

- **Iran sanctions:** Treasury Secretary Bessent detailed new US economic sanctions on Iran; Trump had threatened "economic D-Day."
- **US-Canada tariff dispute:** Trump vowed to raise tariffs on Canadian autos/auto parts/steel to 50% effective Jan 1, 2027. GM and Ford traded lower on the news. Canada's PM Carney suspended talks and vowed like-for-like retaliation.
- **Nvidia earnings loom (Wednesday 8/26)** and **Marvell (Thursday 8/27)** — today's chip weakness reads partly as position-trimming ahead of NVDA, on top of the standalone memory-stock unwind.
- **Fed Jackson Hole (Aug 27-29)** — new Fed Chair Kevin Warsh's first keynote is Friday 8/28, three weeks ahead of the September FOMC. Markets are pricing roughly 1-in-3 odds of a September move; odds build materially for December/March. This is the single biggest scheduled catalyst of the week and sits behind essentially every desk's caution today.

## Brand 9 client tickers — LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

**Not reliably pulled today.** Search snippets returned contradictory homebuilder data spanning different dates (one set showing builders up on falling yields, another showing builders "falling" — neither cleanly dated to 8/24 close), and direct fetch to Yahoo/CNBC ticker pages was blocked. Rather than publish a guess dressed as data, this section is being flagged as a gap rather than filled with an unverified number.

Context that *is* solid: 30-year mortgage rates are sitting around 6.65%, and tariff-driven construction-materials costs are running near a 27% effective rate, adding an estimated ~$11,000 to a typical new home — both continue to work against builder margins independent of today's tape. **Tomorrow's New Home Sales print (10:00 AM ET) is the actual catalyst for this basket** — see Tomorrow's Setup below.

**Action for tomorrow's run:** if a live quote source (Alpaca market data, a working finance API, or an allowed WebFetch domain) is available, use it for per-ticker closes — don't rely on search-snippet aggregation for this section again.

## Signal post-mortem — WOLF Pre-Market Brief

No pre-market brief file exists in this repo for 2026-08-24, so there is nothing to grade. **Error, not zero-signal-day:** the loop is broken upstream of this recap — either the pre-market brief isn't being generated, or it's being generated somewhere that isn't committed here. Fix that first; a post-close recap can't post-mortem a brief it can't find.

## After-hours earnings (16:00-16:30 ET window)

No notable earnings landed in the Monday after-hours window — this week's earnings calendar was light on Monday by design, with the marquee prints (NVDA Wednesday, MRVL Thursday) still ahead. Clean, verifiable data point: nothing to review here tonight.

## Tomorrow's overnight catalysts (2026-08-25)

**Pre-market earnings:** BMO, BNS (both Canadian banks — direct read-through to the US-Canada tariff story), CTRN, DKS (Dick's Sporting Goods — consumer-spending read), EH, GFI, SLQT, TOUR, VIPS.

**Economic calendar (ET):**
- 7:45 AM — ICSC Weekly Retail Sales
- 8:55 AM — Johnson/Redbook Weekly Sales
- 9:00 AM — Case-Shiller 20-City Home Price Index (June) — **homebuilder-relevant**
- 10:00 AM — **New Home Sales (July)** — **the** homebuilder catalyst
- 10:00 AM — Consumer Confidence (August)
- 10:00 AM — Richmond Fed Index (August)
- 1:00 PM — US Treasury $69B 2-year note auction
- 4:30 PM — API Weekly Inventory Data

**Asia/overnight:** could not source tonight's Asia futures/Nikkei-Hang Seng levels through search — flag for tomorrow's pre-market brief to pick up fresh rather than carry forward a guess.

## Tape read for tomorrow's setup

- **Tape character today:** narrow rotation/reversal-within-sectors day, not a trend day. Dow up, SPX/Nasdaq down, breadth actually positive (8/11 sectors green) — the index-level red headline overstates how bad today actually was outside chips.
- **Levels:** no pre-market brief exists to compare against, so "broken vs held" can't be assessed against a stated morning thesis today. Going forward this needs the brief in place.
- **One-line tomorrow's key question:** *Does New Home Sales (10 AM) confirm the housing-cost squeeze (27% material tariffs, 6.65% mortgages) or does a beat give the homebuilder basket a real bid heading into Jackson Hole?*
