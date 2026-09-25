# First-Principles Spike Backlog

Open questions for the daily First-Principles Spike. Pick one open (`[ ]`) item per
run, or add new ones as they come up in Construct work. Mark spiked items `[x]`
with the date and link to the artifact in `first-principles/`. See
`first-principles/log.jsonl` for the running index of past spikes.

## Trading / WOLF / Hartley Capital
- [x] 2026-09-25 — From first principles, why does the Kelly criterion determine optimal position sizing for a strategy with a known win rate and payoff ratio? → `first-principles/2026-09-25-kelly-criterion-position-sizing.md`
- [ ] Why does a circuit breaker on daily/weekly drawdown (e.g. -3%/-7%, as WOLF uses) outperform a pure per-trade stop loss for capital preservation?
- [ ] Why does diversifying across uncorrelated strategies (not just uncorrelated assets) reduce portfolio variance more than adding more capital to the best single strategy?

## Signage industry (Brand 9 Signs) primitives
- [ ] Why does a monument sign's legibility distance scale roughly linearly with letter height, and what's the underlying physics behind DOT sign-visibility standards?
- [ ] From first principles, why do master-planned communities need signage installed in a specific sequence (entry monument before wayfinding before unit/lot signage)?

## Real estate fundamentals
- [ ] Why does cap rate function as an inverse of a price/earnings multiple for income-property valuation?
- [ ] From first principles, why does leverage amplify equity returns faster than it amplifies risk in a low-rate environment, and where does that relationship invert?

## Agent architecture / Construct
- [ ] From first principles, why does a gatekeeper/approval layer (JEV) between agent decision and execution reduce total error rate versus a fully autonomous agent swarm?
- [ ] Why does fan-out/verify (multiple agents producing, one agent verifying) beat a single agent doing both generation and self-verification?
