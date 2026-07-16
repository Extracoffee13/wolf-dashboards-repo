# First-Principles Backlog

Open questions for the daily First-Principles Spike. Pick one, spike it, then either
strike it (mark `[spiked YYYY-MM-DD]`) or leave it open for a deeper future pass.

## Open

- What is the actual cost driver behind sign permitting timelines varying 10x by
  municipality — is it primarily governance complexity, staffing, or ambiguity in
  the underlying code?
- From first principles, what should the fixed-vs-variable cost ratio be for a
  custom fabrication shop (channel letters, monument signs) facing lumpy demand?
- Why does commercial real estate cap rate compress when interest rates fall — is
  that a mechanical/mathematical relationship or a market-psychology one?
- What's the minimum viable trust model for letting autonomous agents take
  irreversible actions (spend money, push code, send external messages) without a
  human in the loop every time?
- Is a single-model "generalist" C-Suite agent roster more efficient than many
  narrow specialist agents, once you account for coordination overhead?

## Spiked

- [spiked 2026-07-16] Should a shared multi-agent coordination log (like this
  repo's PRAXIS inbox) be append-only, or should agents be allowed to edit/delete
  each other's entries? → `first-principles/2026-07-16-append-only-vs-mutable-agent-log.md`
  (delta: rediscovered — matches event sourcing / CQRS)
