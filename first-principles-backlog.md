# First-Principles Backlog

Open questions for the daily First-Principles Spike (see `first-principles/` and
`praxis-inbox.md`). Pick one open question per run, reason it out cold (no
retrieval), then check it against the corpus. Move finished items to Done with
a link to the spike artifact.

## Open

- Why do commercial sign permit review cycles run 4-8 weeks in most
  municipalities — what is actually being checked, and is there a faster
  process architecture that preserves the legitimate safety/aesthetic review
  without the queue time?
- From first principles, what should determine how a multi-agent system routes
  a task to an agent — capability match, cost/latency budget, or blast-radius
  of a wrong answer — and how should those three interact?
- Does a monument sign's price scale better with square footage, with
  illumination/electrical complexity, or with site/foundation conditions? What
  would a first-principles cost model predict vs. the industry's per-square-foot
  rule of thumb?
- From first principles, why does adding leverage to a real estate deal raise
  both expected equity return and equity return variance by the same lever
  ratio only under a specific assumption about debt cost — what breaks that
  symmetry in practice?
- What is the actual failure mode a personal guarantee on a small business
  loan is pricing for, and is a personal guarantee a rational substitute for
  collateral or mostly a signaling device?
- From first principles, should an agent architecture centralize memory
  (single shared store all agents read/write) or federate it (each agent
  keeps local state, syncs on demand) — what does the CAP-theorem-style
  tradeoff look like for a swarm of LLM agents specifically?

## Done

- 2026-09-07 — Why does a real estate cap rate move less than 1:1 with
  interest rates? — `first-principles/2026-09-07-cap-rate-interest-rate-sensitivity.md`
