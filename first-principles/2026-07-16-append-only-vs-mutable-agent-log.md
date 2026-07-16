# First-Principles Spike — 2026-07-16

## Question

Should a shared multi-agent coordination log (like this repo's `praxis-inbox.md`) be
append-only, or should agents be allowed to edit/delete each other's entries?

This came off the backlog because it's live in this repo right now: multiple agents
(AP, Vector, Forge, Signal, Cipher, Spectra, Oracle, Nexus, Ledger, Atlas, Sentinel,
Venture, Equity, Alpha, WOLF, Keystone, Cornerstone, Charlie, Architect) write
decision/outcome/lesson packets into one shared file, and there's a whole
`self-improving-loop` skill whose job is to make sure mistakes get captured and never
repeated. The append-vs-mutate choice for that log is a real design decision, not a
hypothetical.

## First-principles answer (no retrieval)

Start from the actual job the log has to do: N independent, only loosely-coordinated
writers (separate agent sessions, no shared lock, no transaction manager) need to
record what happened, in what order, so that (a) later agents can reconstruct "what
do we currently believe / what's the current state," and (b) later agents — and
humans — can audit "why do we believe that, and who decided it, and were they right."
Any design has to survive concurrent writers who don't coordinate in real time (two
agent sessions could both be appending near-simultaneously) and has to serve a
learning function, not just a storage function.

**Case for mutable (let agents edit/delete each other's or their own past entries):**
keeps the log "clean" — no stale or superseded information sitting around, no need to
mentally diff old vs new. That's the entire benefit, and it's a UX benefit, not a
correctness one.

**Case for append-only (never edit or delete, only add new entries, corrections
supersede rather than overwrite):**

1. **Concurrency is the actual hard constraint, and append-only sidesteps it.** With
   N uncoordinated writers, "two agents append near the same time" is a solved,
   low-stakes problem — worst case you get two entries in arbitrary relative order,
   both intact. "Two agents edit the same existing entry near the same time" is a
   classic lost-update race: whoever writes second silently clobbers the first
   editor's change, and neither agent necessarily finds out. A system with weak
   coordination should be designed so its failure mode is "harmless interleaving,"
   not "silent data loss." This is the same reason CPUs prefer append-friendly
   structures for concurrent logs, and why "never mutate shared state, only add
   immutable facts" is the generic fix for a large class of concurrency bugs — you
   turn a write-write conflict (hard) into a write-write-different-slots situation
   (trivial).

2. **Editability and auditability are in direct tension.** The moment an entry can be
   silently changed or removed, the log stops being evidence of what happened and
   becomes evidence of what the last editor wanted it to say. There's no way for a
   later reader to distinguish "this was corrected because the original was wrong"
   from "this was corrected because someone didn't like how it looked." An
   append-only log doesn't have this ambiguity: corrections are new entries that
   reference the old one, and the old one is still sitting there for comparison.
   This is structurally identical to why accounting uses correcting/reversing
   journal entries instead of erasing the original mistake — the erasure would
   destroy the very information (that an error occurred, when, and by whom) that the
   ledger's audit function exists to preserve.

3. **The stated purpose of this exact log is a learning loop, and learning needs the
   failure preserved, not deleted.** If the whole point of `self-improving-loop` is
   "capture mistakes so they aren't repeated," then letting an agent delete its own
   embarrassing packet is self-defeating — it optimizes for looking good over
   getting better. A learning system needs its negative examples to survive contact
   with the thing that produced them.

4. **The only real cost of append-only is unbounded growth**, and that's a separable,
   already-solved problem: periodically fold/compact the append-only history into a
   "current state" snapshot or summary view, while keeping the full history
   available underneath. You don't need to give up immutability to get a clean
   read — you need a derived view, computed *from* the immutable log, not a mutable
   log pretending to be a view.

**Prediction going in:** this is very likely a well-trodden pattern with an
established name (something like "immutable event log," "append-only ledger," or
"event sourcing"), because the underlying forces — concurrent writers, need for
audit trail, need to separate raw history from derived current-state — are generic
distributed-systems and accounting forces, not specific to AI agents. I'd expect the
corpus to agree strongly, possibly with more precise vocabulary and additional
nuance around snapshotting/compaction mechanics that I'm gesturing at but haven't
worked out in detail.

## Corpus answer (web search)

The named pattern is **Event Sourcing** (often paired with **CQRS**, Command Query
Responsibility Segregation), and the corpus confirms the reasoning point for point:

- "Event Sourcing records every state change as an immutable event in an
  append-only log; the current state is a projection of these events... Instead of
  storing the current state and overwriting it with every change, you store every
  change itself." Events are never changed or deleted.
- **Concurrency**: "This avoids concurrency update issues since new events are only
  appended to the end of logs" — confirms the write-write-conflict-to-different-slots
  argument directly. One source frames it for this exact use case: "lock-free
  multi-agent coordination."
- **Audit trail**: "Every change is recorded, enabling full traceability... any
  malicious attempt to alter history would be evident by a discontinuity or invalid
  hash if cryptographically secured" — same argument, plus a mechanism (hash
  chaining) I didn't derive.
