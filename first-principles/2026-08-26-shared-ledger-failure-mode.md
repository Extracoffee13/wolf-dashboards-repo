# First-Principles Spike — 2026-08-26

## Question

In a multi-agent system like this one, what is the actual failure mode
that a shared inbox/ledger (like `praxis-inbox.md`) is defending against,
and is a flat append-only log the right structure for it?

## First-principles answer (derived before any search)

Start from the primitives: several independent agents (processes with no
shared memory, no synchronous channel) need to coordinate action over
time. Strip away the specific implementation and ask what can go wrong
when independent writers touch shared state. There are really only a
handful of failure modes:

1. **Lost information** — an agent produces a fact (a decision, a lesson,
   a result) and it disappears before anyone else can see it.
2. **Destructive overwrite** — two agents write to the same mutable slot
   at nearly the same time, and the second write silently discards the
   first's information with no record that a conflict even occurred.
3. **Duplicate/racing action** — two agents act on the same task because
   neither could see the other was already doing it.
4. **Causality violation** — an agent acts on stale state because updates
   arrived out of the order they logically happened in.
5. **Unverifiable provenance** — after the fact, nobody can reconstruct
   who said what, when, or why, so trust and audit break down.

A shared inbox that agents only *append* to (never edit or delete) is a
structural defense against #1 and #2 specifically. The reasoning: if the
data structure is a mutable file (say, `state.json`) and two agents write
concurrently, whichever write lands second wins and the first is gone
with no trace — a silent, unrecoverable loss. If the structure is instead
append-only, then two concurrent writers producing interleaved appends
can never destroy each other's data, regardless of interleaving order.
Append is *commutative*: the union of two sets of appended lines is the
same regardless of the order they arrive in. This turns what would be a
write-write conflict (requiring a locking protocol, a merge algorithm, or
a designated arbiter) into a mere sequencing question that doesn't
threaten data integrity. That is a strictly cheaper property to guarantee
than "no data loss under a mutable, lockable shared state," which is why
it's the right *default* choice for a low-stakes, low-frequency,
multi-writer channel like this one.

Does it fully solve the coordination problem? No — and reasoning through
why is the more interesting part. An append-only log gives you durability
and non-destructive concurrent writes, but it does **not** give you:

- **A cheap notion of "current truth."** To know "what does the team
  currently believe about X," a reader has to scan the whole log and
  fold it down (take the latest entry per key, or apply domain logic to
  reconcile). A flat log is a transaction history, not a queryable
  state — those are different things, and conflating them is the most
  common mistake in systems like this. As the log grows, that fold
  becomes the bottleneck, not the storage.
- **Deduplication or contradiction resolution.** Two agents can append
  semantically identical or directly conflicting entries and the log
  will happily hold both forever. The append-only property protects
  against *accidental* loss, not against *redundant or conflicting*
  information — that has to be handled by whatever *reads* the log, not
  by the log's structure itself.
- **Staleness signaling.** Nothing about "entry #4 was appended before
  entry #9" tells a reader that #4 is superseded — that has to be
  encoded explicitly (a "supersedes" pointer) or inferred by convention
  (most-recent-wins per key), which is exactly the same fold-down problem
  as above.
- **Strong ordering guarantees across independent writers**, only
  approximate/local ones (whatever order each agent's writes land in the
  file). For this system, that's fine, because the domain — advisory
  lessons and decision logs — tolerates eventual, approximate ordering.
  A financial ledger cannot tolerate that (double-spend is real money);
  an advisory-lesson ledger can, because the cost of a stale read is
  "an agent repeats a mistake once," not "money moves twice."

So the honest first-principles answer: an append-only flat log is the
*right minimal structure* to solve the highest-cost, easiest-to-hit
failure mode (silent loss/overwrite) in a multi-writer, low-consensus-
requirement setting. It is *not* sufficient as the system's only
structure once volume grows, because it has no compaction and no
derived "current state" view. The natural next step, if this becomes a
bottleneck, is exactly what accounting systems and databases both
converged on independently: keep the log as the source of truth, but
build a periodically-recomputed materialized snapshot on top of it
(fold the log down into "current status per topic") rather than forcing
every reader to re-derive it from scratch.

## Corpus answer

This maps almost exactly onto **event sourcing** (store every state
change as an immutable, ordered, append-only event; current state is
always *derived* by replaying/folding the log, never stored as the
primary source of truth) combined with **CQRS** (the write side is the
log; the read side is a separate, rebuildable materialized view). The
append-only property is explicitly justified in the standard literature
by the same argument: writing an event is a single atomic operation,
eliminating the read-modify-write race that causes lost updates in
CRUD-style mutable state, and immutability means no write can silently
destroy another. Event sourcing and **CRDTs** are described as
complementary rather than competing: the log is the durable record, and
event-handler/merge logic is expected to have CRDT-like properties (no
conflicts, any valid interleaving of events can be applied) — an
append-only set of facts is, structurally, a grow-only CRDT (a "G-Set"),
which is why it merges across independent writers without needing a
coordinator. In distributed deployments, the standard pattern for
healing a network partition is exactly "each side keeps appending
locally, then on reunion the logs are merged and replayed to rederive
state" — the same escape hatch this system already has by virtue of
being a single shared file.

## Delta category: **rediscovered**

The reasoning chain arrived, independently, at the standard
event-sourcing/CQRS/CRDT answer: append-only as a defense against lost
updates and destructive overwrites specifically (not a general
coordination solution), with the same named gap (no cheap "current
state" without a fold/materialized view) that the corpus addresses via
CQRS read models and periodic snapshots.

## Commentary

The one piece the first-principles pass reached that's easy to skip
when quoting the pattern by name is *why the tolerance is domain-
dependent*: event sourcing's ordering/consistency requirements are
routinely relaxed in systems like this precisely because the cost
function of a stale or duplicate read is low. The corpus pattern doesn't
always spell that out — it's usually presented as a general-purpose
architecture, when its correctness argument actually leans on the
domain's tolerance for eventual consistency. Worth carrying forward: the
inbox pattern here is fine as-is, but `praxis-inbox.md` will start to
hurt exactly when someone needs "what is currently true about X" instead
of "what has anyone ever said" — that's the trigger to add a
compaction/summary pass, not a bigger log.
