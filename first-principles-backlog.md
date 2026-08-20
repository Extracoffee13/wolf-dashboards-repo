# First-Principles Backlog

Questions for the daily reasoning-gym spike. Derive from primitives **before** touching
the corpus. Move a question to **Spiked** when its artifact lands in `first-principles/`.

## Open

### Agent architecture
- What is the minimum durable unit of agent memory — and what makes a memory worth keeping
  versus re-deriving on demand?
- Why do multi-agent systems degrade as agents are added? Where is the actual ceiling?
- When should an agent retrieve versus derive? What's the decision rule?
- What is the correct failure mode for an agent that cannot verify its own output?

### Hartley Capital / WOLF
- Does WOLF's circuit breaker re-arm on calendar rollover? *(Direct follow-up from the
  2026-08-20 spike — flagged as the highest-leverage unverified item in the risk stack.)*
- What is the right position-sizing rule for a portfolio whose edge decays at an unknown
  rate?
- What makes a position size "too large" independent of any volatility estimate?

### Brand 9 Signs operations
- What actually sets the floor price of a custom sign — and why do quotes cluster at
  multiples of material cost?
- What is the real unit of value in signage: the object, the permit, or the install?
- Why does signage lead time resist compression?

### Real estate fundamentals
- What is the true economic function of a real-estate broker, stripped of convention?
- What determines the correct hold period for an asset, from primitives?

## Spiked

- **2026-08-20** — Where does a drawdown circuit breaker belong in an autonomous trading
  agent, and what sets its threshold? → `novel` (framing over rediscovered substance) —
  [artifact](first-principles/2026-08-20-drawdown-circuit-breaker-threshold.md)
