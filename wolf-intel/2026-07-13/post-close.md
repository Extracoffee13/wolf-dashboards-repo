# WOLF Post-Close Recap — 2026-07-13

## Headline

Trump announced the U.S. is reinstating a blockade on Iranian shipping through the Strait of Hormuz — declaring the U.S. "GUARDIAN OF THE HORMUZ STRAIT" and floating a 20% fee on cargo transiting the waterway — as the Islamabad Memorandum ceasefire (signed June 17, following the April 8 truce) effectively collapsed this week. Iran struck three commercial ships July 6–7; the U.S. answered with a second straight night of "offensive" strikes; Iran retaliated against Jordan. Oil jumped, tech sold off hard, energy caught the bid. Equities closed lower across the board but well short of panic.

## Index Closes

| Index | Close | Change |
|---|---|---|
| S&P 500 | 7,515.34 | -0.79% |
| Nasdaq Composite | 25,873.18 | -1.55% |
| Dow Jones Industrial | 52,498.64 | -138.37 (-0.26%) |
| Russell 2000 | — | -0.83% |
| VIX | ~16.3–16.6 intraday (range 16.03–17.09) | up from 15.03 Fri close |

Dow's relative resilience vs. Nasdaq's -1.55% is the tell: this was a rotation out of high-multiple tech into energy/value, not an indiscriminate liquidation. VIX in the mid-16s is elevated but nowhere near the 25-30+ range that would signal capitulation — the tape is pricing this as a serious-but-contained reflare, not a rerun of the March 2026 shock (Brent hit $126/bbl that month, the largest oil supply disruption since the 1970s).

## Sector Heatmap

**Led:** Energy +1.37% — oil & gas the only sector group with a clean tailwind from the Hormuz headlines.

**Lagged:** Semiconductors/tech, badly —
- SK Hynix (US-listed) -9% (gave back most of Friday's +13% Nasdaq-debut pop)
- Sandisk -12%
- Intel -6%
- Seagate -5%
- Micron -4%
- AMD -4%

**Commodities:** WTI +3.3–3.5% to ~$73.8–73.9/bbl (crossed $75 intraday); Brent +3.3–3.5% to ~$78.5–78.7/bbl. Gold notably did NOT catch a safe-haven bid — futures -0.78%, spot -1.19% to ~$4,071 — consistent with the move being read as an inflation/rate-risk event (higher yields, firmer dollar) rather than a pure flight-to-safety event.

## Brand 9 Client Tickers — LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

**Data gap, flagged honestly:** verified today's-close prices/volumes for the individual B9 tickers were not obtainable through the tools available to this run (finance-quote endpoints returned 403s; no direct market-data connector is wired into this session). Rather than estimate individual moves, here is what's independently confirmed and directly relevant to the complex:

- Mortgage rates ticked **higher** today specifically on the Iran escalation — 30-yr fixed quoted ~6.6–6.7% across sources (NerdWallet, Mortgage Reports, U.S. News all filed "rates climb as Iran war reignites" pieces today). Bond yields up on oil-driven inflation risk is a direct, same-day headwind for the builder complex layered on top of the broader risk-off tape.
- Both proxy ETFs remain in established downtrends independent of today: XHB -7.9% YTD, ITB -10.5% YTD.
- NAHB builder confidence sits at 32 (June read) — an 18-month low, the 14th consecutive month below the 40 threshold, the longest such streak since 2011–2012.
- Net read: the setup was unfavorable for the group today (energy-driven rate spike stacked on already-depressed sentiment), but exact close-to-close attribution per ticker needs a real market-data feed next run — recommend wiring one in before the next post-close so B9 client names get real receipts, not inference.

## Signal Post-Mortem — WOLF Pre-Market Brief

No WOLF Pre-Market Brief was found committed to this repo for 2026-07-13 (checked `wolf-intel/`, `wolf-brief/`, and repo root for any file dated today). Without a morning brief to grade against, fire/no-fire attribution and error analysis cannot be performed this run.

This is a process gap, not a market observation: the post-close routine depends on the pre-market routine landing a dated file in-repo first. Recommend the pre-market brief writes to `wolf-intel/{date}/pre-market.md` (or equivalent) going forward so post-close has something to reconcile against.

For reference, `WOLF_Command_Center.txt` in the repo root carries example signals (TSLA short breakdown, NFLX long momentum breakout) but that file is a stale template (v1.6, dated 2026-04-14) — not today's live signal set — and was not used for grading.

## After-Hours Earnings (16:00–16:30 ET)

No notable reports landed in the immediate after-the-bell window today. Earnings-calendar sources show 26 companies reporting somewhere in today's session overall, but nothing high-profile hit the 16:00–16:30 ET slot. Volume picks up sharply from here: 25 tomorrow, 23 Wednesday, 32 Thursday, 11 Friday — and Tuesday specifically kicks off Q2 bank earnings (JPM, WFC, BAC, C, GS), which will matter more for tape direction than anything after tonight's close.

## Alpaca Positions / P&L

No Alpaca connector is wired into this session — skipping the live position/P&L pull. Note for the record: the `wolf_live_data.json` snapshot in this repo is stale (last updated 2026-06-24, ~3 weeks old: portfolio $90,479.48, daily P&L -$1,199.17/-1.31%, circuit breaker GREEN) and should not be treated as tonight's numbers. Recommend the Alpaca feed be reconnected to this environment, or the live-data JSON refreshed on a tighter cadence, so post-close can report real numbers instead of noting the gap every night.

## Tomorrow's Setup — Tuesday, 2026-07-14

**Tape read:** Rotation/risk-off day today, not a clean trend day — sector dispersion was wide (energy +1.37% vs. semis down mid-single-to-low-double-digits) and the Dow/Nasdaq spread (-0.26% vs -1.55%) points to a value-over-growth rotation rather than broad liquidation. Breadth was negative but not capitulation-grade; VIX confirms "elevated concern," not "panic."

**Levels vs. morning brief:** Cannot be assessed — no pre-market brief exists in-repo for today to compare against (see Signal Post-Mortem above).

**Overnight/tomorrow catalysts:**
- 6:00am ET — NFIB Small Business Optimism (June)
- 7:45am ET — ICSC weekly retail sales
- **8:30am ET — June CPI**: consensus headline -0.1% m/m (base effect from oil's -20.4% decline in June, before this week's reflare), core +0.2% m/m
- **10:00am ET — Fed Chair Kevin Warsh** testifies before the House Financial Services Committee
- 11:00am ET — Cleveland Fed CPI (June)
- Q2 bank earnings begin: **JPM, WFC, BAC, C, GS**
- 4:00pm ET — Net Long-Term TIC Flows (May); 4:30pm ET — API weekly inventory data
- Asia open: watch yen, oil, and chip/tech sentiment as the dominant cross-asset carryover from today
- Hormuz situation remains fluid — MarineTraffic showed six commercial vessels transiting in the past 24 hours despite the blockade rhetoric; any overnight escalation or de-escalation headline can reprice oil and futures before the cash open

**Tomorrow's key question:** Does June CPI confirm the disinflation base case and let bank earnings pull the tape's attention back to fundamentals — or does another Hormuz headline overnight force a second consecutive risk-off leg straight into the print?
