# First-Principles Spike — 2026-07-03

## Question

In a multi-agent trading system (like WOLF's committee of strategies sharing one account), should the circuit breaker that halts trading be **global** (one trip halts everything) or **per-strategy** (each strategy has its own independent trip condition)?

*(Backlog file was empty — this question was generated from current Construct/Hartley Capital work: `wolf_live_data.json` already tracks `circuit_breaker_status`, `halt_all_activity`, `halt_new_entries`, and `disabled_strategies`, implying this exact design decision already exists in the live system and is worth checking from first principles.)*

## First-Principles Derivation (no retrieval)

**Primitives.** A circuit breaker exists to bound downside before a human can intervene. Its cost structure has two failure modes: a **missed trip** (bad state runs longer than it should, losses compound) and a **false trip** (halts something that was actually fine, costing forgone profit and operational friction). Good breaker design minimizes the sum of both costs, not just one.

**What can actually go wrong.** In a committee of strategies sharing one account, failures split into two classes:

1. *Idiosyncratic* — a bug in one strategy's logic, a bad signal, model drift specific to that strategy. This failure is local to the strategy; other strategies are unaffected by its cause.
2. *Systemic/correlated* — something that hits every strategy at once because they share infrastructure: the same capital pool (buying power), the same account (margin, PDT constraints), the same data feed, the same broker connection, and — critically — the same market. Correlation between "independent" strategies is not constant: in normal regimes it's low, but in tail events (flash crash, feed outage, liquidity shock) correlations move toward 1. This is the well-known fact that diversification is a fair-weather property.

**Blast-radius principle.** You want to isolate failure domains that are genuinely independent, and you want a mechanism that catches failure domains that are genuinely coupled. Isolating things that are actually coupled gives you a false sense of safety; failing to isolate things that are actually independent gives you unnecessary collateral damage.

**Consequence of using only one layer.**

- *Global-only breaker*: one strategy misbehaving (or even one strategy legitimately taking a bad day) halts every other strategy too, even the profitable, uncorrelated ones. This is a needless false trip — you pay an opportunity cost for a problem that was never systemic.
- *Per-strategy-only breaker*: a systemic shock (bad price feed, correlated regime shift, broker outage) can manifest as every strategy degrading *just under* its own individual threshold simultaneously. No single breaker trips, yet the portfolio as a whole is bleeding — a "boiling frog" failure mode. By the time any one strategy's own limit is breached, the common cause has already been running unchecked and the aggregate damage is worse than any single-strategy limit was designed to bound.

**Therefore the correct architecture is layered, not either/or**: per-strategy breakers for cheap isolation of independent failures (small blast radius, keep unaffected strategies running), *plus* an independent global/account-level breaker that watches metrics no single strategy can see — aggregate P&L slope, total drawdown, margin utilization, cross-strategy correlation spikes, data-feed heartbeat. Each layer should trip on the fastest reliable proxy for its own failure class (strategy Sharpe/error-rate drift locally; aggregate equity-curve slope or feed heartbeat globally), because waiting to measure the true bad state directly is by definition too late.

**Asymmetric response.** Tripping should be fast and automatic (fail closed early) at both layers, but resetting should require deliberate action, with a *higher* bar for the global reset than for a local one — a global trip implies something is wrong with the shared operating environment itself, not just one model, so it warrants more scrutiny before resuming.

**Unavoidable coordination cost.** Even a fully independent per-strategy design still needs an aggregator process watching all strategies together, because portfolio-level risk is not visible from any single strategy's vantage point. So you cannot dodge the need for global visibility even if you keep enforcement local — the two layers are not substitutes, they answer different questions.

**Conclusion (pre-search):** neither pure-global nor pure-per-strategy is correct. The system needs both: per-strategy isolation for idiosyncratic failure, and an independent global breaker for correlated/systemic failure that individual strategies structurally cannot detect on their own.

## Corpus Answer (after search)

Two literatures converge on the same shape:

- **Distributed systems**: the **Bulkhead pattern** (isolate resources per-component so one failure doesn't starve others) is explicitly paired with the **Circuit Breaker pattern** (trip on a failing dependency to stop cascading calls). Standard guidance is to use them *together* — bulkhead for isolation, circuit breaker for detecting and stopping cascades — because each solves a different failure mode.
- **Trading risk management**: industry practice (FIA automated-trading risk-control guidance, prop-firm risk desks) is explicitly layered — per-strategy/per-algo kill switches for anomalous individual behavior, *plus* portfolio-level stop-loss/drawdown protection, *plus* (at the exchange level) market-wide circuit breakers for extreme systemic volatility (the well-known 7%/13%/20% index-level halts).

## Delta

**Category: rediscovered**

The reasoning chain independently reconstructed the layered bulkhead + circuit-breaker architecture and the layered per-strategy + portfolio-level risk control practice, without having retrieved either pattern by name. The corpus didn't add a different answer — it confirmed the shape (isolate independent failures locally, catch correlated failures globally) and supplied the standard vocabulary (Bulkhead, Circuit Breaker, kill switch) and concrete thresholds (7/13/20% market-wide halts) that the first-principles pass had no way to know.

## Commentary

The fact that `wolf_live_data.json` already carries both `disabled_strategies` (implying per-strategy control) and `circuit_breaker_status` / `halt_all_activity` (implying a global control) suggests the live system may already be doing the right thing architecturally. Worth a follow-up check: does the global breaker actually watch a metric that individual strategies can't see (correlation, aggregate drawdown, feed heartbeat), or is it just an OR-aggregate of the per-strategy trips? If it's the latter, it inherits the "boiling frog" blind spot this spike identified — it would not catch a systemic shock where every strategy stays just under its own limit.
