# Spike: What is the minimum viable trust model for a multi-agent system where agents can write to shared state?

**Date:** 2026-06-09
**Slug:** minimum-viable-trust-multi-agent-shared-state
**Delta category:** novel

---

## Question

What is the *minimum* set of trust controls required for a multi-agent system to function without catastrophic, unrecoverable failures, given that all agents can write to shared persistent state?

**Why this matters for the current system:** The wolf-dashboards agent ecosystem has 15+ named agents all writing to praxis-inbox.md and other shared files via git. The trust model is currently implicit. This spike asks: what does the floor actually look like?

---

## Step 2 — First-Principles Derivation

### Starting primitives

**Trust** is a predictive belief: "this entity's future actions will not damage my objectives." It is always scoped (I trust you with this, not that) and always conditional. The question "minimum viable" reframes it as an engineering threshold: below which controls does the system experience catastrophic, unrecoverable failures?

**Shared state as deferred instruction.** When agent B reads state written by agent A, it is executing a deferred message from A. The temporal gap between write and read is the core vulnerability: A cannot constrain how B interprets the message at read-time, and B cannot verify A's intent at write-time. This is the fundamental asymmetry of shared-state trust — the writer is gone when the reader acts.

### The three catastrophic failure modes

| Failure mode | What breaks | Recovery? |
|---|---|---|
| **Impersonation** | Agent X writes state claiming to be agent Y → downstream agents act on false attribution | Hard — corrupted provenance chains |
| **Integrity violation** | State is modified between write and read → agents act on corrupted information | Hard — no way to detect what is real |
| **Injection** | Malicious content causes consuming agents to treat data as executable instructions | Catastrophic — arbitrary action execution |

Each is catastrophic in a distinct way. If you remove a control for any one of them, you can construct a concrete attack that is unrecoverable.

### Deriving minimum controls

**Control 1 — Storage-layer identity attribution (defeats impersonation)**

Self-reported identity is trivially spoofable: any agent can include "agent: WOLF" in its output regardless of which agent is writing. Identity must be enforced by the storage mechanism, not the writer's content. The storage layer must bind the write to the writer's identity independently of what the write says.

