# First-Principles Spike — 2026-06-03

## Question

**What is the minimum viable unit of trust in an agent-mediated signage supply chain — and how should it be priced?**

Context: Brand 9 Signs operations, Construct agent ecosystem, physical-digital handoffs between autonomous agents and production floor.

---

## First-Principles Answer (no retrieval)

### Primitives
- A supply chain is a sequence of value-transforming steps where each step depends on outputs from the prior step.
- Trust is the expected probability that a counterparty will perform as represented, weighted by the cost of non-performance.
- An agent (software or human) is a node that takes inputs, applies a decision rule, and emits outputs.
- Signage production has physical irreversibility: once vinyl is cut or a substrate is printed, rework costs material + labor.

### Chain of Reasoning

**1. What does "trust" protect against in a signage supply chain?**

Three failure modes:
- (a) *Spec drift* — the output doesn't match the order
- (b) *Timing failure* — materials don't arrive before install
- (c) *Quality failure* — output meets spec on paper but fails in the field (fading, adhesion, dimensional tolerance)

**2. Where do handoffs happen?**

Customer → Sales agent → Design agent → Production agent → Install agent → Customer sign-off. Each handoff is a trust event: the receiving agent must believe the emitting agent's output is correct.

**3. What is the minimum trust unit?**

The smallest handoff that, if it fails, causes irreversible cost. In signage this is the **spec lock** — the moment a design file is approved and sent to production. Before that point, changes are cheap (pixels). After it, changes cost material + labor.

The minimum trust unit is a single verified spec-lock event: a tuple of `(design_file_hash, substrate_spec, color_profile, install_location, deadline)`.

**4. Why hash-based verification?**

Downstream agents (production, install) cannot trust intent — they can only verify artifact identity. A hash makes the unit tamper-evident and machine-verifiable. Any mutation in the file breaks the hash, surfacing spec drift before material is committed.

**5. How should it be priced?**

Trust has an option value: the buyer is purchasing the right to not re-do the step.

```
trust_price = (rework_cost × P(failure_without_check)) + check_overhead
```

For signage:
- Average rework cost on a mid-size sign: ~$200 (material + 2hr labor)
- Estimated error probability without a formal lock step: 5–15% on complex multi-panel installs
- Fair option premium: **$10–30 per spec-lock event**
- In practice this is bundled into "design approval" line items rather than charged explicitly

**6. Does the same logic hold for agent-mediated (software) handoffs?**

Yes structurally, but the cost structure collapses. Software agents don't make material errors; they emit stale or mis-routed spec data. Verification becomes a cryptographic check (hash + schema validation) rather than a human review. The per-transaction cost approaches zero. The cost is a **one-time infrastructure investment** (schema definitions, validation pipelines) — not a per-handoff charge. This inverts the pricing model: instead of $10-30 per event, you pay once to build the gate and then the marginal cost of each subsequent trust event is negligible.

**7. Implication for Construct / agent architecture**

The agent ecosystem should enforce a spec-lock gate between the design agent and the production agent. This gate is the choke point for trust. Any agent upstream of it can be autonomous; any agent downstream of it should be deterministic. The lock event should be logged immutably (append-only log) so disputes can be arbitrated. The gate's economics justify the infrastructure investment as insurance against rework, not as a recurring fee.

---

## Corpus Answer (post-reasoning retrieval)

### Supply chain trust literature
- The canonical trust unit in supply chains is a **cryptographically signed artifact** — a hash bound to a producer identity, making each handoff tamper-evident and independently verifiable. (Minimus, arxiv 2510.04964)
- Blockchain-based immutable records are the standard mechanism for multi-party supply chains where each handoff needs documented chain-of-custody.

### Multi-agent systems literature (2025)
- The 2025 DMAS framework formalizes trust-aware communication using cryptographic primitives: signed payloads, on-chain verification, non-repudiation. (arxiv 2512.02410)
- OpenAI Agents SDK (March 2025) introduced explicit `Handoff` primitives with guardrails and tracing — closest to operationalizing the spec-lock concept.
- A "vouching with slashing" mechanism: agents sign handoff payloads accepting joint liability; downstream anomalies automatically degrade trust scores of every agent in the vouching chain.

### Signage industry
- Industry practice confirms design approval as the critical lock point; locked templates and approved libraries are the recommended pattern.
- Design files lacking standardized dimensions or complete specs produce "nearly inevitable" production issues. No public rework percentage data exists in industry literature.

---

## Delta Analysis

| Aspect | First-Principles | Corpus | Delta |
|---|---|---|---|
| Core trust unit | Hash tuple at spec-lock event | Cryptographic signed artifact | rediscovered |
| Economic pricing model | Option premium = rework_cost × P(error) | No economic model — treated as security concern | **novel** |
| Agent-mediated cost collapse | Per-transaction cost → zero; one-time infra cost | Not addressed | **novel** |
| Vouching / slashing mechanism | Identified need for immutable log | Full slashing/degradation model | corpus adds |

**Category: novel**

The cryptographic core was independently rediscovered (validating the reasoning path), but the economic framing — trust as an option premium on irreversibility, with agent-mediated costs collapsing to infrastructure-only — is absent from the corpus. This has direct operational value: it reframes "design approval" from a workflow step into a priced option contract, and justifies agent-gate infrastructure investment as actuarial insurance rather than overhead.

---

## Commentary

The most durable insight: **irreversibility is what makes trust expensive**. In any process with cheap reversibility, trust verification is overhead. In any process with expensive irreversibility, trust verification is insurance — and should be priced as such. The signage industry intuitively bundles this into approval fees without naming the mechanism. Naming it opens the door to unbundling, repricing, and eventually automating the gate at near-zero marginal cost.

For Construct: the spec-lock gate is not a bureaucratic checkpoint — it is the actuarially correct control point where trust cost is non-zero and defensible.

---

*Confidence: 0.72*
