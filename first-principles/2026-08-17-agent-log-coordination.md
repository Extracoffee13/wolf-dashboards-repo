# First-Principles Spike — 2026-08-17

## Question

Why should independent agents in a multi-agent system (like Construct's
Praxis ecosystem — AP, Vector, Forge, Signal, Cipher, Spectra, Oracle,
Nexus, Ledger, Atlas, Sentinel, Venture, Equity, Alpha, WOLF, Keystone,
Cornerstone, Charlie, Architect) coordinate through a shared append-only
log (the `praxis-inbox.md` pattern already in this repo) rather than
through direct point-to-point messages between agents?

## First-principles answer (no retrieval)

Start from the primitive: coordination is the transfer of a decision or
observation from a producer to whichever consumers need it, plus enough
shared context for the consumer to trust and interpret it. There are only
two topologies available to move that information: point-to-point (A
addresses B directly) or shared-log (A appends to a common store; anyone
reads at will). Reasoning through the consequences of each:

**1. Wiring cost.** With N agents that might need to exchange information,
point-to-point in the worst case requires O(N²) channels — every pair that
might need to talk needs a path. A shared log requires O(N): one write path
and one read path per agent, independent of how many others care. This is
the same reason airline networks use hubs and why publish/subscribe exists
as a pattern — a hub converts an all-pairs problem into a one-to-hub
problem.

**2. Coupling and discovery.** Point-to-point requires the producer to know
its consumers in advance (or maintain a subscriber list) — if a new agent
is added, every producer that agent needs to hear from must be told to
address it too. This is temporal and referential coupling: producer code
must know about consumers that may not exist yet. A log inverts this —
producer doesn't need to know who reads, consumer doesn't need to know who
wrote. That decoupling is essential for a roster that is still growing (the
inbox already lists ~19 named agents as potential readers).

**3. Ordering and causality.** Many agent decisions depend on "what
happened before" — a lesson logged by one agent presupposes a mistake
logged earlier by another. A shared append-only log gives a total order for
free: appends happen in sequence, so "before/after" is just position in the
file. Scattered point-to-point messages across N² channels have no natural
global order; reconstructing causality would require a separate
synchronization primitive (vector clocks, agreed timestamps).

**4. Durability and replay for stateless agents.** LLM agents in this
ecosystem are frequently instantiated fresh per session with no built-in
memory between runs. If coordination happened over direct messages, a
freshly spawned agent has no way to recover what it missed — that history
is simply gone to it. A log persists the messages as data: a new instance
reads the whole history and reconstructs context. The log isn't just a
communication channel here, it's the memory substrate for otherwise
memoryless agents.

**5. Auditability.** A human operator or a meta-agent needing to answer
"what did the agents decide, and why" needs one place to look. Point-to-point
communication forces an auditor to enumerate every channel and merge
timelines after the fact. A log gives a single linear read.

**6. Failure isolation / backpressure.** If a direct recipient is slow or
broken, the sender either blocks or has to buffer and retry — producer
throughput becomes entangled with consumer health. With a log, the
producer's only obligation is a successful append; each consumer pulls on
its own schedule, so N consumers' readiness never gates the producer.

**7. What's lost.** Immediacy — nothing pushes a notification unless
something also watches the log. Fine-grained targeting — by default
everyone sees everything, unless the log is partitioned by topic. And
unbounded growth — a log that's never pruned makes every future read more
expensive; it needs an archival/rotation step (which is presumably why this
repo already has both `praxis-inbox.md` and `praxis-inbox-processed.md`
side by side).

**Synthesis.** A shared append-only log is the right primitive exactly when
the agent population is open-ended, agents are frequently stateless and
need to recover context on spin-up, a single audit trail matters, and
messages are advisory rather than latency-critical control commands.
Point-to-point remains the right choice for tight synchronous request/response
loops where only one recipient is relevant and an answer is needed now, not
eventually.

## Corpus answer

This is the standard architecture pattern known by several names depending
on lineage:

- **Event sourcing** (state changes recorded as an immutable, appended
  event log serving as the single source of truth; current state is
  reconstructed by replay).
- **"The log as a unifying abstraction"** — the log-centric architecture
  popularized for distributed data systems (Kafka-style): a single
  append-only log decouples every producer from every consumer, gives a
  total order, and supports both live subscription and historical replay
  from the same store.
- **Blackboard architecture**, from classical AI (Hearsay-II era):
  independent "knowledge sources" read and write to a shared blackboard
  rather than messaging each other directly — closely mirrors what
  Praxis's inbox pattern is doing with named agents as knowledge sources.
- **Pub/Sub and CQRS** as the general messaging-pattern framing of the same
  decoupling argument.
- A related, older precursor I did not derive independently: **Linda's
  tuple spaces** (generative communication) — producers and consumers
  coordinate through a shared, content-addressable space without naming
  each other at all, an even more decoupled ancestor of the log pattern.

Current multi-agent-LLM writeups (event-driven multi-agent system posts,
2026) converge on exactly the same benefits list derived above: loose
coupling, audit trail, replay-based resilience/recovery, and multiple
consumers reacting to one event without the producer needing to know about
any of them.

Sources:
- [Four Design Patterns for Event-Driven, Multi-Agent Systems](https://www.confluent.io/blog/event-driven-multi-agent-systems/)
- [Event Sourcing: Architecture Pattern for Auditability and State Management](https://zylos.ai/research/2026-02-17-event-sourcing-architecture-pattern/)
- [A distributed state of mind: Event-driven multi-agent systems](https://www.infoworld.com/article/3808083/a-distributed-state-of-mind-event-driven-multi-agent-systems.html)
- [Multi-Agent Systems | Shared Persistent State](https://medium.com/@aiforhuman/multi-agent-systems-shared-persistent-state-bd33a1b5030f)

## Delta category

**rediscovered** — the first-principles chain (wiring cost → coupling →
ordering → durability/replay for stateless agents → auditability → failure
isolation) landed independently on the same architecture the corpus already
has a name for (event sourcing / log-as-unifying-abstraction / blackboard
architecture). The one piece not derived independently — Linda's tuple
spaces as a decoupling precursor — is a minor corpus addition, not enough
to call the overall delta novel.

## Commentary

The reasoning chain is worth keeping because it explains *why* the
`praxis-inbox.md` file already in this repo is structurally correct rather
than just conventional: the ecosystem's actual constraint is stateless,
frequently-respawned agents with an open-ended and growing roster, which is
precisely the condition under which log-centric coordination beats direct
messaging. It also flags a real gap worth a future spike: the log has no
visible partition/topic mechanism yet, so as agent count and message volume
grow, every agent pays the read cost of every other agent's traffic. The
`praxis-inbox.md` / `praxis-inbox-processed.md` split is the only pruning
mechanism present today, and it looks like a manually-triggered archive
rather than a size- or time-based rotation policy.
