# First-Principles Backlog

Open questions for the daily first-principles reasoning gym (`/first-principles-spike`).
No retrieval during Step 2 — reason from primitives, then check the corpus and log the delta.

Categories: Brand 9 Signs operations, Hartley Capital strategy, agent architecture,
signage industry primitives, real estate fundamentals.

## Open

- [ ] Why do circuit breakers in algo-trading systems (like WOLF's) use separate
      daily and weekly drawdown thresholds with different buffers, instead of a
      single rolling drawdown limit?
- [ ] What's the right unit economics primitive for pricing an LED channel-letter
      sign install — cost-plus-margin, per-square-foot, or value-based — and when
      does each break down?
- [ ] Cap rate vs. discounted cash flow: for a small commercial real estate
      acquisition (e.g. a signage shop's own building), when does the simpler
      cap-rate heuristic diverge meaningfully from a full DCF?
- [ ] Why gate a trading strategy's promotion to "approved" on a Sharpe ratio
      threshold (e.g. 1.0) rather than raw win rate or total P&L?
- [ ] What's the minimum viable governance structure for a holding company
      (Hartley Capital) overseeing operationally distinct subsidiaries (a
      signage business, a trading desk) without becoming a bottleneck?

## Done

- [x] 2026-06-30 — Why should a multi-agent system's shared coordination log
      (e.g. `praxis-inbox.md`) be append-only rather than mutable in place? —
      see `first-principles/2026-06-30-append-only-agent-coordination-log.md`
