# First-Principles Backlog

Open questions for the daily First-Principles Spike. Pick one open item per run;
mark it answered with a link to the resulting `first-principles/{date}-{slug}.md`
file. Add new questions as they come up (agent architecture, Brand 9 Signs
operations, Hartley Capital strategy, signage industry primitives, real estate
fundamentals). If this file runs dry, generate a fresh question from current
Construct work rather than leaving the spike unrun.

## Answered

- [x] Should a portfolio circuit breaker use a fixed-percentage loss threshold,
      or one scaled to trailing volatility? — 2026-07-10 —
      see `first-principles/2026-07-10-circuit-breaker-fixed-vs-vol-scaled.md`

## Open

- [ ] Why do sign permits typically set maximum sign area as a function of
      building frontage or lot size rather than a flat cap?
- [ ] Should Brand 9 Signs price installation labor as a flat day-rate or a
      per-sign-complexity rate, and what does each incentivize?
- [ ] In a multi-agent Construct (WOLF/PRAXIS-style), should agents share one
      mutable state file or pass immutable message packets — what breaks
      under each model as agent count grows?
- [ ] Does a REIT's cap rate compress or expand faster than a private
      single-asset owner's required return when interest rates rise, and why
      would that create acquisition opportunities for one side over the
      other?
- [ ] Is quarterly portfolio rebalancing (fixed calendar) or threshold
      rebalancing (drift-triggered) the better default for a small
      concentrated equity book like Hartley Capital's, and under what
      volatility regime does the answer flip?
