# WOLF Post-Close Recap — 2026-08-26

Compiled after 16:00 ET close. Data pulled via web search against CNBC, Yahoo Finance,
TipRanks, and company IR/press coverage — WOLF is not wired to a live tick feed for
indices/equities, so treat prices as end-of-day-accurate, not tick-precise. Where a
number couldn't be confirmed, it's flagged rather than guessed.

## 1. Index close

| Index | Close | Chg | % |
|---|---|---|---|
| S&P 500 (SPX) | 7,675.70 | -1.58 | -0.02% |
| Dow Jones Industrial | 53,463.88 | -113.52 | -0.21% |
| Nasdaq Composite (NDX proxy) | 26,151.30 | +171.11 | +0.66% |
| Russell 2000 (RTY) | 3,009.96 | +14.88 | +0.50% |

Read: a rotation day, not a trend day. S&P essentially flat, Dow the laggard, while
Nasdaq and small-caps both pushed higher — breadth was fine (8 of 11 S&P sectors
closed green) even though the megacap-weighted Dow didn't participate. Tape was
holding its breath into NVDA/CRM/CRWD prints after the bell; sticky July PCE (+3.7%
y/y, a touch above estimate) capped upside and kept rate-cut hopes in check most of
the session.

## 2. Sector heatmap

- **Led:** Information Technology (+1.03%)
- **Lagged:** Energy (-1.25%), pressured by falling oil prices
- 8 of 11 GICS sectors closed higher on the day
- Notable single names: Meta whipsawed on a $17B legal settlement (popped, then gave
  back most of the gain); Abercrombie & Fitch +40% on an earnings beat and raised
  full-year guide

## 3. Brand 9 client tickers (homebuilders) — close

| Ticker | Close | % chg |
|---|---|---|
| LEN | $92.38 | -1.16% |
| DHI | $138.33 | -0.35% |
| PHM | $118.09 | -0.46% |
| TOL | $145.61 | -1.79% |
| KBH | $55.36 | -1.25% |
| NVR | — | -2.25% |
| BZH | — | -1.50% |
| MHO | — | -3.44% |
| TMHC | — | -0.03% |
| MTH, TPH, MDC | not confirmed this run | — |

The whole vertical was red-to-flat despite the NAHB/Wells Fargo Housing Market Index
ticking up to 35 from 34 in August — sticky inflation data kept the rate-cut narrative
that homebuilders need in check, and that outweighed the modest sentiment uptick.
**The homebuilder bid did not follow through today.** MTH/TPH/MDC closes weren't
confirmed via available sources this run — don't treat their absence as "flat," it's
a data gap, not a signal.

## 4. Signal post-mortem — Pre-Market Brief

**Gap flagged:** no Pre-Market Brief file was found in this repo for 2026-08-26
(checked `wolf-intel/2026-08-26/` and `wolf-brief/` before writing this file — neither
had a same-day AM brief committed). That means there's no fired/didn't-fire signal
list to grade against today. This is a pipeline miss, not a "no signals fired" result
— logging it as an error rather than skipping it silently. Action item: confirm the
AM pre-market scan is actually running and committing to this repo before tomorrow's
open, or this recap will keep hitting the same gap.

## 5. After-hours earnings (16:00–16:30 ET window)

**NVIDIA (NVDA)** — reported FQ2 FY27 after the close.
- Adjusted EPS $2.22 vs. $2.10 est — **beat**
- Revenue $96.22B vs. $92.17B est (guided ~$91B ±2%) — **beat, big**
- Stock reaction: **down** in extended trading (~-1.3% roughly 30 min ahead of the
  call), extending a soft final regular-session hour. This is the 5th straight
  quarter NVDA has sold off post-print despite meeting/beating — the "beat magnitude
  shrinking" story (13 straight guide-beats, but the beat's been shrinking from
  +22.8% in FQ2 FY24 to +4.6% last quarter) looks like it's still the market's
  overhang, not the headline number.

**Salesforce (CRM)** — reported FQ2 FY27 after the close.
- Revenue +11% y/y; net income $3.53B ($4.29/share GAAP), +87% y/y
- FCF +81% y/y to $1.10B vs. ~$643M consensus — big beat on cash generation
- Agentforce annualized revenue >$1.5B, +240% y/y; RPO $33.5B
- Q3 guide: adj. EPS $3.42–3.44 / rev $11.42–11.50B vs. $3.38 / $11.41B est — **beat
  and modest raise**
- AH stock reaction: not confirmed via available sources as of this file's compile
  time — flagging as unconfirmed rather than guessing.

**CrowdStrike (CRWD)** — scheduled ~4:05 PM ET, after the close.
- Guide going in: non-GAAP EPS $0.29, revenue $1.43–1.44B, net new ARR $284–286M
  (~28% growth at midpoint)
- **Actual print not confirmed via available sources this run** — search coverage
  was still all-preview at compile time. This is a real gap, not a "nothing to
  report" — check tomorrow's pre-market brief for the confirmed number before
  trading off any CRWD-adjacent thesis.

## 6. Alpaca positions / P&L

No Alpaca connection available in this session (no credentials/API tool wired up) —
**no positions tracked this run**. `wolf_live_data.json` in this repo is stale
(last_updated 2026-06-24) and was not used as a substitute for live data.

## 7. Tomorrow's setup

- **Tape character today:** rotation/consolidation day, not trend, not reversal.
  Breadth positive, index-level flat-to-up, waiting on the NVDA/CRM/CRWD print
  cluster to set direction.
- **Levels:** no AM brief exists for today (see §4), so there's no documented
  morning level to grade as broken/held. SPX closed essentially unchanged around
  7,676.
- **Overnight catalysts:** Asia opens into the NVDA/CRM/CRWD reaction — Nikkei 225
  closed today's own session +0.62% at 66,262 ahead of the U.S. prints, so watch
  the follow-through direction in Tokyo/Hang Seng trade tonight as the first read
  on how AI-capex sentiment digests the NVDA number.
- **Thursday earnings to watch:** Dollar General (DG), Dollar Tree (DLTR),
  Burlington (BURL), Best Buy (BBY), Marvell (MRVL), Autodesk (ADSK), Workday
  (WDAY), Affirm (AFRM), Ulta Beauty (ULTA), plus RY/TD out of Canada — exact
  AM-vs-PM split wasn't fully confirmed per name, verify before the print.
- **Tomorrow's key question:** does the "NVDA beats but sells off" pattern hold a
  5th straight quarter and drag the Nasdaq's outperformance back toward the Dow's
  flat/negative read, or does the Salesforce beat-and-raise give risk appetite
  enough cover to shrug NVDA off and keep the small-cap/tech bid going?
