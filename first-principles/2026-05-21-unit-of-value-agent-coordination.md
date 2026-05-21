# Spike: What is the correct unit of value in agent-to-agent coordination?

**Date:** 2026-05-21
**Question:** What is the correct unit of value in agent-to-agent coordination — the task, the token, or the outcome?
**Delta category:** rediscovered
**Confidence:** 0.82

---

## First-Principles Answer

### Setup: what must a unit of value satisfy?

Value in any exchange must be (a) measurable by both parties, (b) agreed upon upfront, and (c) proportional to the actual utility delivered to the recipient. If the unit fails any of these, the exchange system develops perverse incentives.

### Candidate 1 — Task

A task is an instruction: "summarize this doc," "score this lead," "draft this email." Tasks appear clean — they have scope and a definition of done. But tasks are **value-indifferent**. Two tasks with identical specifications can produce wildly different utility (summarizing a grocery list vs. a $10M contract). Tasks also ignore effort asymmetry — a trivial task and a multi-hop research task are the same "unit." Paying per task creates incentives to subdivide work artificially or to technically satisfy a spec without delivering real value.

### Candidate 2 — Token

Tokens measure computational substrate consumed — they are uniform, real-time metered, and auditable. This is appealing because it makes cost transparent. The fatal flaw: **tokens measure cost, not value**. This is the labor theory of value error. A 50-token response that closes a deal is worth more than a 50,000-token analysis nobody reads. Token-denominated payment incentivizes padding — verbose, sycophantic, elaborated output that inflates token count without increasing utility. Worse, as models improve, the same useful output requires fewer tokens, making the unit deflate over time. Token pricing is a proxy for cost, not a measure of value.

### Candidate 3 — Outcome

An outcome is a verified state change: "meeting booked," "lead scored above threshold," "invoice approved and sent." Outcomes are:
- **Model-agnostic** — it doesn't matter whether it took 100 tokens or 10,000
- **Aligned with the requester's actual utility** — you pay for the thing you actually wanted
- **Verifiable by both parties** — the state change either happened or it didn't

Outcome-denominated coordination resolves the principal-agent incentive gap. The sub-agent cannot game the metric by padding or technical compliance — it must deliver the actual state change.

### The three-layer hierarchy

All three units exist simultaneously, but at different architectural layers:

| Layer | Unit | Who cares |
|---|---|---|
| Compute | Token | Model provider |
| Protocol | Task | Agent-to-agent message passing |
| Value exchange | Outcome | Orchestrator ↔ sub-agent contract |

The coordination error is **conflating layers** — pricing at the token layer when value is at the outcome layer. This is like paying a contractor by the hour (token) when you hired them to build a wall (outcome). Hour-billing creates slow contractors; token-billing creates verbose agents.

### First-principles conclusion

The correct unit of value in agent-to-agent coordination is the **outcome** — defined as a verifiable state change agreed upon at the coordination boundary. Tasks and tokens are implementation details and cost proxies respectively, not value units. Any multi-agent system that prices coordination in tokens or undifferentiated tasks will develop systematic incentive misalignment.

---

## Corpus Answer

**IMF Note 2026/004** and **Nevermined's agent payment guide** both confirm that the "most advanced" payment model charges for outcomes rather than resource consumption, citing:
- $5 per meeting booked by a sales agent
- 3% of order value processed by a procurement agent
- 10% of cost savings identified by an optimization agent

**Berkeley EECS** (principal-agent alignment research) documents how reward functions that diverge from actual stakeholder values create misaligned agents — exactly the token-padding and task-gaming failure modes I derived.

**arxiv multi-level value alignment survey (2025)** notes the shift toward multi-agent organizational governance: "alignment is engineered through systems that define objectives, intervention rights, accountability, and success metrics upfront" — which maps to outcome specification at coordination boundaries.

**A2A protocol** (joined Linux Foundation AI in Dec 2025) targets inter-agent task delegation — the protocol layer — without prescribing the value layer, consistent with my framing that tasks belong at the protocol layer, not the value layer.

---

## Delta Analysis

**Category: rediscovered**

The first-principles chain arrived independently at the conclusion the corpus confirms: outcome-based pricing is the correct unit of value at coordination boundaries. The reasoning path was consistent with the corpus findings.

**Possible novel element:** The explicit three-layer hierarchy (compute=token, protocol=task, value=outcome) does not appear verbatim in the searched corpus. The corpus describes the outcome preference but does not clearly articulate *why* tasks and tokens fail as value units using a layered architecture framing. This layering may be a useful explanatory primitive for designing the Construct agent ecosystem.

---

## Commentary

For the wolf-dashboards / Construct agent ecosystem specifically: when AP delegates to Vector, Forge, Signal, or any sub-agent, the contract should be specified as an **outcome** (what state change must be true when the sub-agent is done), not a token budget or a task list. Token budgets belong in operational constraints, not the value exchange. This distinction matters as the ecosystem scales — a sub-agent paid in tokens will always find ways to use more tokens.
