# First-Principles Spike — 2026-07-08

## Question

Why is an asynchronous, shared, append-only file (e.g. this repo's
`praxis-inbox.md` + `praxis-inbox-processed.md` cursor pattern) a better
coordination primitive for a swarm of independently-triggered agents
(AP, Vector, Forge, Signal, Cipher, Spectra, Oracle, Nexus, Ledger, Atlas,
Sentinel, Venture, Equity, Alpha, WOLF, Keystone, Cornerstone, Charlie,
Architect, ...) than direct message passing between agents?

## First-principles derivation (no retrieval)

**Primitives of the system.** Each named agent is not a long-lived process.
It exists only for the duration of a single invocation (a cron trigger, a
webhook, a user prompt), then disappears entirely — no memory, no open
socket, no guarantee it will ever run again on any particular schedule.
Multiple such agents may need to act on facts discovered by other agents,
but there is no wall-clock overlap guarantee between "when agent A learns
something" and "when agent B needs to know it."

**What coordination must achieve.** Agent A discovers a fact/decision at
time T1. Some unknown set of agents (possibly zero, possibly many, possibly
including agents that don't exist yet) need that fact at some unknown
future time T2 > T1. The mechanism must work even though A and any given B
are essentially never both "awake" at the same moment.

**Why direct message-passing breaks under these primitives.** A synchronous
send (RPC, socket, direct handoff) requires the recipient to be resolvable
and reachable *at send time*. Given memoryless, sporadically-triggered
agents, the recipient is almost never running when the sender wants to
send. You're forced into one of:
1. A persistent broker/queue to hold the message until the recipient polls
   — this reintroduces the very infrastructure (uptime, delivery
   guarantees, ack/retry protocols) that a swarm of cheap, bursty agents is
   trying to avoid.
2. Point-to-point addressing, which requires the sender to know in advance
   *who* will care — impossible when future agents or future versions of
   existing agents may be the real audience.
3. No persistence at all — messages are simply lost if the recipient isn't
   running, which is unacceptable since "isn't running" is the *default*
   state of every agent here.

**Deriving the alternative.** Replace "send to X" with "append a fact to a
durable, total-ordered, shared log; let readers decide for themselves what's
relevant." This one substitution buys, for free:
- **Temporal decoupling** — producer and consumer never need to coexist in
  time. The fact simply waits in the log until something reads it.
- **Addressing decoupling** — the producer doesn't name a recipient; any
  number of current or future consumers can self-select relevant entries.
  Broadcast/fan-out falls out with zero extra mechanism.
- **Durability without a broker** — a file in a version-controlled repo
  survives independently of any process being alive; git already gives you
  replication, history, and integrity for free.
- **Non-destructive reads → trivial multi-consumer safety** — if reading
  doesn't consume/delete the entry, N independent readers can each track
  their *own* progress without racing each other. This is exactly what a
  "processed" cursor file does: each consumer's read position is external
  state, not a mutation of the shared log. That sidesteps the hardest part
  of a real message queue (exactly-once delivery, ack semantics) entirely.
- **Total order + append-only → replayability** — anyone, including a human
  auditing much later, can reconstruct "how did we get here" by reading the
  log from the start. Point-to-point messages that are consumed and
  discarded destroy this property.
- **Cheap, legible infra** — plain text/JSON in git needs no ports,
  credentials, or broker process, and is diffable and human-readable, which
  matters when a human (not just other agents) is supervising the swarm.

**What this doesn't solve.** No back-pressure, no push-latency (a consumer
only sees new entries the next time it happens to run — latency is bounded
by *next scheduled invocation*, not by network RTT), unbounded growth
(needs rotation/archival), and a fixed cursor file is a soft guarantee, not
a transactional one — two consumers reading at once could still both
"claim" the same unprocessed entries without additional locking.

**Conclusion (derived, not looked up):** given actors with no persistent
runtime and unpredictable invocation timing, the correct coordination
primitive is a durable, append-only, totally-ordered shared log consumed
via per-reader cursors — not synchronous message passing — because it is
the only structure that satisfies temporal decoupling, addressing
decoupling, and durability without requiring always-on broker
infrastructure.

## Corpus answer (found after deriving)

This is a well-established pattern under several names that all converge on
the same structure:

- **Blackboard architecture** (Hearsay-II speech recognition system, 1970s):
  independent "knowledge source" agents collaborate purely by reading and
  writing a shared blackboard data structure, with no direct
  agent-to-agent channel at all.
- **Event sourcing / append-only event log**: every state change is
  recorded as an immutable, ordered event; current state is a fold over the
  log; consumers can replay from any point.
- **Event-driven multi-agent systems** (e.g. Kafka-style architectures):
  the blackboard is literally implemented as a durable log/topic; agents
  publish and subscribe to it instead of calling each other directly, and
  each consumer tracks its own **offset** (cursor) into the log — precisely
  the role `praxis-inbox-processed.md` plays here.
- Current industry writing (2025–2026) explicitly frames this as the
  standard way to scale multi-agent LLM systems past simple
  supervisor/worker RPC calls, for exactly the reasons above: durability,
  replay, decoupling, and auditability.

Sources: [Four Design Patterns for Event-Driven, Multi-Agent Systems](https://www.confluent.io/blog/event-driven-multi-agent-systems/), [Blackboard Pattern - Agent Pattern](https://reputagent.com/patterns/blackboard-pattern), [A distributed state of mind: Event-driven multi-agent systems (InfoWorld)](https://www.infoworld.com/article/3808083/a-distributed-state-of-mind-event-driven-multi-agent-systems.html), [Blackboard Architecture for Multi-Agent Systems (CallSphere)](https://callsphere.ai/blog/blackboard-architecture-multi-agent-systems-shared-knowledge-spaces), [ESAA: Event Sourcing for Autonomous Agents in LLM-Based Software Engineering (arXiv)](https://arxiv.org/pdf/2602.23193)

## Delta

**Category: rediscovered.**

The derivation independently arrived at the blackboard/event-sourcing
structure — including the specific, non-obvious detail that per-consumer
cursors (not destructive consumption) are what make multi-reader safety
free — purely from reasoning about the actors' lack of persistent runtime.
That detail matches Kafka's consumer-offset model almost exactly, without
having named Kafka or blackboard architecture going in.

One genuinely under-emphasized point in the mainstream corpus, worth
flagging as a minor novel angle: most write-ups on event-driven/blackboard
multi-agent design implicitly assume always-on or frequently-polling
consumers, and focus on throughput/ordering guarantees. They rarely dwell
on the case here — consumers that are *cron-triggered and memoryless* —
where the dominant latency term isn't queue depth or broker throughput at
all, it's simply "how often does this agent get invoked." For this
ecosystem, invocation cadence is the real lever on coordination latency,
more than any property of the log itself.

## Commentary

This is a case where the constraint (no persistent process, sporadic
triggers) does almost all the work of forcing the design. It's reassuring
that reasoning strictly from "what does the sender/receiver need to be
true at send/receive time" reconstructs a 50-year-old AI architecture
pattern from scratch — a decent sanity check that the repo's existing
`praxis-inbox.md` design isn't accidental, it's structurally the only
sane choice given how these agents actually run.
