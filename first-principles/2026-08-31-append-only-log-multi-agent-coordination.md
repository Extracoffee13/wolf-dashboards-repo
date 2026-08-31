# First-Principles Spike — 2026-08-31

## Question

Is a shared append-only log (e.g. this repo's `praxis-inbox.md`) fundamentally
the right coordination primitive for a multi-agent system like The Construct,
or is it just a workaround for missing infrastructure (message queues, an
actor runtime, a real event bus)?

## First-Principles Answer (derived cold, no retrieval)

Start from what coordination is actually for: multiple independent actors need
to (a) know what has happened, (b) avoid duplicating or clobbering each
other's work, (c) build on each other's outputs, and (d) let a human or
supervisor audit and intervene.

There are two fundamental topologies for this. **Point-to-point message
passing**: each agent addresses specific peers directly (RPC, a queue, an
actor mailbox). **Shared observable state**: agents read and write a common
surface that nobody addresses directly — a blackboard. Point-to-point
requires solving discovery/routing, and worst-case channel count grows with
the square of agent count unless you add a broker. A shared log sidesteps
addressing entirely — write once, anyone interested reads later — at the cost
of pushing filtering work onto every reader instead of onto the writer.

Ordering and causality differ too. Point-to-point coordination gets causal
order for free from the call graph. A shared log needs an explicit ordering
mechanism. In this repo's case, that mechanism is free: git commits on a
branch are strictly sequential, so "append order in the file" already gives a
total order without inventing logical clocks.

Concurrency is where the *format* matters, not just the pattern. Append-only
means no in-place mutation, so the classic lost-update conflict class
(two writers stomping the same field) can't happen *semantically* — but it
can still happen *mechanically* as a git merge conflict if two agents append
near the same lines at once. The fenced-block format (`~~~ ... ~~~`, one
self-contained record per agent action) is doing real work here: because no
two legitimate writes ever need to touch the same line, git's line-based
merge almost never actually conflicts, even though nothing in the "log"
abstraction itself guarantees that — it's an artifact of *how* the format was
chosen, not of logs in general.

Durability and auditability come nearly free from choosing "a file in a git
repo" as the log's substrate: every append is versioned, diffable, blameable,
revertible. For a system whose explicit purpose is producing durable,
reviewable lessons for semi-autonomous agents, that's a strong fit — you get
a supervision surface without building one.

Latency is the real constraint that decides right-vs-wrong here. A log read
by periodic review (a daily/triggered reviewer agent) has a latency floor
equal to the poll interval; nobody learns of a new entry the instant it's
written. Push messaging has near-zero latency by comparison. So: wrong
primitive for reflexive, time-critical coordination (two agents racing to
claim the same task in real time); right primitive when the actual
consumption pattern is asynchronous and batch, which is what a "daily
review" cadence already implies — the system was never trying to be
low-latency, so the log's weakness is inert here.

Failure modes specific to the log approach, reasoned out: (1) unbounded
growth — nothing compacts old entries into a distilled knowledge base, so
"read the whole log for context" gets linearly more expensive forever; the
fix, by analogy to how any log-structured system matures, is a periodic
snapshot/compaction pass, not abandoning the log. (2) no delivery
acknowledgment — a write is *visible*, not *received*; if a task must
provably get picked up, a log alone can't promise that, only a request/ack
channel can. (3) schema drift — free-text fields will drift in quality across
writers without validation, unlike a typed message contract.

**Verdict from primitives alone:** the log is the right primitive exactly
when (i) write frequency relative to agent count is low enough that
line-level merge conflicts stay rare, (ii) human-in-the-loop auditability is
a first-class requirement rather than an afterthought, and (iii) the
consumption pattern is asynchronous/batch rather than reflexive. All three
hold for this system today. It becomes wrong at the boundary — high write
contention, any need for sub-second cross-agent reaction, or a log nobody
ever compacts — and the fix at that boundary is never "replace the log," it's
"add a derived/compacted view or a low-latency side channel on top of the
same durable ledger."

## Corpus Answer

This maps almost exactly onto a named, well-established pattern: the
**blackboard architecture** (classical AI, e.g. Hearsay-II) — a shared state
object that independent specialist agents read and opportunistically write
to without direct peer-to-peer addressing. The modern software-engineering
descendant is **event sourcing**: state changes recorded as an immutable,
appended event log that serves as the single source of truth, replayable for
recovery, with multiple independent consumers subscribing to the same
stream. Current multi-agent-LLM literature and practitioner writeups
(Confluent's "event-driven multi-agent systems," "the log is the agent"
framing from event-sourced AI-memory writeups, and comparison guides on
multi-agent architecture) converge on the same tradeoff table I derived:
blackboard/log patterns win on decoupling, auditability, and replay, and lose
on tight coupling, real-time ordering guarantees, and (for LLM-specific
event-sourced memory) the cost of replaying token-expensive history rather
than cheap state mutations.

## Delta Category: **rediscovered**

The core tradeoff structure (shared-state/blackboard vs. point-to-point
message passing; append-only log as low-coupling, high-auditability,
latency-tolerant coordination; compaction as the scaling fix) is the standard
answer, arrived at independently without naming it. One piece goes further
than the generic corpus discussion: the specific claim that git's line-based
merge algorithm plus a *self-contained fenced-block* record format is what
actually prevents write conflicts in this system — the corpus material talks
about "conflict resolution when multiple agents write to shared state" as a
cost to manage, not as something a chosen record shape can engineer away
almost entirely. That's a small novel wrinkle on top of an otherwise
rediscovered answer, not a distinct category on its own.

## Commentary

The exercise validates the reasoning process more than it produces new
knowledge: cold-deriving "blackboard vs. message-passing, log wins on
auditability, loses on latency, compaction is the long-run fix" and then
finding that's exactly the received architecture pattern is a good sign the
first-principles chain is sound, not a lucky guess. The one genuinely useful
takeaway for this repo specifically: the reason `praxis-inbox.md` hasn't hit
merge-conflict pain yet isn't luck, it's the fenced-block-per-entry format —
and that's worth protecting deliberately (never restructure it into something
where two agents' writes could land on the same line) rather than assuming
"it's a log, logs don't conflict."

Sources:
- [Four Design Patterns for Event-Driven, Multi-Agent Systems (Confluent)](https://www.confluent.io/blog/event-driven-multi-agent-systems/)
- [The Log Is the Agent: Event Sourcing Comes to AI Systems](https://www.developersdigest.tech/blog/log-is-the-agent-event-sourced-ai)
- [Patterns for Democratic Multi-Agent AI: Blackboard Architecture — Part 1](https://medium.com/@edoardo.schepis/patterns-for-democratic-multi-agent-ai-blackboard-architecture-part-1-69fed2b958b4)
- [Multi-agent system architecture: a comparison guide + best practices — Openlayer](https://www.openlayer.com/blog/multi-agent-system-architecture-guide)
- [A distributed state of mind: Event-driven multi-agent systems — InfoWorld](https://www.infoworld.com/article/3808083/a-distributed-state-of-mind-event-driven-multi-agent-systems.html)