- There is a paper specifically on this: *ESAA: Event Sourcing for Autonomous Agents
  in LLM-Based Software Engineering* (arXiv 2602.23193) — the exact pattern applied
  to exactly this problem (multi-agent LLM systems), which is a strong signal the
  underlying forces are recognized as general rather than something I'm overfitting
  to this one repo.

Nuance the corpus adds that I under-specified:

1. **Replay cost, not just storage growth.** I identified "unbounded growth" as the
   cost and waved at snapshotting as the fix. The corpus is more precise: the real
   cost is *replay time* to reconstruct current state ("replaying 10 million events
   to rebuild state is slow"), and snapshots exist specifically to bound how far back
   a reader has to replay from, not just to keep storage small.
2. **Eventual consistency window.** In CQRS/event-sourced systems, the read
   model (derived "current state" view) lags the write log by a real, nonzero
   window. I treated "derived view" as basically free; the corpus treats the lag as
   an inherent tradeoff to design around, not an implementation detail.
3. **Explicit scope warning.** Multiple sources warn against applying event
   sourcing/CQRS globally: "if your domain is straightforward, event sourcing is
   over-engineering." I argued append-only is structurally superior for *this*
   log, but didn't generalize (correctly) that it's a tool for specific
   forces — concurrent writers + audit need + derived-view need — not a default for
   all state.

## Delta category: **rediscovered**

The core structural argument (append-only log + derived current-state view beats
mutable shared state under concurrent, loosely-coordinated writers; corrections
should be new entries, not edits) matches the established pattern (event sourcing /
CQRS) point for point, arrived at independently from the concurrency and audit
forces rather than from knowing the pattern's name. The corpus adds real value on
top: precise vocabulary, a mechanism for tamper-evidence (hash chaining) I didn't
think of, a more precise account of the actual cost (replay time, not just storage),
the eventual-consistency framing for the read side, and an explicit warning against
over-applying the pattern outside contexts that actually need it.

## Commentary

`praxis-inbox.md` as currently structured (append `~~~ PRAXIS_INBOX ~~~` blocks,
never edit past ones) is already the right shape — this spike is a confirmation, not
a course correction. Two concrete improvements worth carrying forward: (1) if an
agent needs to retract or correct a prior packet, it should append a new packet that
references the old one rather than editing it in place — this repo doesn't currently
have that convention explicitly written down; (2) as the inbox grows, a periodic
"snapshot" summary (e.g., a rolled-up `praxis-inbox-summary.md` regenerated
occasionally from the full log) would give readers a fast current-state view without
requiring the full log to be re-read every time, mirroring the snapshot mechanism
the corpus describes.
