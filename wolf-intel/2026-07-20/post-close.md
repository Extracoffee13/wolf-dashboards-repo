# WOLF Post-Close Recap — Monday, July 20, 2026

*Compiled post-16:00 ET. See data-reliability note before citing any index print from this file.*

## 1. Data-reliability note (read first)

No live market-data feed (Alpaca or otherwise) was reachable from this session — see §5. Every index/sector figure below came from web search, and the search layer returned **internally contradictory numbers for today's close**: one query returned S&P +0.63% / Nasdaq +1.02% / Russell 2000 -0.42%; another, worded differently, returned S&P -1.0% (7,457.69, -76.08 pts) / Nasdaq -1.4% (25,520.24) / Dow -0.8% (52,146.42). I independently confirmed the second set (7,457.69) is actually **July 17's close**, mislabeled as "today" by the search summarizer. Direct WebFetch to CNBC, TheStreet, Zacks, Benzinga, TradingKey, and StockAnalysis all returned HTTP 403 (bot-blocked), so I could not verify against primary sources.

**Bottom line: do not treat any index closing level in this doc as ground truth.** The qualitative narrative below (direction, drivers, dispersion) is corroborated across multiple independent sources and is reliable; exact ticks are not. Tomorrow's run needs a real quote feed (Alpaca market data, Polygon, IEX) wired in before this section can carry numbers with confidence.

## 2. Index tape (directional, not tick-verified)

- **S&P 500 / Nasdaq / Dow**: mixed-to-negative, headline-driven session. Nasdaq was the most exposed to the Iran headline flow intraday ("Iran worries derail Nasdaq, S&P 500 despite modest chip comeback" — TheStreet). Whether the close finished net positive or net negative could not be pinned down — see §1.
- **Russell 2000**: underperformed the majors, consistent with a risk-off, small-cap-lagging tape (-0.42% in the one internally-consistent read I got).
- **Character of the day**: not a clean trend day. It's a **dispersion/rotation day** — one macro driver (Iran/oil) splitting the tape into clear winners and losers rather than moving everything one direction.

## 3. Sector heatmap

Could not obtain a verified full 11-sector heatmap. What's corroborated from named-stock moves:
- **Energy**: likely the session's leader — Brent +1.3% to $89.22, WTI +0.9% to $83.23, oil up ~20% month-to-date on the Iran conflict (source: CNBC oil desk, internally consistent, no contradiction across sources).
- **Software/mega-cap AI adjacents**: sharp laggards — Oracle -4.4%, ServiceNow -4.2%, Adobe -4.0%.
- **Chip/hardware**: bid up in apparent rotation away from software — Lumentum +7.5%, Teradyne +4.6%. This is the "modest chip comeback" referenced in the TheStreet headline.
- Treat any specific sector-ETF % (XLK, XLE, etc.) as unverified; I could not get a live quote for any sector ETF today (StockAnalysis WebFetch also 403'd).

## 4. Brand 9 client tickers — LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

**No ticker-specific closes, volumes, or moves for today were obtainable.** Search returned only stale/general commentary (analyst positioning from May–July: BofA Buy on DHI, Underperform on LEN, Neutral on PHM; 2026 homebuilder EPS estimates cut ~18% YTD; PHM adjusted EPS seen -21.5% y/y) — none of it dated to today's session. This is a real gap, not a rounding error: **the recap format promises "close, volume, notable moves" for the B9 book and could not deliver it tonight.**

Macro read that likely matters for this book tomorrow: oil spiking toward $90 on an active shooting conflict is a two-sided risk for homebuilders — flight-to-safety could pull Treasury yields down (helps mortgage rates), but sustained energy-cost inflation and consumer-confidence damage from a widening war is a demand-side drag. Structural backdrop already bearish going in (record-high 40-year-old median first-time buyer age, elevated inventory, construction-cost inflation cited across multiple sources this week).

**Action item:** wire a real quote source (Alpaca market data endpoint, or even a free delayed feed) into this pipeline specifically for the 12-name B9 book — this section is the one B9 actually needs verified, and it's the one I couldn't fill.

## 5. Alpaca / positions / P&L

No Alpaca MCP connector is available in this session (searched; none registered). `wolf_live_data.json` in this repo has a cached snapshot, but it's dated **2026-06-24T13:43 — 26 days stale** (portfolio value $90,479.48, daily P&L -$1,199.17 / -1.31% as of that date). That is not today's data and is not reported as such.

**No positions tracked this run.**

## 6. Signal post-mortem — today's WOLF Pre-Market Brief

Checked this repo (`git log`, full-tree search) for a pre-market brief dated 2026-07-20: **none exists.** No pre-market brief was published to this repo today, so there is nothing to grade a post-mortem against. This is itself the finding: the morning→evening loop has a gap — WOLF's pre-market signals aren't landing where the post-close job can find them. Either the pre-market brief is being written somewhere this repo doesn't see, or it didn't run today. Worth checking before tomorrow's pre-market cycle.

## 7. After-hours earnings (16:00–16:30 ET window)

Could not confirm a specific list of companies reporting in the 4:00–4:30 ET window tonight — earnings-calendar sites (Yahoo, Earnings Whispers, TipRanks, Seeking Alpha) were surfaced by search but not fetchable directly. One item that surfaced repeatedly but is **unconfirmed for today's session**: AMC Entertainment +9% on an earnings beat — this may be residual from an earlier print this cycle, not tonight's AH action. Do not repeat as fact without a verified source.

What is confirmed: the market is bracing for **Big Tech earnings later this week** (Yahoo's live-blog headline referenced markets "in wait for Big Tech earnings"), with Alphabet and Tesla both slated to report **Wednesday, July 22, after the close** — not tonight.

## 8. Tomorrow's setup — overnight catalysts (Tue, July 21)

- **Iran/Hormuz**: the active driver. The U.S. has struck Iran for 9 consecutive nights; 3 U.S. service members reportedly killed; Houthis have declared a maritime embargo on Saudi Arabia. This is a live, escalating war story, not a one-day headline — expect it to keep setting the tape until there's a de-escalation signal (there was a passing mention that Iran received mediator proposals to resume talks — watch for that).
- **Oil**: Brent near $89, WTI near $83, up ~20% this month. Analysts flagged $100+ Brent as plausible if Hormuz shipping traffic degrades further. This is the single biggest swing factor for tomorrow's open.
- **Earnings**: Tuesday, July 21 has ~73 reports scheduled; confirmed premarket names include **Schwab (SCHW)** and **Novartis (NVS)**, plus ~68 more unconfirmed by name via available search.
- **Asia**: no verified overnight print obtained for Nikkei/Hang Seng/Kospi tonight — flag as a gap, watch open for gap risk given the live Iran headline flow.

## 9. Tape read for tomorrow

- **Levels broken/held vs. this morning**: cannot assess — no pre-market brief exists in this repo to check against (see §6).
- **Setup-friendly tape?** It's a headline-driven dispersion day, not a clean trend or range day — the kind of tape where levels matter less than the next Iran/oil headline. Lower conviction for level-based setups until the geopolitical risk stabilizes.
- **Tomorrow's key question**: *Does the Iran-driven oil spike toward $90 stay contained as a geopolitical headline trade, or does it start bleeding into rate expectations and consumer sentiment in a way that hits the homebuilder/small-cap bid B9's clients are exposed to?*
