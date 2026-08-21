# First-Principles Spike — 2026-08-21

## Question

Should a multi-agent system coordinate via a shared append-only log
("blackboard") or via direct point-to-point messages between agents? This is
directly relevant to this repo's own `praxis-inbox.md` mechanism, where
agents (AP, Vector, Forge, Signal, Cipher, Spectra, Oracle, Nexus, Ledger,
Atlas, Sentinel, Venture, Equity, Alpha, WOLF, Keystone, Cornerstone,
Charlie, Architect) append packets to a shared file rather than messaging
each other directly.

## First-principles answer (derived before any search)

Start from primitives: N agents, each with partial information and
autonomous execution, needing to influence and be influenced by others over
time. Communication carries three costs — attention (reading takes
agent-time), coupling (a dependency on another agent's identity/availability
creates fragility), and coordination overhead (deciding who talks to whom,
when). Failure modes to design around: an agent going offline mid-exchange,
messages arriving out of order, a new agent joining with no shared history,
and — critically for a system humans must supervise — the need to
reconstruct *why* a decision was made after the fact.

Point-to-point messaging (A sends directly to B) requires A to know B's
address, and scales as O(N²) potential links as the fleet grows. If B is
offline, the message is lost unless a durable queue is bolted on. If C later
needs the same information, C must have been explicitly CC'd — there's no
way to retroactively discover it. This is fine for small, stable,
tightly-coupled pairs, but breaks down as membership grows or turns over,
which is exactly the shape of a fleet still being built out.

A shared append-only log (blackboard) decouples producer from consumer in
both time and addressing: A writes without knowing who reads; B reads
whenever it comes online, even much later; a brand-new agent onboards simply
by reading history, no special introduction needed. It gives durability
(nothing is lost if the reader isn't running), auditability (anyone —
including a human — can reconstruct the full decision trail), and a natural
mechanism for resolving conflicting claims via write order. This is
essentially the blackboard architecture from classical AI systems, and it's
the same tradeoff distributed systems make between RPC (synchronous,
point-to-point, used when an immediate reply is required and tight coupling
is acceptable) and event sourcing/pub-sub (asynchronous, decoupled, used
when producers and consumers should not need to know about each other and
replay/audit matters more than latency).

The cost of the log approach is that every reader pays attention-cost
proportional to total log volume, not just what's relevant to it — unless a
subscription/filter layer is added, which reintroduces some point-to-point
structure. And without compaction or summarization, the log grows
unboundedly and old entries become effectively unreadable context. This
predicts a need for something like the "processed" file split observed in
this repo (`praxis-inbox.md` vs `praxis-inbox-processed.md`) — a consumer
offset/checkpoint, the same idea as Kafka consumer offsets: mark what's been
consumed without destructively dequeuing.

**Prediction:** for a fleet of loosely-coupled, asynchronously-scheduled
agents that don't need synchronous replies from each other but do need
durability and human-auditable history, an append-only shared log is the
correct choice over direct messaging — and the specific failure modes to
watch for are unbounded growth (needs periodic compaction/summarization) and
lack of a subscription mechanism (every consumer re-scans and re-filters the
whole log, cost growing linearly with total writes even when only a few
entries are relevant to it).

## Corpus answer (searched after the above was written)

Web search on blackboard architecture, point-to-point messaging, event
sourcing, and pub/sub confirms the same shape of answer:

- **Blackboard**: agents interact indirectly through a shared, structured
  workspace; agents self-select and contribute based on evolving shared
  state, which "enhances both flexibility and scalability" and decouples
  every phase from every other. Documented downside: "if the problem is
  large, the blackboard can become huge and each agent has to navigate
  through a lot of information to find what matters to it" — needs careful
  state management. This matches the predicted unbounded-growth /
  no-subscription-filter failure mode exactly.
- **Point-to-point**: "With N agents, you get N(N-1)/2 potential
  communication paths. Ten agents create 45 connections... Consensus
  protocols add overhead that grows quadratically with agent count." This
  matches the O(N²) scaling argument derived above.
- **Event sourcing**: "durable sequence of events that can be replayed or
  consumed by different services at different times... ideal for
  event-driven architectures that require audit logs, playback, or state
  rebuilding" — matches the durability/auditability claim.
- **Pub-sub**: "the messaging system doesn't need to know about any of the
  subscribers" — matches the identity-decoupling claim.
- **Hybrid**: "Many real-world systems actually combine these patterns...
  use a queue for one-to-one communication... but use pub-sub to notify
  multiple services of important events, and use an event stream to
  maintain a long-term record." This matches the derived conclusion that
  tightly-coupled synchronous two-party exchanges should use direct
  messaging while broadcast/audit-worthy decisions should go to the shared
  log.

Sources:
- [Multi-agent systems: Why coordinated AI beats going solo](https://redis.io/blog/multi-agent-systems-coordinated-ai/)
- [Patterns for Democratic Multi‑Agent AI: Blackboard Architecture — Part 1](https://medium.com/@edoardo.schepis/patterns-for-democratic-multi-agent-ai-blackboard-architecture-part-1-69fed2b958b4)
- [Grokking Messaging Patterns: Queues, Pub/Sub, and Event Streams](https://www.designgurus.io/blog/message-patterns)
- [Event-driven architecture with Pub/Sub — Google Cloud](https://cloud.google.com/solutions/event-driven-architecture-pubsub)
- [Event-Driven Communication Patterns on AWS](https://www.martinrichards.me/post/eda_for_the_rest_of_us_communication_patterns/)

## Delta category: rediscovered

The first-principles derivation arrived independently at the same
conclusion the corpus documents: blackboard/log for decoupled broadcast +
audit trail, point-to-point for tightly-coupled synchronous exchange, and a
hybrid combining both in practice. It also independently predicted the two
specific failure modes the corpus names (unbounded blackboard growth
requiring state management; O(N²) point-to-point scaling) and drew the
correct analogy between this repo's inbox/processed-file split and a
consumer-offset checkpoint pattern (e.g. Kafka), without having looked any
of that up first.

## Commentary

This isn't "noise" — the reasoning didn't just restate a trivial fact, it
derived a specific architectural judgment (including a concrete prediction
about *this repo's* design and its likely failure mode) purely from
communication-cost primitives, and that judgment held up against the
established literature on blackboard systems, event sourcing, and pub/sub.
The corpus doesn't yet document the specific recommendation that a
per-agent fleet like this one should keep the log for broadcast/audit and
selectively add point-to-point *only* for the rare case where an agent
needs a synchronous answer before proceeding — that combination is implied
by the "many systems combine these patterns" note but not spelled out with
this specificity in what was found. That's a thin edge toward "novel" but
not enough on its own to override "rediscovered," since the core answer
(blackboard for decoupled/async/audit, point-to-point for tight coupling,
hybrid in practice) is squarely the orthodox one.
