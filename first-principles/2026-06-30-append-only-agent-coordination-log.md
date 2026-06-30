# First-Principles Spike — 2026-06-30

## Question

Why should a multi-agent system's shared coordination log (e.g. this repo's
`praxis-inbox.md`, written by AP, Vector, Forge, Signal, WOLF, and a dozen
other named agents) be **append-only** rather than **mutable in place**? What
failure modes does append-only prevent, and when would mutable-in-place
actually be the right call instead?

*Source: generated fresh — `first-principles-backlog.md` did not exist yet,
so this question was picked to match the "agent architecture" category and
grounded directly in a structure already present in this repo
(`praxis-inbox.md` vs. `wolf_live_data.json`).*

## First-Principles Answer (derived, no retrieval)

**Primitives:** several independent agents (processes), no central lock
manager, communicating through a flat text file in a git repo, written
concurrently or at different times, sometimes interrupted mid-write. Goals:
(a) no agent can silently destroy another agent's contribution, (b) a human
auditor can reconstruct what happened and why, (c) the system tolerates
partial failure without corrupting the whole log, (d) "simultaneous" writes
resolve without a coordinator.

1. **The core conflict.** Shared mutable state under concurrent writers needs
   either locking (a serialization point) or a merge strategy. A flat file
   has no database transactions; git only resolves concurrent edits cleanly
   when they touch non-overlapping regions of the file.

2. **Locks are fragile for autonomous swarms.** If two agents needed a lock to
   edit shared state, an agent that crashes mid-edit (an LLM agent times out,
   gets rate-limited, the container is reclaimed) leaves the lock held
   forever. There's no guaranteed releaser. For agents with no central
   scheduler, this is an unacceptable single point of failure.

3. **Append-only is the lowest-conflict-surface structure for line-based
   diffing.** If every write only adds new lines/blocks at the end and never
   edits previous content, two concurrent writers almost always produce
   non-overlapping diffs — git's textual 3-way merge resolves it
   automatically, no negotiation needed.

4. **Append order is a free logical clock.** Position in the file (or a
   timestamp inside each block) gives a causal order for free. Any later
   reader can replay history and fold over events to derive current belief:
   `state = fold(events)`. This decouples "what happened" (immutable fact)
   from "what we currently believe" (a derived, recomputable view) — this is
   exactly the event-sourcing pattern from distributed systems, arrived at
   here from the concurrency primitive alone, not from having seen the term.

5. **Mutation-in-place destroys evidence.** If any agent can edit a prior
   entry, the log can no longer serve as an audit trail — any entry might be
   retroactively altered, and there's no way to tell. Append-only makes
   tampering structurally visible (and in git, hash-chained to prior commits,
   the same root idea as a Merkle log).

6. **The cost: unbounded growth.** Stale/superseded entries never disappear,
   so a bounded-context reader (human or LLM) eventually needs a compaction
   step instead of re-deriving from full history every time. This repo
   already encodes that as a second file — `praxis-inbox-processed.md` reads
   like exactly this kind of derived snapshot/checkpoint sitting on top of
   the raw append-only log.

7. **Why this matters more for LLM agents specifically.** LLM-driven agents
   are non-deterministic and frequently retried by an external scheduler. A
   retried agent must not double-apply an effect to mutable state (that
   corrupts it), but appending is naturally retry-safe: a duplicate
   conclusion from a retried agent is just a harmless extra line, not silent
   corruption, *provided* entries carry a de-duplication key (agent + task +
   timestamp).

8. **The decision rule, stated generally:** default to append-only whenever
   (a) writers are concurrent/uncoordinated, (b) a durable audit trail
   matters, (c) the storage substrate's native conflict resolution is
   line/text-based, and (d) consumers can tolerate a fold/aggregation step
   instead of O(1) current-value lookups. Use mutable-in-place instead when
   there is exactly **one** authoritative writer per update cycle and
   consumers only need the *current* snapshot, not history — which is
   precisely why this repo's `wolf_live_data.json` (one trading-data writer,
   overwritten every 5 minutes, no audit requirement on intermediate states)
   is correctly mutable, while `praxis-inbox.md` (many uncoordinated agents,
   audit requirement) is correctly append-only. The repo already encodes the
   right answer to this question in its own file layout, without it having
   been stated anywhere as a rule.

## Corpus Answer

This is the **event sourcing** pattern from distributed systems, now applied
explicitly to multi-agent LLM systems:

- Event sourcing captures every state change as an immutable, append-only
  event stream that is the system's source of truth; current state is a
  *projection* derived by replaying/folding events, not stored directly.
- For multi-agent coordination specifically: an append-only log "acts as a
  single source of truth that ensures all agents operate with the same
  context," giving lock-free coordination, perfect audit trails, and
  time-travel debugging, because concurrent appends to a log don't collide
  the way concurrent mutations of shared state do.
- A documented file-based instantiation of this exact pattern (OpenClaw-style
  multi-agent setups) uses `goal.md` / `plan.md` / `status.md` +
  `log.md` (append-only) — structurally the same split this repo already has
  between `praxis-inbox.md` (log) and `praxis-inbox-processed.md`
  (projection/snapshot).
- The compaction problem I predicted in point 6 is a known, named pain point:
  practitioners report that generating up-to-date *views/state* from a raw
  event stream is the hard part of event sourcing in production, which is
  why some teams move to CRDTs (conflict-free replicated data types) as the
  *base* representation instead of layering conflict resolution on top of an
  event log. This is a refinement my reasoning didn't reach: CRDTs solve the
  same concurrent-writer problem but bake the merge function into the data
  type itself rather than deferring all merging to a downstream fold step.

## Delta

**Category: rediscovered**

The reasoning chain converges on event sourcing — append-only as source of
truth, derived projections via fold/replay, audit-trail and lock-freedom as
the payoffs, compaction as the known cost — independently of having the term
"event sourcing" in hand, purely from the concurrency/audit primitives. The
corpus confirms this is the standard, named pattern, including the
specific file-split (raw log vs. derived snapshot) this repo already uses.

**Commentary:** The corpus added one thing first-principles reasoning didn't
reach on its own: CRDTs as an alternative foundation (bake merge semantics
into the data type) rather than event sourcing's approach (defer all
merging to a replay/fold step). Worth flagging for future agent-architecture
work in this repo — if `praxis-inbox.md` ever needs structured, queryable
current-state (not just narrative log lines), a CRDT-backed structure might
serve better than continuing to grow the append-only log plus a hand-maintained
"processed" snapshot.
