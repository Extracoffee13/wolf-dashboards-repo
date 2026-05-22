# WOLF Brief — Committee Edition
## Week of May 18–22, 2026
*Published Friday, May 22, 2026 · Post-close*

---

## THE THESIS OF RECORD

**The AI infrastructure trade is intact. The book is not.** Energy (XLE +5.48%) and medical devices (MDT +3.62%) led the portfolio this week while Tesla (-3.95%) and the enterprise AI names (PLTR flat, MSFT slightly negative) gave back ground. The market is sending a clear signal: we are in mid-cycle consolidation, where quality-growth and real-yield assets outperform the speculative AI froth. The rotation is real. The problem is that WOLF's book is not positioned to capture it — PLTR sits at 47.6% of the portfolio, the cash line is -$100K on margin, and the entire fund has been on MANUAL HALT all week. The thesis is right. The execution has been wrong.

**Monday morning, this fund has exactly one job: rebalance.** mandate_rebalance.py fires at 9:31 AM. PLTR trims from 364 shares to ~61. MDT from 333 to ~106. TSLA closes entirely — the signal is broken and the cost-basis is punishing. Proceeds wipe the margin and put cash in positive territory for the first time since the fund launched. Once the circuit breaker goes green, the 52-Week High Breakout strategy (Sharpe 1.91 — best in the book) is free to scan. The first new entry is XLE at a mandate-compliant 8% weight: energy sector rotation thesis, 60-90 day hold, stop at $56.40, target $66. That's a 2.1:1 R:R on the cleanest signal in the system.

**The 30-90 day macro call is cautious risk-on, not a charge.** The Generalist sees energy and healthcare outperformance continuing into Q3 as the Fed holds rates and institutional capital seeks yield with duration protection. The Quant agrees the signals are there — XLE momentum, NVDA AI-capex confirmation, 52-Week Breakout gated but ready. The Skeptic correctly flags the kill scenario: if PLTR guides down on a government contract miss or AI spending scrutiny, a 47.6% concentration at current sizing means a single bad print wipes out months of gains. The committee did not dismiss that risk. It voted to act on it Monday morning.

---

## THE VOTE

| Role | Vote |
|------|------|
| The Generalist | Neutral |
| The Quant | Neutral |
| The Skeptic | **Risk-Off** |
| The Operator | Neutral |

### **COMMITTEE DECISION: NEUTRAL — 3 to 1**

**Skeptic dissent on record:** If mandate_rebalance.py does not execute by Monday 10:00 AM ET, the Skeptic's Risk-Off stance takes effect immediately and all new entries are blocked. The committee's Neutral vote is contingent on rebalance execution.

---

## THE TRADE IDEA

**XLE — Energy Sector Rotation**
- **Entry:** $59.50 (current) or better on Monday open post-rebalance
- **Position size:** 8% of book (~$8,350 at current AUM)
- **Stop:** $56.40 (entry cost basis; -5.2% downside)
- **Target:** $66.00 (energy sector rotation thesis, 90-day hold; +10.9% upside)
- **R:R:** 2.1 : 1
- **Hold horizon:** 60–90 days
- **Signal source:** Sector ETF Rotation strategy (Sharpe 1.69, max DD -7.1%, backtested real Alpaca data). XLE was top-3 of 11 SPDR sectors by 20-day momentum.
- **Conviction:** Medium-high. Energy sector momentum is confirmed by XLE's 5.48% outperformance in the book this week. The risk is a reflationary surprise unwinding the defensive rotation.

**Secondary:** TSLA — Close entirely Monday. Signal broken (-3.95% from entry $442.45). EV demand thesis is under pressure from competition and margin normalization. No meaningful catalyst to hold. Freeing the capital is more valuable than the position.

---

## THE KILL CRITERION

**What would have to be true by next Friday, May 29, for this thesis to die:**

1. **PLTR drops >15% on a guidance miss, government contract loss, or AI spending scrutiny.** At 47.6% current concentration (pre-rebalance), this would wipe 7%+ from total book and trigger the weekly circuit breaker. If this happens before Monday's rebalance fires, the thesis is not just dead — the fund is in drawdown territory that requires a 100% gain to recover. This is the Skeptic's point. It is a real risk.

2. **Mandate_rebalance.py fails to execute Monday and the halt persists a second week.** If the operational rebalance does not fire, the fund remains gated from its best strategy (52-Week Breakout, Sharpe 1.91) and the committee's Neutral vote becomes the Skeptic's Risk-Off by default. A second week of mandate non-compliance is not a thesis — it is a failure of execution.

3. **Energy reverses on a macro shock.** A Fed "no cut in 2026" statement, a China demand slowdown signal, or an OPEC supply surge would reverse XLE quickly. The 5.48% gain in XLE is a real signal, but if the energy rotation unwinds simultaneously with a tech drawdown, the fund has no hedge. Both legs of the rotation thesis fail at once.

---

## 90-DAY P&L SCOREBOARD
*WOLF Committee calls vs. SPX — tracking accountability*

| # | Date | WOLF Thesis | WOLF Call | SPX Ref | Result | vs SPX |
|---|------|-------------|-----------|---------|--------|--------|
| 001 | 2026-05-22 | Neutral: Rebalance first, then XLE rotation. TSLA close. 52W Breakout unlock. | **NEUTRAL** | *[Record SPX close Monday 5/25]* | Open | TBD |

*Scoreboard tracks each committee's weekly call against the SPX weekly return. A "correct" call: Risk-On week + SPX positive, or Risk-Off week + SPX negative, or Neutral when SPX is within ±1%. Will be updated each Friday.*

*Next data point: 2026-05-29 committee will score this call.*

---

## WHAT TO WATCH NEXT WEEK

- **Monday 9:31 AM:** mandate_rebalance.py execution — circuit breaker goes GREEN or the Skeptic's Risk-Off applies
- **PLTR:** Any news on government contracts, AI spending, or enterprise software guidance
- **XLE / Energy:** Oil prices, OPEC meeting signals, demand data from China
- **Fed speakers:** Any hint of rate path for Q3 2026 will move the rotation thesis materially
- **52-Week High Breakout scanner:** Once the halt clears, this is the signal to watch for the next entry

---

*WOLF Brief is the public-facing synthesis of the WOLF AI Hedge Fund Committee's weekly deliberations. Strong opinions. Named tickers. Tracked accountability.*
*Committee session transcript: `wolf-intel/committee/2026-05-22-week-of-2026-05-18.md`*
