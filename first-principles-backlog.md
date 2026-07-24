# First-Principles Backlog

Open questions for the daily First-Principles Spike. Each entry is a question
worth deriving from raw primitives (no retrieval) before checking it against
the corpus. Pull one per day, mark it done, add new ones as they surface.

## Open

- [ ] Signage industry: why do sign shops price by square footage rather than
      by materials-cost-plus-labor-plus-margin? What does sq-ft pricing
      implicitly encode about production economics and customer willingness
      to pay?
- [ ] Real estate: from first principles, why does commercial real estate
      value converge to NOI / cap rate rather than to discounted cash flow
      of the specific lease in place?
- [ ] Agent architecture: why does giving an agent a smaller, well-scoped
      tool surface tend to outperform giving it a larger one, even when the
      larger surface is a strict superset of capabilities?
- [ ] Brand 9 Signs operations: what is the first-principles argument for
      batching production runs vs. one-off fabrication, given fixed setup
      cost and variable per-unit material cost?
- [ ] Hartley Capital: is a fixed-percentage daily/weekly circuit breaker
      (as currently implemented) actually the right control, or would a
      volatility-normalized (ATR-based) breaker dominate it?

## Done

- [x] 2026-07-24 — Hartley Capital: what is the mathematically optimal
      fraction of capital to risk per position, and why do practitioners
      systematically bet less than that optimum? (Kelly criterion /
      fractional Kelly) — see `first-principles/2026-07-24-kelly-criterion-position-sizing.md`
