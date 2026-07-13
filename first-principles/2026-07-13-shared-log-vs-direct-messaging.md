# First-Principles Spike — 2026-07-13

## Question

Why should autonomous agents in a multi-agent system (e.g. the Construct's own
`praxis-inbox.md` / `praxis-inbox-processed.md` mechanism) coordinate via an
append-only shared log rather than direct agent-to-agent messaging?

Picked from live repo context: this repo already implements the pattern under
scrutiny (`praxis-inbox.md`, `praxis-inbox-processed.md`, `praxis-daily-review/`),
so the question asks *why the system I'm running inside is built the way it is*.

## First-principles answer (derived, no retrieval)

Primitives of the situation, observed directly in this repo: multiple named
agents (AP, Vector, Forge, Signal, Cipher, Spectra, Oracle, Nexus, Ledger, Atlas,
Sentinel, Venture, Equity, Alpha, WOLF, Keystone, Cornerstone, Charlie, Architect)
each run as independent, isolated sessions with no persistent shared runtime.
They start fresh, do work, and stop. The only thing that reliably survives
between their sessions is whatever got committed to the git repo. Coordination
has to be built on top of that constraint, not around it.

Start from what "coordination" actually needs to accomplish: agent A learns
something during its run (e.g. "the inbox files must exist before capture can
happen") that should change some future agent B's behavior. The question is what
mechanism gets that fact from A's head into B's head, given the constraints above.

**Primitive 1 — time-decoupling.** A and B are not running at the same time. A
finishes and exits before B is ever invoked, possibly hours or days later. Any
coordination mechanism that assumes a live recipient (an RPC call, a socket, an
in-memory queue, a direct "ping agent B") is structurally incompatible with
this — there is no B to call. The only mechanisms that work under strict
time-decoupling are ones where the sender writes to something durable and the
receiver reads it later, on its own schedule. That already rules out
point-to-point messaging as the primary mechanism and forces something
store-and-forward.

**Primitive 2 — unknown audience at write time.** When A writes a lesson, A
does not know which future agent (or how many) will need it. It might be
relevant to Vector next week, or to a new agent, "Architect," that doesn't
exist yet. Direct messaging requires the sender to name a recipient — but the
recipient set for a "lesson" is genuinely unbounded and unknown in advance. The
only way to serve an unknown future audience is to publish somewhere all
potential readers can look, rather than address a specific one. This is the
same reason a company puts a policy in a handbook instead of emailing it
individually to everyone who might ever need it — broadcast-to-a-place beats
point-to-point when the reader set is open-ended.

**Primitive 3 — no shared mutable runtime, but a shared durable substrate
exists.** These agents don't share RAM, a database, or a long-lived process.
What they do share is a git repository. Git already gives you: durability
(survives any single agent's session ending), a total order of writes
(commits), a free audit trail (who wrote what, when), and conflict detection
(merge conflicts surface concurrent writes instead of silently losing one).
Building a custom message bus would mean re-implementing all of that from
scratch on infrastructure that doesn't natively support it (no long-lived
broker process). Reusing the git log as the coordination log is close to free
by comparison — persistence, ordering, and audit come as side effects of a
mechanism that already has to exist for an entirely different reason
(versioning the code/content).

**Primitive 4 — write cost should be O(1) per agent, not O(N).** If N agents
coordinate by direct messaging and each new lesson is potentially relevant to
several others, the sender either guesses and addresses a subset (lossy — some
readers never see it) or addresses all N-1 others (fan-out that grows O(N) per
message, O(N²) system-wide as agent count grows). Every agent added to the
Construct makes every future message more expensive under direct addressing.
An append-only shared log inverts this: write cost is O(1) regardless of how
many agents exist or will exist later; distribution cost is paid by readers
pulling from a common place, not by writers pushing to N destinations. This
gets *more* attractive, not less, as the Construct adds agents.

**Primitive 5 — separating "new" from "processed" gives you a queue with a
checkpoint, without a broker.** The repo already shows this: `praxis-inbox.md`
holds unprocessed entries, `praxis-inbox-processed.md` holds what's been
folded into review. This is the append-only-log equivalent of a consumer
offset in a message queue — a periodic reader (the daily review) reads
everything since the last checkpoint, acts on it, and advances the checkpoint
by moving entries across files. You get at-least-once delivery semantics
without needing a broker to track per-consumer offsets, because there's
effectively one consumer and the checkpoint is just "which file it's in."

**Primitive 6 — convergence, not synchronization.** Because every agent reads
the same log rather than negotiating pairwise state with every other agent,
all readers converge on the same view of "what has been learned so far"
without needing to synchronize directly with each other. This is weaker than
strict consistency (an agent that hasn't read recently is behind) but is
exactly the right tradeoff for intermittently-online agents: it never blocks a
writer on a reader's availability, and never requires a reader to contact
multiple writers to reconstruct the full picture.

**Conclusion, derived:** given (a) agents that don't run concurrently, (b) an
unknown and growing set of future readers per message, (c) a git repo as the
only durable shared substrate, and (d) a desire to keep per-write coordination
cost constant as agent count grows — an append-only shared log dominates
direct point-to-point messaging on every axis that matters here. Point-to-point
messaging would only win if agents needed private, addressee-specific
communication (not the case for "lessons," which are explicitly meant to be
shared) or low-latency synchronous coordination (not the case for agents that
run once and exit).

## Corpus answer (after search)

Two established patterns converge on the same shape:

- **Blackboard architecture** (Hearsay-II, 1970s AI, still used in modern
  multi-agent LLM systems): specialist agents ("knowledge sources") don't
  message each other directly — they read and write a shared blackboard.
  A control shell decides which agent acts next based on blackboard state.
  This decouples agents from each other and lets specialists be added or
  removed without touching the rest of the system. Modern write-ups add a
  detail I didn't derive: an explicit *control shell* doing opportunistic
  scheduling over blackboard state, and per-key locking/optimistic concurrency
  for parallel writers.
- **Event sourcing**: state changes are stored as an immutable, ordered,
  append-only sequence of events, which becomes the system of record; current
  state is derived by replay. Corpus explicitly contrasts this with
  point-to-point queues, where a consumed message is typically deleted and
  lost for future reference — the same "no replay, no unknown-future-reader"
  limitation I derived under Primitive 2. Corpus's stated advantages —
  auditability, traceability, resilience, replayability — line up with my
  Primitive 3 almost exactly.

## Delta: rediscovered

My reasoning independently arrived at the blackboard-architecture /
event-sourcing shape — shared append-only store, decoupled writers and
readers, audit-by-construction, replay over re-delivery — without having the
names for either pattern going in. The mechanics (Primitives 1, 2, 3, 6) match
the corpus closely enough that this counts as validation of the reasoning
chain, not just a coincidence of vocabulary.

One wrinkle that leans slightly toward **novel**: the corpus discusses both
patterns as *purpose-built* infrastructure (a blackboard data structure, an
event store/broker). My reasoning went a step further and argued specifically
for *repurposing version control* — git, chosen not because it's an idiomatic
event store but because it's the one thing that happens to already be durable
and shared across ephemeral, isolated agent sessions with no long-lived
process. That "use whatever the deployment topology already makes durable and
shared, even if it wasn't designed as a coordination log" framing isn't
something either search hit articulated — the corpus assumes you're allowed to
provision a broker or an event store; this repo can't, so git is doing double
duty. Net category: **rediscovered**, with a minor novel corollary about
infra-repurposing under ephemeral-runtime constraints.

## Commentary

The strongest primitive was time-decoupling (Primitive 1) — it alone rules out
most alternatives before audience-size or write-cost considerations even come
into play, which matches how the corpus frames blackboard/event-sourcing as
solutions to *asynchronous* multi-party coordination first and foremost.
The one thing pure reasoning under-weighted going in: the corpus's control
shell / scheduling concept. My derivation explains why a shared log beats
messaging for *distribution*, but doesn't independently produce the idea that
you also need something deciding *who reads/acts next* — in this repo that
role is played by the periodic `praxis-daily-review` process, which I noted
exists but didn't connect to the "control shell" abstraction until the corpus
named it.
