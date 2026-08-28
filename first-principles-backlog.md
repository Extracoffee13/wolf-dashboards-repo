# First-Principles Backlog

Open questions for the daily First-Principles Spike. Each run pops one entry
(or, if this file is empty/stale, generates a fresh question relevant to
current Construct work) and moves it to `first-principles/{date}-{slug}.md`.

Format: one question per line, phrased so it has a checkable "orthodox
answer" to compare against (not pure opinion).

## Open

- Why does position sizing under a fixed daily-loss circuit breaker (see
  wolf_live_data.json `circuit_breaker_status`) converge to a Kelly-like
  fraction, and is a flat percentage buffer (1.7% daily / 3.1% weekly) the
  right first-principles shape for that breaker, or should it scale with
  realized volatility?
- FIFO vs. specific-lot-ID cost basis for tax-loss harvesting: from first
  principles, which lot-selection rule minimizes tax drag for a systematic
  harvester, and does the IRS default (FIFO absent an election) match that?
- What is the minimum information a signage fabricator needs from a permit
  set to quote accurately, derived from the physical production steps alone
  (fabrication, UL listing, install, electrical)?
- Cap rate as a real estate primitive: derive why cap rate ≈ discount rate −
  growth rate from the Gordon growth model, and check it against how brokers
  actually use cap rates in the field.
- Multi-agent architecture: from first principles, when does a shared
  blackboard (single mutable state store) beat point-to-point message
  passing between agents, and does that match how production agent
  frameworks (e.g. LangGraph, AutoGen) actually default?

## Consumed

(moved to first-principles/ once spiked — kept here as a log so the same
question isn't re-picked)
