# First-Principles Spike — 2026-07-06

## Question

The backlog file (`first-principles-backlog.md`) was missing/empty, so this
question was generated from current Construct work — specifically this
repo's own coordination mechanism:

> Why should a set of autonomous agents (the AP/Vector/Forge/Signal/... roster
> already named in `praxis-inbox.md`) coordinate through a shared,
> append-only log file rather than through direct agent-to-agent messaging?

## First-principles answer (derived before any search)

**Primitives:** N independent agents, each invoked on its own schedule
(cron/event-trigger), never guaranteed to be running at the same instant.
They need to transfer decisions and lessons forward so future runs (of
themselves or others) don't repeat mistakes.

**Chain of reasoning:**

1. Direct messaging (A calls B) requires B to be addressable *and live* at
   send-time. Given independent schedules, the odds any specific recipient
   is executing when a sender wants to communicate are low — and for
   one-to-many lessons there often isn't a single natural recipient anyway.
   Synchronous point-to-point messaging is the wrong shape for this
   population; the problem isn't reliability, it's that "who do I call" has
   no stable answer.

2. If delivery can't be synchronous, it must be mediated by something
   durable that outlives any single agent's execution window: a store any
   agent can write to and any agent can read from, with no handshake
   required.

3. Given a shared store, choose mutable-state-per-topic vs. append-only.
   Mutable state fails under concurrent writers — two near-simultaneous
   writes produce a lost update unless you add locking/versioning, which is
   exactly the complexity append-only avoids for free (appends don't
   collide; each is a self-delimited record).

4. What's being transferred is naturally *events* (a decision, an outcome, a
   lesson) — facts-in-time, not values-to-be-overwritten. An append-only log
   preserves history automatically; a mutable snapshot destroys it by
   construction. Audit ("why did the system behave this way") falls out for
   free.

5. Downstream aggregation (a "daily review" computing packet counts,
   trending lessons, low-confidence flags) needs a well-defined view to
   replay against. That's only cheap over an immutable ordered sequence —
   replaying mutations to shared state isn't deterministic unless every
   historical version was kept anyway, which is just a log in disguise.

6. Consumption must be decoupled from production the same way production is
   decoupled from addressing: the reader won't be online when the writer
   writes. So the reader needs a checkpoint — "consumed up to here" — without
   deleting or locking the source. The cheap solution: a second file
   (`praxis-inbox-processed.md`) as the checkpoint, functionally a
   hand-rolled consumer offset.

7. Why not a real broker instead of a flat file? A broker reintroduces the
   exact dependency step 1 eliminated: a live, addressable, operated
   service. For a small, low-frequency agent population that's
   disproportionate. A version-controlled file gets persistence,
   replication, and even conflict resolution for free by riding on
   infrastructure (git) that already exists for an unrelated reason. The
   file *is* the broker; git *is* the replication/merge layer.

**Conclusion:** prefer transferring immutable facts through a durable,
appendable medium over transferring mutable state through direct or
brokered messaging whenever producers and consumers can't be guaranteed to
coexist in time. Trade a little storage growth and eventual consistency for
eliminating liveness coupling, lock contention, and lost history.

## Corpus answer

Two established patterns match this derivation almost exactly:

- **Blackboard architecture** (Hearsay-II speech recognition system, 1970s):
  specialist agents ("knowledge sources") don't message each other directly;
  they read from and write to a shared data structure (the blackboard), with
  a control shell deciding who acts next based on blackboard content. This
  decouples agents from one another and lets specialists be added/removed
  without touching the rest of the system. ([CallSphere](https://callsphere.ai/blog/blackboard-architecture-multi-agent-systems-shared-knowledge-spaces), [Muthu's engineering notes](https://notes.muthu.co/2025/10/collaborative-problem-solving-in-multi-agent-systems-with-the-blackboard-architecture/), [Springer — Reflective Blackboard Pattern](https://link.springer.com/chapter/10.1007/3-540-35828-5_5))

- **Event sourcing / log-based architecture**: system state is represented
  by a durable, append-only log of immutable events rather than mutable
  snapshots; the event store supports only INSERT and SELECT, never
  UPDATE/DELETE; current state is a projection replayed from the log. This
  sidesteps the classic distributed-systems race/lock problems that arise
  when multiple writers share one mutable record, and gives auditability and
  temporal replay for free. ([EmergentMind](https://www.emergentmind.com/topics/event-sourced-state-management), [TianPan.co — agent state as event stream](https://tianpan.co/blog/2026-04-10-agent-state-event-stream-immutable-event-sourcing))

Kafka-style consumer offsets are the industry-standard version of the
"processed" checkpoint file reasoned about in step 6.

## Delta category: **rediscovered**

The derivation independently reconstructed both the blackboard-architecture
rationale (indirect coordination through shared state beats direct
messaging when participants aren't co-live) and the event-sourcing
rationale (append-only beats mutable-shared-state under concurrent writers,
and gives audit/replay for free), without having looked either up first.
The reasoning chain and the corpus converge on the same structure almost
term-for-term (checkpoint/offset, control shell vs. daily-review, knowledge
source vs. agent).

## Commentary

One thing the corpus search didn't surface: neither the blackboard nor the
event-sourcing literature discusses using a plain git-tracked file as the
blackboard/event-store itself. Both assume dedicated infrastructure (a
blackboard data structure in-process, or a real event store/broker like
Kafka). This repo's actual implementation — `praxis-inbox.md` /
`praxis-inbox-processed.md` as plaintext files in a git repo — gets
persistence, replication, and conflict resolution "for free" by riding on
git rather than standing up a database or broker. That specific packaging
(git-as-broker for a small, low-frequency agent population) is a
reasonable specialization of the general pattern rather than something the
corpus names outright — worth keeping in mind as this repo's agent count or
message volume grows and the git-file approach starts to strain (e.g. merge
conflicts on concurrent appends, no query capability beyond grep).
