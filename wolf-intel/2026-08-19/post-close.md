# WOLF Post-Close Recap — 2026-08-19

## Index closes (vs. prior close)

| Index | Change |
|---|---|
| S&P 500 | +0.43% |
| Nasdaq Composite | +0.40% |
| Dow Jones Industrial | +0.25% |
| Russell 2000 | **-1.30%** |

Source: TheStreet's Aug 19, 2026 market wrap ("S&P 500 rises despite tech weakness as health care, cyclicals jump") and a Spokesman-Review/Reuters wire pickup ("Wall Street recovers as yields ease; Moderna lifts healthcare stocks"). No direct exchange feed available this run (see Data Confidence below) — these are search-sourced, not Alpaca/Bloomberg-verified.

**Read:** large-cap indices green, Russell 2000 down over a point — this is a narrow, defensive-led bounce, not broad risk-on. Small caps did not confirm the rally.

## Why: the driver

Treasury announced it will more than double the size of its long-bond buybacks, easing the surge in long-end yields (the 30-year had hit its highest level in nearly two decades just yesterday, 8/18, driving Tuesday's tech-led selloff). Lower yields today gave equities room to bounce.

## Sector heatmap

**Led:**
- Healthcare: +2.9%, a fresh record high for the sector — the single biggest support to the index. Moderna surged on positive vaccine trial data; Merck +12%.
- Consumer discretionary / communication services: firm. Notable gainers: Sherwin-Williams +2.8%, Home Depot +2.0%.

**Lagged:**
- Technology: continued weakness — roughly 35.6% of all US issues were declining mid-session, "almost all of them" tech names, extending Tuesday's chip-stock selloff.
- Industrials/financials soft: Caterpillar -2.2%, Goldman Sachs -2.0%, JPMorgan lower.

## Brand 9 client tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

**Data confidence: LOW.** No Alpaca/broker connector is configured for this run, and direct fetches to Yahoo Finance/CNBC quote pages were blocked by network egress policy. The figures below are pulled from search-engine result summaries and are **not exchange-verified** — treat as directional only, confirm against a live feed before acting on them.

Search-sourced moves (unconfirmed):
- LEN: ~-3.5%
- PHM: ~-1.8%
- DHI: ~-2.7%
- KBH: ~+2.5%
- TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC: no reliable same-day figures returned.

**Flag:** if directionally correct, this is a notable divergence — the homebuilder cohort did *not* participate in today's yields-down bounce the way the standard "lower yields → homebuilder bid" playbook would suggest (only KBH green, and Home Depot's strength suggests some housing-adjacent demand read-through even as the pure-play builders lagged). This needs same-day chart confirmation tomorrow morning before treating it as real signal rather than a data artifact.

## Signal post-mortem — today's WOLF Pre-Market Brief

**No pre-market brief file exists in this repo for 2026-08-19** (checked `wolf-brief/`, `wolf-intel/`, and full git history — no file matching a premarket/pre-market pattern for today or any prior date). This appears to be the first run of the `wolf-intel`/post-close pipeline in this repo.

**This is itself a process gap, named:** either the AM brief didn't run today or it ran somewhere that never got committed to this repo. Either way, there is nothing to grade signals against for today's post-mortem. Fixing the AM→PM handoff (both briefs landing in the same repo) is a prerequisite for real signal accountability going forward.

## After-hours earnings (16:00-16:30 ET window)

- **Webull (BULL)** — confirmed 4:15pm ET report. Framed pre-earnings as the cleanest read on retail options/crypto risk appetite (~$3.6B market cap, exposure to both). No verified beat/miss/guide or AH price reaction was found via search this run — check premarket for the AH move.
- Broader calendar showed ~51 companies reporting on 8/19; no complete after-the-bell list with results was retrievable via web search. Recommend a dedicated earnings-calendar pull (Yahoo/TipRanks/Seeking Alpha calendars) next run rather than general search.

## Tomorrow's overnight/AM catalysts (2026-08-20)

- **08:30 ET — Initial jobless claims** (consensus ~265K)
- **08:30 ET — Philadelphia Fed manufacturing index** (August; consensus recovering to ~-5.0 from -12.3 in July)
- **10:00 ET — Existing home sales** (July; consensus ~4.85M annualized SAAR, down from 5.12M) — **directly relevant to the B9 homebuilder cohort**, first hard data point since today's builder-stock divergence.
- **13:20 ET — Kansas City Fed President Esther George** speaks
- **13:45 ET — Minneapolis Fed President Neel Kashkari** speaks
- Asia open: no reliable same-night futures/Nikkei-Hang Seng data retrievable via search at time of writing (most recent confirmed Asia data was from 8/17: Hang Seng +1.4%, Nikkei flat, Straits Times -0.9%, KOSPI flat). Check a live futures feed before the open.

## Tape read for tomorrow's setup

**Reversal/rotation day, not a trend day.** The bounce was narrow (healthcare-led, defensive) and small caps didn't confirm — that combination (large-cap green, RTY red) usually reads as short-covering/rate-relief in specific pockets rather than a durable risk-on shift. Treat today's strength as fragile until broadened.

No AM brief exists to check today's levels against, so "broken vs. held" can't be assessed this run — this should be fixable starting tomorrow if the AM brief pipeline is wired into this repo.

**Tomorrow's key question:** Does the 10am existing home sales print confirm or break the homebuilder cohort's weak divergence from today's easier-yield tape?

## Positions / P&L

No Alpaca connector is configured for this session (checked via connector list — none found). Per instructions, skipping the live position/P&L pull.

**No positions tracked this run.**

The repo's `wolf_live_data.json` and `scout_state.json` contain portfolio and options-relevant data, but both are stale (last updated 2026-06-24 and 2026-06-16 respectively) and were not treated as live for this recap.
