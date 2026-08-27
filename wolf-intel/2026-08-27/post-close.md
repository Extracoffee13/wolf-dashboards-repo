# WOLF Post-Close Recap — 2026-08-27

## Data provenance (read this first)
- No WOLF Pre-Market Brief exists in this repo for 2026-08-27. Signal post-mortem below is therefore a gap-flag, not a pass/fail — there was nothing on record to grade against.
- No Alpaca connector is available in this session (no Alpaca MCP tool registered). Position/P&L pull skipped per runbook — **no positions tracked this run**. The `wolf_live_data.json` and `scout_state.json` files in this repo are stale (last touched 2026-06-24 and 2026-06-16 respectively) and were not used as a substitute for live data.
- Index/sector/earnings data below pulled via live web search this run. Several primary quote sources (Yahoo Finance, CNBC, Investing.com, StockAnalysis, TheStreet, Benzinga) returned `EGRESS_BLOCKED` from this session's network proxy, so exact intraday closing prints for the 12 Brand 9 client tickers individually (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC) could not be confirmed and are **not** reported as hard numbers below — flagged explicitly rather than guessed.

## Index closes (2026-08-27)
- **S&P 500**: 7,673.04, **+0.42%**
- **Dow Jones Industrial Average**: 53,195.36, **+0.83%**
- **Nasdaq Composite**: 26,168.46, **+0.39%**
- **Russell 2000 (RTY)**: could not confirm today's exact close (sources blocked). Context: RTY set a 2026 record close of 3,052.85 on 8/13, then pulled back roughly 2% into the 3,000–3,010 zone by mid-to-late last week on the rising 50-day MA. Treat today's RTY level as unconfirmed until verified at the open tomorrow.

Tape read: broad, tech-led up day off a big overnight NVDA beat. Dow's +0.83% outpacing SPX/Nasdaq is a bit unusual for a "chips lead" day — points to broad participation, not just mega-cap tech carrying the index (financials/industrials also firm on the CNBC recap).

## Sector heatmap
- **Leaders**: Technology (XLK) — reported up as much as +2.3% intraday on the NVDA/CRM/CRWD/OKTA earnings wave; semis and software both bid.
- Note on conflicting reads: an earlier mid-session snapshot (Investrade) had "10 of 11 sectors lower" with defensives (Healthcare, Utilities, Staples) lagging as money rotated into semis/software — this matches the final tape (rotation into tech, defensives sold) even though the index-level close was positive across the board once the NVDA move broadened out intraday.
- **Laggards**: Defensives — Healthcare, Utilities, Consumer Staples — as flows rotated out of safety and into risk/tech.

## The NVDA/CRM/CRWD earnings wave (reported Tue/Wed after close, traded today)
- **NVDA**: Q2 revenue $96.2B vs $92.27B consensus; adj. EPS $2.22 vs $2.09 est. Guided Q3 revenue to ~$108B vs $103.9B street. Beat estimates for a 15th straight quarter. Stock +4% AH Tuesday, extended to **+7-9% in today's session**, adding roughly $400-440B in market cap — the single biggest driver of today's tape.
- **CRWD**: Q2 revenue $1.47B vs $1.44B est; adj. EPS $0.31 vs $0.29 est; revenue +26% YoY. Popped +11% AH, then **+18% intraday today** — one of its biggest single-day gains on record. AI-driven security demand cited as the growth driver.
- **CRM (Salesforce)**: reported in the same window; specific print not independently confirmed this run (search access limited) — direction was net-positive per the "software roars back" framing in coverage, but treat the exact beat/miss numbers as unconfirmed.

## Brand 9 client tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)
**Could not pull individual closes/volumes today — flagging rather than fabricating.** What's confirmed instead:
- Homebuilder-sector proxy data (ITB/XHB) came back as YTD/1yr performance only, not today's daily print — not usable for a same-day read.
- Active live catalyst in the space: reporting this week (as of 8/22) that the administration is weighing **inflation-indexing of capital gains and an expanded home-sale exemption** (unchanged since 1997) — a real potential tailwind for existing-home turnover and, by extension, builder sentiment. This is a standing story, not confirmed to have moved specifically today.
- No confirmation either way that Brand 9 client names were in the leader or laggard column today. Action item: verify LEN/KBH/DHI/PHM/TOL closes directly against a broker feed before publishing anything ticker-specific to clients.

## Signal post-mortem (WOLF Pre-Market Brief)
No pre-market brief was found in this repo for 2026-08-27 (`wolf-brief/` only contains a `launch/` subfolder with onboarding copy, no dated brief). Nothing to grade — this is a process gap: the loop needs a same-morning pre-market brief written to a discoverable path before a post-close recap can do real signal attribution. Logged as the lesson below.

## After-hours earnings — reporting in the 16:00–16:30 ET window today
- **Marvell Technology (MRVL)** — reported after close today. Adj. EPS $0.94 vs $0.93 est. on revenue $2.74B vs $2.71B est. (double beat). Guided Q3 FY27 adj. EPS $1.10 (±5c) / revenue $3.15B (±5%) vs $1.08/$3.04B consensus — a beat-and-raise. **Stock reaction: sold off despite the beat**, dropping from ~$255.88 to ~$241.45 (-1.49%) as the print matched what was already priced into a +188% YTD run. Classic sell-the-news after an enormous run.
- **Autodesk (ADSK)** — reported today, Q2 FY27 (call at 2pm PT / 5pm ET). Revenue $2.05B, +16% YoY, above the $2.005–2.015B guide. GAAP EPS $2.33 (guide was $1.84–1.97), non-GAAP EPS $3.30 (guide $3.10–3.14) — clean beat and raise on FY27 targets.

## Tomorrow's overnight catalysts (Friday, 2026-08-28)
- **Jackson Hole — Fed Chair Kevin Warsh's inaugural keynote**, Friday 8/28. Reported timing varies by source (8:00am ET vs 10:00am ET — confirm exact time before the open). This is Warsh's first major address since becoming the 17th Fed Chair (succeeded Powell, seated May 2026) and lands with 10Y yields near 4.7%, inflation still sticky above target, and the September 16 FOMC live. Hawkish vs. dovish framing here is the single biggest swing factor for tomorrow's tape.
- 80 economic events and 17 earnings reports are on the docket for 8/28 per the general calendar sweep — specific pre-market earnings names for B9-relevant sectors were not individually confirmed this run; re-check a live earnings calendar before the open.
- Watch Asia/Europe open reaction to the NVDA/CRWD AI-capex re-rate — a "does the AI trade keep running into Warsh" setup.

## Tomorrow's setup analysis
- **Tape character today**: trend day, tech-led, broad participation (Dow +0.83% > SPX/Nasdaq is the tell that it wasn't just mega-cap chips carrying it). Not a range day, not a reversal day.
- **Levels broken/held vs. this morning**: no pre-market brief exists to check against — can't grade level-by-level. Flag for tomorrow's setup instead of a stale claim.
- **One-line tomorrow's key question**: *Does the rally survive Kevin Warsh's Jackson Hole debut, or does a hawkish first speech from a new Fed Chair reprice the AI-led melt-up?*

## Action items for the loop
1. Confirm exact Warsh speech time (8am vs 10am ET) before Friday's open.
2. Fix the pre-market brief pipeline — nothing was found at a predictable path today, which broke the signal-attribution half of this recap.
3. Wire up a live quote source (or Alpaca) that isn't proxy-blocked, so B9 client tickers get real closes instead of a data gap.
