# First-Principles Spike — 2026-07-31

## Question

Why should a multi-agent system route coordination through a shared
append-only inbox (like `praxis-inbox.md` in this repo) rather than
direct agent-to-agent messages?

(Self-generated — the backlog file was empty/missing, so this spike seeded
it. Chosen because it's directly relevant to this repo's own agent
architecture: `praxis-inbox.md`, `praxis-daily-review/`, and the ~19 named
agents referenced there.)

## First-Principles Answer (derived before any search)

Strip the question down to primitives: an agent observes state, produces an
output, and that output eventually needs to influence other agents' future
observations. Coordination is just the mechanism for (3). Treat this as a
plain distributed-systems problem — N independent, asynchronously-run
processes that need to share information over time, where N grows and
processes are added/removed independently.

**1. Topology cost.** If every agent can directly message every other agent,
the number of possible channels is O(N^2); adding the Nth agent means
deciding, for each of the N-1 existing agents, whether a channel is needed.
A shared store makes the cost of adding a new participant O(1): the new
agent just starts reading (and writing) the same stream everyone else does.

**2. Temporal decoupling.** Direct messaging requires the sender to know,
*at send time*, who the relevant receivers are. But agents get added over
time — a sender today can't know which agent built six months from now will
need to react to its decision. A shared log breaks this bind: the writer
doesn't address anyone, it just records what happened. Any current or
future reader can subscribe without the writer's cooperation. This is the
generic shift from push-to-known-destination to publish-and-let-consumers-
decide-relevance — coupling deferred from write-time to read-time.

**3. Durability solved once.** If A messages B directly and B isn't running
at that instant, either the message is lost or A must own retry/queueing
logic for every possible recipient. A durable shared store solves this
problem centrally, once, instead of N times (once per sender).

**4. For stateless agents specifically, the log IS the memory.** An
LLM-based agent invoked fresh has no persistent process memory between
invocations — its only way to "know" what happened before is to read
something durable. So durable storage is required regardless of the
messaging topology; once you have it, routing *all* coordination through it
(rather than maintaining it as a side-channel next to direct messages)
eliminates dual-bookkeeping ("did I tell everyone, or just whoever I
remembered to message directly?").

**5. Append-only sidesteps conflict resolution.** Two agents writing "at the
same time" each just append their own record — no locking or merge logic,
unlike a single mutable shared object multiple agents PATCH.

**Cost paid:** every consumer must filter a shared, growing stream for
relevance instead of receiving only what's addressed to it, and there's no
strong ordering/causality guarantee the way a direct synchronous call would
give.

## Corpus Answer (found after searching)

This is the **Blackboard architecture pattern** (Hayes-Roth/Hearsay-II
lineage, AI systems literature, 1970s-80s), now widely re-applied to
LLM-based multi-agent systems: a shared, globally-readable/writable
workspace ("the blackboard") that agents post to and monitor, instead of
messaging each other directly. Named benefits cited across current
sources: agents don't need to know about each other (decoupling), it
supports asynchronous/opportunistic contribution as agents become able to
act on newly-posted information, and it composes with modern event-driven /
pub-sub designs (Confluent's write-up frames the same pattern as an event
log). Named cost, matching what I derived: it's less immediately responsive
than direct messaging, and the shared store can grow large enough that each
agent has to filter through a lot of irrelevant material — "less efficient
than targeted messages" for high-volume cases.

Sources:
- [Patterns for Democratic Multi-Agent AI: Blackboard Architecture — Part 1 (Medium)](https://medium.com/@edoardo.schepis/patterns-for-democratic-multi-agent-ai-blackboard-architecture-part-1-69fed2b958b4)
- [Four Design Patterns for Event-Driven, Multi-Agent Systems (Confluent)](https://www.confluent.io/blog/event-driven-multi-agent-systems/)
- [Blackboard Architecture in Agentic AI (DataFlair)](https://data-flair.training/blogs/blackboard-architecture-in-agentic-ai/)
- [The Blackboard Architecture: Solving the Agent "Phone Game" (rajatpandit.com)](https://rajatpandit.com/agentic-ai/the-blackboard-architecture/)

## Delta

**Category: rediscovered**

The derivation landed on the core structural claim of blackboard
architecture independently: indirect communication via a shared store,
avoiding O(N^2) pairwise wiring, agents not needing to know each other, and
the same named tradeoff (slower/less targeted than direct messaging as the
store grows). No terminology from the field was recalled or assumed going
in — the reasoning was built purely from "N processes, asynchronous,
growing set of participants."

One angle in the derivation isn't emphasized in the corpus write-ups
surveyed: point 4, that for agents with *no persistent process memory*
(true of LLM-based agents invoked fresh each time, unlike the original
Hearsay-II knowledge-source processes, which were long-running), the shared
log isn't just a coordination bus — it's the *only* memory substrate the
system has. The blackboard-pattern literature treats durability as an
implementation detail of "the workspace"; here it's closer to load-bearing:
without the log, this class of agent has no continuity at all. That's a
minor sharpening, not a full novel framing, so it doesn't change the
category — but it's worth carrying into how `praxis-inbox.md` itself gets
used going forward (see lesson below).

## Commentary

Confidence this was reasoned cleanly rather than pattern-matched from
training data: moderate-high. The prompt explicitly avoided naming
"blackboard," "pub/sub," or any pattern going in, and the derivation chain
(topology cost → temporal decoupling → durability → statelessness →
conflict-freedom) reads as genuine construction from primitives, not
recall. The main value of the exercise wasn't discovering something new —
it's that the reasoning cross-checks clean against 50 years of prior art,
which is itself useful evidence that the design of this repo's own
`praxis-inbox.md` pattern rests on sound footing rather than convention for
convention's sake.
