# First-Principles Backlog

Open questions for the daily First-Principles Spike. Pick one, derive an answer
from primitives with no retrieval, then search the corpus and compare. Move a
question to "Spiked" with a link once it has an artifact under `first-principles/`.

## Open

- Is a linear rebalancing band (e.g. "rebalance when any position drifts >5pp
  from target") the right rule, or should band width scale with each
  position's own volatility?
- What is the minimum information a sign-installation crew actually needs on
  a work order to avoid a truck roll — derived from the install steps
  themselves, not from what a template happens to include?
- Does a real-estate cap rate compress or expand as a market's construction
  permitting friction increases, holding rent growth constant?
- Why does a circuit-breaker / kill-switch threshold belong on a *rate*
  (loss per day) rather than a *level* (absolute drawdown from peak), and
  when does that stop being true?
- Should a multi-agent system's error-handling live in each agent or in the
  orchestrator — derived from where the information needed to decide "retry
  vs. escalate" actually lives?

## Spiked

- 2026-09-24 — Should a weekly loss circuit-breaker threshold be 5x the daily
  threshold (linear) or some other multiple? → `first-principles/2026-09-24-circuit-breaker-scaling.md`
