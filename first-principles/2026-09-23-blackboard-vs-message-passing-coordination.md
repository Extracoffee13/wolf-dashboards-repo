# First-Principles Spike — 2026-09-23

## Question

In a multi-agent system where agents work asynchronously, on independent
schedules, without shared memory — should coordination default to a shared
append-only log ("blackboard" / inbox pattern, like this repo's
`praxis-inbox.md`) or to direct point-to-point messaging between agents?
Which should a system like The Construct default to, and why?

(Self-generated: no open item existed in `first-principles-backlog.md`, and
this question is directly load-bearing for Construct's own agent
architecture — it's the design decision behind the PRAXIS inbox pattern
this very task writes to.)

## First-Principles Answer (derived, no retrieval)

Start from the primitives. Coordination is the problem of getting the right
fact to the right agent at the right time so the group's actions stay
locally correct and don't collide or go stale. There are two limit cases:
direct messaging (A addresses and sends to B) and a shared log (every
writer appends, every reader filters independently).

**Coupling in space.** Direct messaging requires the sender to know the
receiver's identity. That's topology coupling: adding a new consumer means
rewiring every producer that should now also notify it. A shared log
removes this — producers write facts, consumers subscribe by content, not
by address. This is the single biggest asymmetry between the two models.

**Coupling in time.** Point-to-point messaging generally needs the
receiver's mailbox to exist and be live, or the message is lost or has to
be separately queued. A shared log is durable by construction — a reader
that starts three days late can replay from the beginning. This matters
enormously here specifically: Construct's agents fire on unrelated
schedules (cron triggers, event webhooks, human-gated approvals), so most
"receivers" are not running at write time.

**Consistency and single source of truth.** If N agents need to agree on
one fact (current AAIR score, open-todo count), a single ordered log gives
everyone the same read with a natural total order. N independent
point-to-point channels can silently diverge — two agents can each believe
a different "current state" because they received different message
subsequences. The log gets you an audit-grade single source of truth for
free; a mesh of direct channels has to build that as a separate concern.

**Fan-out cost.** If one fact matters to an unknown or growing number of
consumers, point-to-point messaging is O(N) sends and requires the
producer to maintain a consumer list (more coupling). A log write is O(1)
regardless of how many future readers exist. This dominates in a system
like Construct where new named agents get added over time (the inbox
example literally lists ~19 agents) — the producer of a fact should not
need to know who might care.

**Cost shifts to the reader.** The flip side: in a shared log, every
consumer must filter the whole stream for what's relevant to it, and that
filtering cost grows with the number of unrelated writers. Point-to-point
messaging keeps reader cost flat because the producer already filtered by
addressing. This is the log architecture's real scaling failure mode, and
the standard fix is to sub-partition the log into topics — which is really
reintroducing addressing inside the log.

