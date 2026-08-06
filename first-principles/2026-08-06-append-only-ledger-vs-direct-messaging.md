# First-Principles Spike — 2026-08-06

## Question

Why should a multi-agent system use an append-only shared ledger (like `PRAXIS_INBOX` in this repo) for cross-agent coordination, instead of direct agent-to-agent messaging?

(Backlog was empty at spike time — question generated from current Construct work: the repo already runs ~19 named agents — AP, Vector, Forge, Signal, Cipher, Spectra, Oracle, Nexus, Ledger, Atlas, Sentinel, Venture, Equity, Alpha, WOLF, Keystone, Cornerstone, Charlie, Architect — coordinating through `praxis-inbox.md`.)

## First-Principles Answer (derived before any search)

Start from the actual constraints of this system, not from named patterns:

1. **No shared runtime.** Each agent is an independent process/session, often fired by its own cron schedule, with its own context window and no shared memory. The only substrate every agent can reach in every invocation is durable storage — the git repo. That alone rules out sockets, RPC, or any live call between agents: whatever coordination mechanism exists has to be store-and-forward, not synchronous.

2. **Unpredictable, possibly concurrent execution.** Agents run on independent schedules and can fire close together. Any coordination mechanism must survive two agents writing "at the same time" without silently destroying one write. Appending a new, self-contained block to a file is close to a commutative operation — two agents appending near-simultaneously in the worst case produce a git merge conflict, which is recoverable. Two agents *overwriting* the same mutable "status" record concurrently is not recoverable — last-write-wins silently drops information. So concurrency safety alone favors append over mutate.

3. **The audience for any given fact is unknown at write time.** When Ledger logs a margin decision, it doesn't know in advance whether Keystone, Scout, or nobody will care later. Point-to-point messaging requires the sender to pre-resolve the audience — but here the audience is "whoever reads the log later, for whatever reason." A shared broadcast log is strictly more general than addressed messaging whenever the sender can't enumerate the readers; it converts the coordination problem from "who do I tell" (up to N×(N-1) routes for N agents) to "everyone writes once, everyone reads the shared log once" (O(N)).

4. **A durable audit trail is a hard requirement**, not a nice-to-have — a human (Bobby) needs to review what agents decided and why, after the fact, not just current state. An append-only log gives you this for free: the log *is* the history. A system built on mutable state needs a second, separate history mechanism bolted on; the append-only ledger doesn't, because nothing is ever discarded.

5. **Failure must degrade gracefully.** Agents can crash mid-task or re-fire on a stale trigger. If "sending a message" means appending a self-contained entry, a duplicate re-fire produces at worst a duplicate entry — annoying, but harmless and easy to filter. If "sending a message" means updating shared mutable state, a duplicate or out-of-order re-fire can corrupt that state (e.g., overwrite a newer value with a stale one).

Conclusion: given no shared runtime, concurrent/unpredictable execution, an audience that can't be known in advance, a hard audit-trail requirement, and a need for safe idempotent failure — an append-only shared ledger dominates direct agent-to-agent messaging on every axis that matters here. Direct messaging would only win if audiences were narrow and known ahead of time and synchronous low-latency response were required — neither holds for cron-fired, best-effort agents like these.

**One gap my own reasoning surfaced but didn't fully resolve:** an append-only log solves the *write* side cleanly but doesn't by itself solve the *read* side — something has to track what's already been consumed, or readers reprocess the same entries forever. That requires a second artifact (a cursor / processed-marker), which is itself a place things can drift out of sync. This repo already has empirical evidence of exactly that: `praxis-inbox-processed.md` exists alongside `praxis-inbox.md`, and an earlier bootstrap entry in the inbox records that both files were initially missing and "capture velocity is zero" until seeded manually.

## Corpus Answer (found after search)

This is a known, named pattern in distributed systems and event-driven multi-agent architecture:

- **Event sourcing**: state changes are recorded as an immutable, append-only sequence of events that serves as the single source of truth; state can be reconstructed by replaying events, which also gives failure recovery for free.
- **Blackboard architecture**: independent agents coordinate indirectly through a shared, persistent workspace (the "blackboard") rather than direct communication, incrementally accumulating hypotheses/results that any agent can read.
- **Event bus / pub-sub**: a lighter-weight, more ephemeral variant of the same idea — decouples producers from consumers, supports multiple consumers per event, without the blackboard's persistent queryable memory.

The literature explicitly cites the same benefits derived above: decoupling producers from consumers when the consumer set isn't known in advance, resilience via replayable/immutable logs, and a single durable source of truth for coordination and audit. The blackboard pattern additionally supports richer relational/global-state reasoning than a plain event bus, which the append-only-log framing above doesn't fully capture — that's a genuine axis the corpus adds.

Sources:
- [Blackboard/Event Bus Architectures](https://www.emergentmind.com/topics/blackboard-event-bus)
- [A distributed state of mind: Event-driven multi-agent systems | InfoWorld](https://www.infoworld.com/article/3808083/a-distributed-state-of-mind-event-driven-multi-agent-systems.html)
- [Four Design Patterns for Event-Driven, Multi-Agent Systems](https://www.confluent.io/blog/event-driven-multi-agent-systems/)
- [Event Sourcing: Architecture Pattern for Auditability and State Management | Zylos Research](https://zylos.ai/research/2026-02-17-event-sourcing-architecture-pattern/)
- [Event-based blackboard architecture for multi-agent systems | IEEE Xplore](https://ieeexplore.ieee.org/document/1425173/)

## Delta Category: **rediscovered**

The first-principles chain independently arrived at the core mechanism the corpus names as event sourcing / blackboard architecture: append-only over mutable state for concurrency safety, decoupled producer/consumer because the audience is unknown at write time, and the log doubling as the audit trail. This validates the reasoning path rather than adding new information.

## Commentary

The one place the corpus outran the derivation: the blackboard pattern is explicitly framed as *richer* than a plain append-only event log because it supports structured, queryable, relational state, not just a flat sequence of facts — a distinction the first-principles pass didn't need to invent but which matters if `praxis-inbox.md` ever needs to support queries like "show me every decision that touched pricing" rather than linear reading. Conversely, the first-principles pass surfaced something the search summary didn't foreground: the consumer-side cursor/offset problem (the `praxis-inbox-processed.md` gap already visible in this repo) is a necessary second invariant that an append-only log does not solve by itself — it's implicit in "replayable" but easy to under-design in practice, which is exactly what happened here.
