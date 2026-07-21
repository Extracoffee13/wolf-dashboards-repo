# WOLF Post-Close Recap — 2026-07-21

**Data note:** This run had no live Alpaca connector and no live market-data terminal (FMP was installed but not enabled in this session's tool chat). All figures below are sourced from public web search/news aggregators. Where sources conflicted or a number could not be confirmed, it's flagged rather than guessed. `wolf_live_data.json` in this repo is stale (last updated 2026-06-24) and was NOT used as a stand-in for today's data.

---

## 1. Index closes

| Index | Close | % chg |
|---|---|---|
| S&P 500 (SPX) | 7,489.64 | +0.62% |
| Nasdaq Composite (NDX proxy) | 25,785.36 | +1.09% |
| Russell 2000 (RTY) | 2,965.02 | +0.77% |

Bounce day. Monday (7/20) sold off on Iran-war escalation and rising oil; today recovered most of that as chip stocks rebounded and earnings season took over the narrative from geopolitics. Nasdaq led on a "chip stocks revive" rotation (Yahoo Finance, 24/7 Wall St).

## 2. Sector heatmap

**Confidence: low.** Aggregator (StockTitan) sector table and the index closes above are inconsistent with each other — the sector table shows only Energy positive (+1.16%) with 10 of 11 sectors red (Communication Services worst, -1.78%), which doesn't square with SPX +0.62% / NDX +1.09% closes. Likely a stale or mistimed snapshot on the aggregator's side.

Best-effort synthesis pulling from multiple sources:
- **Energy** led — oil spiked >2% intraday on Iran conflict / Houthi Red Sea blockade threats (Brent >$89, WTI ~$82).
- **Tech / semis** likely closed positive given "chip stocks revive" was the explicit Nasdaq-leadership narrative in two independent sources — this contradicts the StockTitan table's -1.09% Tech read, another reason to discount that table.
- **Consumer Discretionary** lagged (-1.62% per StockTitan) — consistent with homebuilder softness on DHI's guidance cut (see below).
- **Communication Services** weakest in the StockTitan read (-1.78%) — unconfirmed elsewhere, treat as low-confidence.

Don't publish precise sector percentages externally today — the underlying data isn't clean enough to stand behind.

## 3. Brand 9 client tickers (homebuilders)

Tracking: LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

| Ticker | Read | Confidence |
|---|---|---|
| **DHI** | Reported FQ3'26 before the open: EPS $3.20 beat ($2.97 est), revenue $9.23B beat ($9.1B est). But cut FY26 revenue guidance to $32.5–33.0B (from $33.5–34.5B), home-closings guide down to 83,800–84,300 (from 86,000–87,500), and guided Q4 revenue $8.8–9.3B vs. $10.05B consensus — big miss on the forward number. Stock popped premarket (+2.15% to $147.90) on the EPS beat, then reporting suggests it faded through the session (one source: -3.1%) as the guidance cut sank in. Net: **beat-and-cut, stock likely gave back the premarket pop.** | Medium — beat/guide numbers confirmed by two independent sources; exact closing price/% not confirmed. |
| **KBH** | ~$55.79, +0.68% (~+$0.37) | Medium |
| **LEN** | Traded in a $81.58–$84.16 range; exact close not confirmed | Low |
| **PHM** | Conflicting reads across sources (one has it +2.89% on a "gained" day, another has it "registering a bigger fall than the market") — can't reconcile which session each refers to | Low — do not use |
| **TOL** | Headline read: "TOL dips while market gains" — directionally down vs. the tape | Low |
| **MTH, TPH, NVR, BZH, MDC, MHO, TMHC** | No confirmed data found this run | None |

**Read:** DHI is the story — it's the largest homebuilder and its guidance cut (affordability pressure, cautious buyers, rising incentives) is a legitimate sector-wide signal, not company-specific. That the group broadly lagged the tape (Consumer Discretionary underperforming on an up day) is consistent with the market reading DHI's guide as read-through for the whole cohort, even as DHI's own headline EPS beat.

## 4. Pre-Market Brief signal post-mortem

**No record found.** This repo has no `wolf-intel` history prior to today and no public WOLF Pre-Market Brief for 2026-07-21 could be located via web search (checked Substack directly — nothing under "WOLF Brief"). Either the Pre-Market routine didn't publish today, publishes somewhere not searchable/indexed, or this is simply the first day this recap pipeline has run. **Flagging this as a process gap** — can't grade signals that weren't captured anywhere this recap can reach. Recommend the Pre-Market Brief routine also commit its output to this repo (e.g. `wolf-intel/{date}/pre-market.md`) so post-close has something concrete to grade against.

## 5. After-hours earnings (16:00–16:30 ET window)

- **Capital One (COF)** — reported Q2'26 after the bell. EPS $4.42 vs. $4.50 est (miss), revenue $15.23B vs. $15.35B est (miss). Early read has shares down modestly (~-1.5%). YTD COF is down ~15% into this print on credit-quality/macro concerns — a miss here doesn't help that narrative. **Confidence: medium** (numbers came from one aggregator, not cross-confirmed).
- **Alaska Air (ALK)** — reported after the close. Consensus was a $0.99/share Q2 loss vs. $1.78 profit a year ago; implied options move was a large ±15%. Actual results not confirmed this run — high-vol name, watch for a large gap tomorrow.
- **Annaly Capital (NLY)** — scheduled to report; implied move ±2.7%. Actual results not confirmed this run.

## 6. Tomorrow's overnight catalysts

- **Asia:** Nikkei 225 jumped +3.26% to 66,231 today (Topix +2.44%) as chip/AI names led a recovery from last week's selloff — read-through is constructive for tomorrow's US semis open if it holds through the Asia session.
- **Geopolitics — the dominant overnight risk:** US has now struck Iranian targets for 10 consecutive nights; Iran has retaliated against US positions in Bahrain, Kuwait, and Jordan; Houthis are threatening a Red Sea blockade of Saudi maritime traffic. Oil (Brent >$89, WTI ~$82) is the transmission channel into equities — any escalation overnight (or de-escalation/ceasefire headline) is a bigger swing factor than any scheduled data release right now.
- **Earnings:** more than 15 S&P 500 names reporting this week; pre-market tomorrow includes continued Q2 season flow. Watch ALK's actual print and guidance for a read on travel demand.

## 7. Tape read / setup assessment

- **Tape type:** Reversal/recovery day off Monday's geopolitics-driven selloff, not a clean trend day — led by a single catalyst (chip rebound + oil pulling back off highs) rather than broad participation. The sector data (however messy) points to narrow leadership, not a broad risk-on day.
- **Levels:** No confirmed morning-brief levels to check against (see §4). Flagging rather than fabricating a "held/broke" call.
- **Tomorrow's key question:** **Does the Iran conflict escalate or cool overnight — and does that override earnings as the tape's driver again?** Secondary question for the Brand 9 book: does DHI's guidance cut get echoed by the rest of the homebuilder cohort this week, or does the group stabilize once the initial read-through fades?

## 8. Alpaca positions / P&L

No positions tracked this run — no Alpaca connector available in this session. The `wolf_live_data.json` file in this repo is a month stale (2026-06-24) and should not be read as current.