**Failure semantics.** Unpersisted point-to-point messaging loses messages
if the receiver is down, forcing acks/retries/dead-letter handling. A log
solves loss for free but pushes the problem into deduplication ("have I
already processed this entry?") and into who tracks the read offset.

**Debuggability and provenance.** A durable, human-readable, append-only
log is an audit trail: who decided what, when, why. Ephemeral
point-to-point messages leave no trace unless someone deliberately logs
them. For a swarm run by one human operator who is *not* watching in real
time — which is exactly this session's situation, a scheduled task firing
with nobody reading along — that audit trail has value independent of the
coordination problem it solves: it's the mechanism by which the operator
can retroactively reconstruct what an asynchronous fleet did.

**Conclusion.** Pick the shared log when: the consumer set is unbounded,
unknown, or growing; consumers run on independent async schedules and need
to catch up on history; a durable audit trail has value beyond the
coordination itself; single-source-of-truth matters more than raw
throughput. Pick direct messaging when: it's a tight request/response
between two known parties (a subagent returning a result to its caller);
latency beats durability; payloads are large/high-frequency/ephemeral
(heartbeats, streamed tokens) where logging would be wasteful; the
relationship is fixed and won't grow into a fan-out problem. In practice
the right design layers both — a log for facts that matter to an unknown
future audience, direct channels for synchronous in-task work. That's
exactly what this repo already does: `praxis-inbox.md` is the log layer
for asynchronous, audit-worthy decisions; the `Agent`/`SendMessage` tool
calls underneath any single task are the point-to-point layer for
synchronous work within it. The split isn't arbitrary — it falls directly
out of the fan-out/audit/temporal-decoupling reasoning above.

## Corpus Answer (after search)

Search confirms the two-model framing is standard and the tradeoffs match
almost term for term:

- **Blackboard architecture** (shared knowledge space; agents monitor and
  write back when relevant) is directly contrasted in current literature
  with peer-to-peer message passing, including a 2026 piece explicitly
  titled "The Blackboard Is Back: What 1980s AI Knew About Multi-Agent
  Coordination" — arguing the pattern from 1980s AI (Hearsay-II) is being
  rediscovered for LLM multi-agent systems.
- **Coupling**: standard pub/sub literature states the same asymmetry —
  "the publisher doesn't know how many subscribers exist... you can add
  new subscribers without changing the publisher," versus point-to-point
  where "the publisher must know every consumer."
- **Fan-out**: "a single published event reaches an unbounded number of
  subscribers simultaneously" vs. one producer→one consumer for
  point-to-point — same claim as above, same reasoning.
- **Quantified coordination overhead I didn't derive**: message-passing
  topology cost is named explicitly as O(N²) — "ten agents create 45
  connections" — and empirical MAS research is cited showing a
  blackboard-based system beat master-worker architectures by 13-57% in
  end-to-end task success, with early message-passing systems suffering
  from agents "distracting each other with excessive updates."
- **Design coupling**: "blackboard architecture decouples phases —
  modifying one agent requires changing only that agent and configuration,
  leaving downstream agents untouched" — matches my coupling-in-space
  point almost verbatim.
- **Hybrid systems are standard practice**, not a compromise I invented: a
  common AWS pattern pairs SNS (fan-out) with SQS (durable, per-consumer
  queue) specifically to get fan-out and durability together, mirroring
  the "layer both" conclusion above.
- **When to prefer point-to-point**: corpus adds a framing I didn't
  derive — it favors direct messaging when agents work in genuinely
  different domains with specialized knowledge, or under network
  partitions requiring local decisions. My derivation reached point-to-point
  via latency/ephemerality/fixed-relationship reasoning instead; these are
  complementary, not contradictory.

## Delta Category: **rediscovered**

The core architecture — decoupling in space and time, fan-out cost,
single-source-of-truth, and the conclusion that production systems layer a
shared log with direct point-to-point channels rather than picking one —
was derived independently and matches the corpus closely, down to the
specific hybrid pattern (log/broadcast layer + durable per-consumer queue
layer) that Construct's own inbox + tool-call split already implements.

Two things the corpus supplied that pure reasoning didn't: the quantified
O(N²) topology cost and the empirical 13-57% success-rate delta from real
MAS research — numbers, not principles, and exactly the kind of thing
first-principles reasoning can't manufacture on its own.

One genuinely novel wrinkle, not emphasized in the retrieved sources: the
corpus discussion of blackboard-vs-messaging is framed around *task
coordination efficiency between agents*. The reasoning chain above
surfaced a second, independent justification specific to Construct's
actual deployment shape — a human operator who is *not watching live* and
depends on the log as the only mechanism for retroactive audit of an
asynchronous fleet. That's a supervision-oriented argument for blackboard
architectures, not a coordination-efficiency one, and it wasn't visible in
what the search turned up.

## Commentary

The practical takeaway for Construct: the PRAXIS inbox is not just
convention, it's the empirically-favored pattern (1980s blackboard
architecture, now validated again in 2026 multi-agent LLM research) for
exactly this shape of problem — many independently-scheduled agents,
unbounded/growing consumer set, and a human who checks in asynchronously.
Keep using it as the log layer, and keep direct Agent/SendMessage calls as
the synchronous layer underneath any single task. No architecture change
indicated; this spike is a validation, not a correction.