Minimum implementation: git commit author (enforced by the runtime environment, not the agent's output content) or namespace isolation where the storage layer rejects writes to namespaces an agent is not credentialed for.

What is NOT minimum: cryptographic signing of each write. Useful, but adds key-management overhead that can be satisfied more cheaply by storage-layer attribution in a controlled environment.

**Control 2 — Append-only log with hash linking (defeats integrity violation)**

If state can be modified after writing, you can't tell whether what you're reading is what was originally written. The minimum integrity control is a storage mechanism that makes post-write modification detectable.

Full cryptographic signing per write achieves this at higher complexity. Append-only storage with hash-linked entries achieves the same outcome at lower complexity: git's SHA chain means you cannot rewrite history without detection. All existing consumers who cached a previous SHA will notice the discrepancy.

The current system already satisfies this: git is an append-only, hash-linked log.

**Control 3 — Read-side data/instruction segregation (defeats injection)**

Injection is a consumer-side failure, not a producer-side failure. A writer can embed any content — you cannot prevent it with producer-side controls alone. The reader must maintain an architectural boundary: state read from shared storage is *data input*, never *executable instruction*, regardless of what the content says.

This means: consuming agents must parse state through a schema or structured extraction step before acting on it, never passing raw state content into their instruction context. The boundary is: state → structured data extraction → reasoning/action. Never: state → instruction.

This cannot be enforced by access controls. It must be an architectural invariant of every consuming agent.

### What is above the minimum (not strictly required)

- **Scope enforcement** (each agent can only write to its own namespace): reduces blast radius of a compromised agent but the system survives without it — damage is localized, not systemic
- **Dynamic trust scoring** (updating trust weights based on observed behavior): adds resilience but is above the catastrophic-failure threshold
- **End-to-end encryption of state**: privacy concern, not a trust failure mode in a controlled internal system
- **Human-in-the-loop gates**: valuable for high-stakes writes, but the system can operate autonomously without them

### First-principles conclusion

**Minimum viable trust = storage-layer identity attribution + append-only hash-linked log + read-side data/instruction segregation.**

Test: remove any one and describe a concrete unrecoverable attack. All three pass this test. Remove scope enforcement — damage is real but localized and recoverable. Scope is therefore above the minimum.

The current wolf-dashboards system partially satisfies this: git provides (1) commit-author attribution and (2) hash-linked append-only log. What is currently implicit, not architectural: (3) read-side data/instruction segregation. Agents reading praxis-inbox.md have no enforced boundary preventing them from treating inbox content as instructions.

---

## Step 3 — Corpus Answer

Research literature (2025–2026) frames multi-agent trust entirely under **"zero-trust" and "defense-in-depth"** paradigms:

**Key findings from the corpus:**

1. **Provenance ledgers** — Cross-Agent Multimodal Provenance-Aware Defense Framework (arxiv 2512.23557) uses a provenance ledger tracking metadata: modality, source, and trust level per message. Four cooperating agents: Text Sanitizer, Visual Sanitizer, Main Task Model, Output Validator.

2. **Sanitization at every boundary** — Standard finding: "architectural controls at every inter-agent communication boundary, as prompt-level defenses alone fail to prevent propagation of injections." Input sanitization + output validation per hop.

3. **Zero-trust inter-agent communication** — "Fortifying the Agentic Web" (arxiv 2508.12259) applies zero-trust to agent-to-agent calls: no implicit trust even within the same system.

4. **TRiSM framework** — "Trust, Risk, and Security Management in LLM-based Agentic Multi-Agent Systems" (arxiv 2506.04133) identifies that current orchestrations "assume baseline inter-agent trust without modeling its strength, authorization limits, or revocability, dynamic variability, contextual dependencies" — explicitly naming this as an industry gap.

5. **Dynamic trust scoring** — Binary trust scores per neighbor, updated via observed behavior; consensus measured by variance.

**Corpus framing:** Always additive. Every paper adds more controls; none asks "what's the minimum?" The corpus is written for security practitioners, not product engineers optimizing for minimal viable complexity.

---

## Step 4 — Delta

| My derivation | Corpus parallel | Status |
|---|---|---|
| Append-only hash-linked log | Provenance ledger | **rediscovered** |
| Read-side data/instruction segregation | Sanitization + output validation at boundaries | **rediscovered** |
| Storage-layer identity attribution | Provenance tracking per message | **rediscovered** |
| **"Minimum viable" framing — floor question** | Absent — corpus only asks "how much can you add?" | **novel** |

**Delta category: novel**

The individual primitives were rediscovered, confirming the reasoning chain is sound. The novel element is not a new primitive but a new *question shape*: "what is the minimum below which you have catastrophic failure?" is a product/engineering trade-off question. The security literature never poses it. Every paper frames trust as "add more layers," never as "what can you strip away and still survive?"

This framing matters for the wolf-dashboards system specifically: the system cannot afford defense-in-depth complexity on every write (15+ agents, high-frequency commits). Knowing the floor — the three non-negotiable controls — tells you what to harden first and what can wait.

**Practical implication:** The current system has controls 1 and 2 (git attribution + hash chain). Control 3 (read-side data/instruction segregation) is the gap. Any agent consuming praxis-inbox.md or similar shared state should route state through a structured parser before it enters the instruction context.

---

## Commentary

The "minimum viable" framing is itself a first-principles move: security research is written to persuade organizations to *add* controls, so it naturally frames everything as "you need more." An engineer asking "what's the least I can build and still have a safe system?" is asking a different question — one that the corpus cannot answer by its framing.

This suggests a general rule: when the corpus is all in one direction (add more X), the first-principles question to ask is "what is the minimum X?" — that's where the gap lives.
