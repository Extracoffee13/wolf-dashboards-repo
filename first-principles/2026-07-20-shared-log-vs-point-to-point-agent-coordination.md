# First-Principles Spike — 2026-07-20

## Question

The backlog was empty at spike time, so this question was self-generated, taken directly from a pattern already live in this repo (`praxis-inbox.md`, the append-only cross-agent decision log used by AP, Vector, Forge, Ledger, and the rest of the Construct's ~19-agent roster):

> **Why should a multi-agent system coordinate through a shared append-only log rather than through direct agent-to-agent messaging?**

This is Construct-relevant on two levels: it's literally the mechanism this repo already uses (`praxis-inbox.md`), and it generalizes to any future decision about how WOLF, Brand 9 Signs agents, and Hartley Capital agents should hand information to each other as the roster grows.

## First-principles answer (derived before any search)

Start from primitives. Agents here are independent reasoning loops with bounded, private context, invoked intermittently rather than running continuously — a session spins up, does work, terminates. Coordination means ensuring each agent's actions account for relevant decisions made by other agents, without redundant or conflicting work. There are two basic topologies for moving information between agents: direct point-to-point messaging (sender addresses a specific receiver), and a shared structure both write to and read from (a log, blackboard, or inbox).

**A) Addressing cost.** Point-to-point requires the sender to know, at write time, every consumer who might care. In a system with ~19 named agents and presumably more to come, a sender (say AP, deciding on a pricing policy) can't enumerate every future consumer (Ledger for accounting, Cornerstone for real estate exposure, some not-yet-built agent). Point-to-point coupling is O(N×M) — every producer needs to know every relevant consumer. A shared log collapses this to O(N+M): producers write once, any number of readers subscribe independently, and new agents can be added without touching existing ones' code or prompts.

**B) Temporal decoupling.** These agents are not continuously running listeners; they are invoked per-task and exit. A point-to-point "send" would need the receiver to be live at that exact moment, or would need a buffering/retry layer to hold the message until the receiver next wakes up — and a general-purpose buffer-until-consumed mechanism is structurally just... a log. So for a system of sporadically-invoked, state-reset-between-runs agents, an append-only log isn't an alternative to messaging so much as the substrate that makes asynchronous messaging possible at all.

**C) Auditability.** For agents making consequential, semi-autonomous decisions (trading in WOLF, pricing/ops in Brand 9 Signs, capital allocation in Hartley Capital), being able to answer "why did the system do X, based on what, decided by whom, when" is close to a safety requirement, not a nicety. An append-only shared structure makes the audit trail a structural byproduct of the coordination mechanism itself. Point-to-point messages, once delivered and consumed, typically leave no trace unless every agent independently maintains its own log — auditability becomes an opt-in cost per agent instead of a free property of the system.

**D) Global ordering vs. availability.** A shared log is a single point of coordination: every agent reads from (roughly) the same canonical structure, so all agents can derive the same view of "what has happened so far." This creates a bottleneck/single-point-of-failure risk (a git conflict, an unavailable file) but buys a consistent global order — which matters the moment two agents' decisions could conflict (e.g., two agents both assuming they can spend the same budget). Pure point-to-point messaging has no shared ordering; different agents can perceive the same sequence of events differently, which is fine only if agents never need to reason about each other's relative ordering.

**E) Failure visibility.** If a point-to-point sender guesses the wrong (or no) recipient, the information is silently lost — a false negative nobody can detect, because nothing records that a message *should* have gone somewhere. If a log-reader simply fails to pick up a new entry, that's still a miss, but it's an inspectable one: the entry sits in the log and can be grepped retroactively by any agent, including one built after the fact. This asymmetry — silent loss vs. inspectable loss — favors the log whenever the cost of missed coordination is high and the set of interested parties is uncertain or still growing.

**Conclusion, reasoned independently:** for a system of intermittently-active, growing-in-number, semi-autonomous agents making consequential and auditable decisions, a shared append-only log dominates point-to-point messaging on coupling cost, temporal decoupling, auditability, and failure visibility. Point-to-point is preferable only for tight two-party, low-latency negotiation with a small fixed recipient set, or for high-volume transient data where durable storage would be wasteful. That implies a *hybrid* is optimal: direct messaging for narrow, synchronous back-and-forth between two known parties, and a shared log for durable, broadcast-worthy, auditable decisions.

## Corpus answer

Two established literatures converge on the same structure:

1. **Blackboard architecture** (AI systems, dating to Hearsay-II in the 1970s): multiple specialist agents read/write a shared data structure instead of messaging each other directly. Agents "do not need to know about each other — they only know about the blackboard," which "decouples agents from one another and makes it easy to add or remove specialists without changing the rest of the system." Point-to-point/peer negotiation is called out as better suited to linear pipelines or small, known participant sets, and blackboard as better when the problem-solving order isn't known in advance and dependencies are complex.
2. **Event sourcing / log-centric architecture** (distributed systems): "event streams retain all events... meaning consumers aren't required to be online at the exact moment an event is published" (temporal decoupling), and "in an event-sourced system you can replay the history... whereas in a CRUD system a corrupted database might mean irreversible loss of state" (auditability/recovery). Message queues, by contrast, are explicitly framed as one-producer/one-consumer and transient — "reading from a queue removes the data" — i.e., point-to-point and not durable by default.

## Delta: **rediscovered**, with one novel framing angle

The five arguments (decoupling/addressing cost, temporal decoupling, auditability, ordering/consistency, failure-visibility asymmetry) map cleanly onto established blackboard-architecture and event-sourcing literature — this was independently re-derived, not new. Categorize as **rediscovered**: it validates the reasoning chain rather than surfacing something the corpus doesn't already say.

One genuinely narrower framing the corpus search didn't hand back verbatim: the specific argument in (B) that for *intermittently-invoked, state-reset-between-runs LLM subagent sessions* (as opposed to always-on microservices, which is what most event-sourcing writing targets), a durable log isn't merely preferable to point-to-point messaging — it's closer to a *precondition* for asynchronous coordination working at all, since there's no live receiver to hand a message to synchronously. That's a small novel-ish inflection on well-trodden ground, not a corpus error.

Practically, this validates the Construct's existing design: `praxis-inbox.md` as the durable, auditable, broadcast log, with direct tools (`SendMessage`, `AskUserQuestion`) reserved for tight two-party exchanges — which is in fact the architecture already in place.
