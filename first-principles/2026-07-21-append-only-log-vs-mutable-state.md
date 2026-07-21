# First-Principles Spike — 2026-07-21

## Question

Why is an append-only log (like this repo's `praxis-inbox.md`) the right
coordination primitive for a multi-agent system, rather than a shared
mutable state file (e.g. a single `agent_status.json` each agent
overwrites)?

The backlog was empty, so this question was self-generated as directly
relevant to current Construct work: it's the actual mechanism this repo
uses for cross-agent coordination (`praxis-inbox.md`, `wolf_live_data.json`,
`scout_state.json`), and getting it wrong has already shown up once in this
repo's own history (an earlier PRAXIS entry noted the inbox files didn't
exist yet and had to be bootstrapped).

## First-Principles Derivation

*(No retrieval used for this section — reasoned from primitives only.)*

**Primitives.** The system is: several independent agents, each a separate
process/session, running on independent schedules (cron fires, manual
invocations, webhook wakeups), with no shared memory and no synchronous
channel between them. The only shared substrate is a git repository. Any
coordination must happen through file reads/writes mediated by git commits,
which are themselves asynchronous and can race.

**The core hazard: lost updates.** Suppose two agents both want to report
status via a single mutable file, `status.json`. Agent A reads the file,
computes a new version with its own status merged in, and writes it back.
Agent B does the same, concurrently, working from the *same* stale read.
Whichever writes last wins outright — B's commit doesn't know A's write
happened, so A's contribution is silently destroyed. This is the classic
read-modify-write race from database theory; it requires either a lock
(mutual exclusion around the read-modify-write) or a merge function. In an
async, cron-driven, multi-container system, there is no reliable lock — no
agent can block on another's turn. So mutable shared state needs conflict
resolution it structurally cannot get.

**Why append avoids the hazard.** If instead every agent's operation is
"add a new block to the end of the file, don't touch anything else," then
two concurrent writers no longer conflict in *content* — the worst case is
a git merge conflict on *where* the new text gets spliced in, which is a
trivial, mechanically resolvable conflict (both blocks exist; their
relative order barely matters since each is self-describing with an
agent/date field). This is the same reason CRDTs use grow-only sets/logs
as their conflict-free base case: if the merge operation is set union
(commutative, associative, idempotent), then order of application cannot
change the result. An append-only file is effectively a grow-only ordered
log, and its merge is close enough to union that git's line-based merge
algorithm — which is bad at semantic/structural merges but good at
"both sides added text at different places" — handles it almost for free.

**State should be a view, not a store.** A mutable `status.json` can only
ever answer "what is true *right now*, as of whoever wrote last." It cannot
answer "did agent A ever report in the last week" once overwritten — that
information is gone. An append log lets any reader fold over all entries
to reconstruct current state (event sourcing), but *also* keeps the full
history: who claimed what, when, and — since entries are never edited —
whether a claim was later contradicted. This matters specifically in a
multi-agent-with-verification context: the system already treats agent
self-reports as claims to be checked ("trust but verify"), and you cannot
verify a claim that has been overwritten before anyone read it.

**Failure containment.** If a write is interrupted (process killed
mid-write, malformed output, truncated commit), a mutable single-object
file can end up entirely unparseable — every downstream reader breaks,
including for entries that were previously fine. An append-only file with
self-delimited blocks (like the `~~~ PRAXIS_INBOX ... ~~~` fences here)
contains the damage to the newest block: a parser that reads block-by-block
can skip one malformed entry and still recover everything before it. Blast
radius is bounded to the tail, not the whole state.

**Fit with the substrate.** Git's own object model is itself append-only
and content-addressed — commits never mutate, they add new objects with
parent pointers. A file format that is itself "add new content at the end"
is homomorphic with the tool coordinating it, so git's native merge
machinery does most of the conflict-resolution work for free. A mutable
structured file (JSON object two agents both edit) fights this: git will
often report a conflict even when the *logical* edits (two different keys)
don't actually collide, because git merges are line/text-based, not
schema-aware.

**Synthesis.** For a coordination medium that is asynchronous, has no
locking primitive, is mediated by a line-based version control system, and
needs both current state and an audit trail, the append-only log wins on
every axis: conflict-free merges, bounded blast radius on partial writes,
full history for verification, and native compatibility with git's merge
algorithm. The corollary is that *current state* (e.g. "which agents are
active") should always be a materialized view computed by folding the log,
never a separately maintained mutable file — maintaining both invites the
two to drift out of sync.

## Corpus Answer

Searched: event sourcing, CRDTs (conflict-free replicated data types), and
log-centric architecture (Kafka / "the log" as a systems-design pattern).

The literature converges on essentially the same shape:

- **Event sourcing** (Martin Fowler, and formalized in Kleppmann's
  *Designing Data-Intensive Applications*) treats the append-only sequence
  of events as the source of truth, with current state derived by replaying
  ("folding") the log — exactly the "state is a view, not a store" point
  above. The stated motivations are auditability, the ability to
  reconstruct past state, and decoupling writers from a single shared
  mutable representation.
- **CRDTs** (Shapiro et al., *Conflict-Free Replicated Data Types*, and
  Kleppmann's later CRDT work) formalize why grow-only sets/logs merge
  without coordination: the merge operator must be commutative,
  associative, and idempotent, and union over a grow-only set trivially
  satisfies all three, which is why logs/sets are the base case CRDT
  designs build from, while a shared mutable "last write wins" register is
  explicitly the *lossy* case they're trying to avoid.
- **Log-centric architecture** (Jay Kreps, "The Log: What every software
  engineer should know about real-time data's unifying abstraction," the
  design rationale behind Kafka) makes the same "log as source of truth,
  every derived table is a materialized view" argument at infrastructure
  scale, and explicitly frames the log as the right integration primitive
  between decoupled, asynchronous producers/consumers.
- Git's internal design (content-addressed, append-only object store with
  commits as immutable snapshots plus parent pointers) is standard,
  documented git internals — matches the "substrate fit" argument above.

No source contradicts the derivation; if anything, the corpus is more
emphatic about it than the derivation needed to be — "the log as the
unifying abstraction for distributed data systems" is treated as close to
a first principle in its own right in that literature.

## Delta

**Category: rediscovered**

The reasoning arrived at the same structure the corpus has formalized
(event sourcing / CRDT grow-only-log / log-centric architecture) without
having looked any of it up first — commutative-associative-idempotent
merge, state-as-materialized-view, and bounded blast radius are all
standard results, independently re-derived here from the concrete failure
mode (lost updates on a shared mutable file) rather than from naming the
pattern first. This validates the reasoning process but the *content* isn't
new: it's a well-trodden result in distributed systems, just not one this
repo's own coordination files (`praxis-inbox.md` etc.) had been explicitly
justified against before.

## Commentary

The practical payoff isn't the theory — it's a concrete audit item: this
repo already does the right thing for `praxis-inbox.md` (append-only,
fenced blocks) but `wolf_live_data.json` and `scout_state.json` are
named like mutable "current state" files. If those are ever written by
more than one agent/process concurrently, they inherit the lost-update
hazard described above and should either move to append+fold, or be
clearly documented as single-writer-only. Worth a follow-up backlog item
rather than fixing blind in this spike.
