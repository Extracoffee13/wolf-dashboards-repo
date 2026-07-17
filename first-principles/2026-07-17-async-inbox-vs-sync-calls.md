# First-Principles Spike — 2026-07-17

## Question

Should independent agents in a multi-agent system (like this one — AP,
Vector, Forge, Signal, Cipher, Keystone, WOLF, etc.) coordinate through an
asynchronous shared inbox (write-and-forget, e.g. `PRAXIS_INBOX`), or
through direct synchronous request/response calls between agents? What's
the underlying rule for choosing one over the other?

*Source: no open item in `first-principles-backlog.md` (file was missing —
created as an empty placeholder), so this question was generated from
current Construct work: the very PRAXIS_INBOX mechanism this spike ends
by writing to.*

## First-Principles Answer (derived before any search)

Define an agent as a unit of computation with private state and behavior
that sends and receives messages. Define a coordination mechanism as
whatever lets one agent's output influence another agent's behavior.
There are two archetypes on the table: (A) a synchronous direct call,
where agent A invokes agent B, blocks, and uses the return value
immediately; and (B) an asynchronous shared inbox, where A writes a
message to a durable, shared, append-only location, and some unknown set
of agents read it at some unknown future time.

Reason through six axes:

**1. Coupling.** A synchronous call requires A to know B's identity,
interface, and availability *at call time*. That's a real-time directed
dependency: if B is slow, down, or overloaded, A blocks or fails with it.
With N agents calling each other directly, the dependency graph can grow
toward O(N²) live edges. A shared inbox decouples producer from consumer
along three dimensions at once — identity (A doesn't need to know who, if
anyone, reads it), time (the reader doesn't need to be present when the
writer writes), and failure domain (a crash on either side doesn't unwind
the other's call stack).

**2. Failure isolation.** If each agent fails independently with
probability p, a synchronous call chain of depth k has failure
probability roughly 1-(1-p)^k — failures compound multiplicatively along
the chain. This matters more than usual here because the agents are LLM
agents, which have a non-trivial baseline error/hallucination rate. An
inbox breaks the chain: a bad write just sits as a bad message to be
ignored or corrected later, it doesn't propagate a crash up a call stack.

**3. Consistency requirements.** If B genuinely needs A's freshest state
before acting, only a synchronous call (or an explicit request/response
protocol) gives a fresh read. If B can tolerate acting on a stale or
delayed view — which is true of most "lessons learned" or "decision log"
traffic — paying for synchronization buys a guarantee nobody needed. Rule:
match the mechanism's consistency guarantee to the task's actual
consistency requirement; anything stronger is wasted coupling.

**4. Reader cardinality.** A synchronous call is inherently 1:1 (fan-out
is just N live edges). An inbox is naturally 1:N or N:N: one writer,
arbitrary current and *future* readers, without the writer enumerating
them. If a message's value is "whichever agent cares can pick this up"
(a lesson that Vector, Forge, and Signal might all want), a durable log
is structurally cheaper than N synchronous calls, and it works for
readers/agents that don't exist yet.

**5. Backpressure / rate mismatch.** Agents run on different cadences —
some hourly, some daily, some on demand. A synchronous call forces the
caller to match the callee's readiness. An inbox absorbs the mismatch:
writers write at their pace, readers drain at theirs. This is the actual
reason message queues exist in distributed systems generally — they
convert a synchronization problem into a storage problem, and durable
storage is cheap and well understood in a way that synchronized
rendezvous under partial failure is not.

**6. When synchronous is actually correct.** If A cannot proceed with its
own next step without B's answer *right now*, that's a genuine data
dependency. No amount of decoupling removes the need for the value —
forcing it through an async inbox just adds a polling loop and latency
without removing the coupling.

**Derived rule:** use a synchronous direct call when there's a real,
immediate, single-consumer data dependency the caller cannot proceed
without. Use an asynchronous shared inbox when the interaction is a
broadcast, a notification, a durable record for unknown future consumers,
or when producer and consumer run on independent cadences. The deeper
principle: pick the coupling mechanism that matches the true dependency
structure of the work, no more — every unit of excess coupling multiplies
failure exposure across the whole agent graph.

## Corpus Answer (found after searching)

The literature converges on almost exactly this line, across two
independent traditions:

- **Blackboard architecture** (Hearsay-II lineage, and its modern
  multi-agent-LLM revival) is precisely the shared-inbox pattern:
  "asynchronous communication via a shared memory or data store... rather
  than sending direct messages between agents... a communal workspace
  where agents post their findings and read what others have posted."
  Guidance: choose blackboard "when you have many specialists with
  complex dependencies... and when the problem-solving order is not known
  in advance"; use direct messaging for linear pipelines.
- **Actor model** (Hewitt): agents communicate by asynchronous message
  passing to mailboxes — async by default, but still *addressed*
  point-to-point, unlike blackboard's indirect broadcast.
- **Enterprise Integration Patterns** (Hohpe & Woolf) names the exact
  failure-propagation mechanism I derived, almost verbatim: "components
  that communicate... synchronously are temporally coupled: if a provider
  is slow or only intermittently available, the requestor also becomes
  slow or only intermittently available... message queues provide
  temporal decoupling while increasing robustness."
- The practical rule of thumb the corpus gives for the sync/async split
  matches axis 6 directly: "use synchronous APIs when the caller needs a
  response immediately... use asynchronous APIs when the operation takes
  time or the client doesn't need an immediate response."

## Delta Category: **rediscovered**

## Commentary

The failure-isolation argument, the temporal-decoupling framing, and the
"does the caller need the value right now" litmus test all match
published sources closely enough that this reads as independent arrival
at a known answer, not coincidence dressed up after the fact — the
reasoning chain (coupling → failure compounding → consistency → reader
cardinality → backpressure → the one case for sync) is the same chain
Hohpe/Woolf and the blackboard-architecture literature use, derived here
without having read them first.

One gap: I treated "async shared inbox" as a single archetype. The corpus
draws a real distinction I didn't — actor-model mailboxes are async but
*addressed* (point-to-point), while blackboard is async and *indirect*
(broadcast, shared workspace, no addressing). `PRAXIS_INBOX` is
specifically the blackboard variant, not a generic actor mailbox, and the
corpus is explicit that blackboard is the right choice specifically when
"the problem-solving order is not known in advance" — which is exactly
this agent ecosystem's situation (no fixed pipeline, unknown future
readers, unknown future agents). Worth folding "addressed vs. indirect"
into the framework as a seventh axis next time this question comes up.
