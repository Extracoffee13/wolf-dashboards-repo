# First-Principles Spike — 2026-09-21

## Question

*Self-generated (backlog was empty/missing on this session's branch).* Relevant to
agent architecture, and provoked directly by this repo's own history:

> When should a recurring, scheduled agent task persist its output to shared
> durable state (a merged trunk) versus isolated ephemeral state (a fresh
> scratch branch per run) — and what specifically breaks when a scheduled task
> defaults to the latter?

This question wasn't picked in the abstract. Before reasoning, Step 1 required
reading `first-principles-backlog.md` from *this* repo — which didn't exist on
this session's branch (`claude/friendly-euler-43f4vw`). Checking why turned up
the actual data point that makes this question worth asking: this exact spike
has apparently run on the order of ~130 times since 2026-05-01, one per day,
each time on a brand-new randomly-named branch (`claude/friendly-euler-*`,
`claude/wonderful-hamilton-*`). Only one PR was ever opened for this repo
(#1, 2026-05-01, closed unmerged). None of the other ~129 runs' branches were
ever merged or PR'd. So every run's backlog read is against a trunk that has
never once received a prior spike's output — this file, ironically, is a live
instance of the failure mode it's about to analyze.

## First-principles answer (derived before searching)

Strip a recurring task to its primitives. It's a function invoked on a
schedule: `f(state_t) → (state_t+1, output_t)`. For the task to accumulate
value across invocations — a shrinking backlog, a growing log, an ability to
avoid re-asking the same question — invocation *N+1* must be able to read the
union of effects from invocations *1..N*. That's the whole requirement:
**a monotonically growing read set.**

There are exactly two places an invocation can commit `state_t+1`:

1. **Shared durable state** — one location every future invocation is wired
   to read by default (a trunk, a database row, an event log).
2. **Isolated ephemeral state** — a location scoped to this invocation alone,
   that no future invocation reads unless something explicitly goes and finds
   it (a fresh branch, a worker's local memory, a thread-local buffer).

Under (1), the read-set is monotonic by construction: invocation N+1's default
read is trunk, and trunk already contains 1..N's commits (once merged).
Under (2), the read-set resets to empty every time, *regardless of N*,
because nothing routes prior ephemeral state back into the one place the next
invocation looks. The task doesn't fail loudly — each individual run still
does correct, well-formed work (reads a file, reasons, writes a file, commits
it) — it fails silently, at the aggregate level, because "the backlog" and
"the log" are each-run fictions: N independent single-entry systems instead of
one N-entry system. It's N sheets of paper in N different drawers, not one
notebook.

Why would a system default to (2) at all, given the failure mode is obvious
once stated? Because branch-per-invocation is the *locally correct* default
for a different problem: protecting concurrent, human-reviewed code changes.
Isolating a session onto its own branch prevents two concurrent agents from
corrupting each other's uncommitted work, and gates changes behind a PR/review
step before they touch trunk. That's the right shape for a feature change. It
is the wrong shape for append-only bookkeeping data (a log line, a backlog
edit) that has no meaningful review step and whose *entire value proposition*
is being visible to the next automatic reader. The mechanism that protects
code correctness (branch isolation + a review gate) silently strangles a
use case that needs write-through durability, the moment nobody (human or
automation) closes the loop by actually merging. A branch nobody merges is
functionally a `/dev/null` with excellent audit logging.

Generalizing: any coordination problem where N agents must build shared
knowledge without directly messaging each other reduces to "do they have a
common rendezvous point they all read *and* write, by default, without extra
steps." If yes, work compounds. If the write side requires an extra step
(open a PR, wait for a merge) that isn't automated and isn't someone's actual
job, the default is silent non-compounding — not a crash, just an invisible
ceiling on the system's total accumulated value that looks, from any single
run's vantage point, exactly like healthy operation.

The fix implied by the same primitives: either (a) make the commit path to
trunk automatic for this class of data (auto-merge append-only bookkeeping
files, no human gate needed since there's nothing to review-reject), or (b)
move the durable state off git-branch-per-session entirely, onto something
whose write path *is* inherently shared (a database row, a single
long-lived branch the scheduler is configured to reuse rather than mint
fresh each time). Branch-per-session and durable-accumulation are not
compatible defaults; picking one silently forfeits the other unless something
explicitly bridges them.

## Corpus answer

Two independent literatures converge on the same principle:

- **Trunk-based development (CI/CD):** the orthodox rule is that branches
  should be short-lived (hours, not days) and merged to trunk *at least once
  a day*, specifically so the trunk stays the one place that reflects
  everyone's latest state and stays "green"/deployable at every commit.
  Long-lived, unmerged branches are the named anti-pattern this practice
  exists to prevent.
- **Event sourcing / durable logs:** the append-only log is treated as the
  single source of truth precisely *because* every reader defaults to it;
  worker-local or derived state is explicitly disposable and rebuildable from
  the log, never the other way around. A write that never reaches the log
  "didn't happen" from any other consumer's perspective.

Both bodies of convention independently state the same primitive I derived:
value compounds only at the one write path every future reader is already
wired to check; anything else needs an explicit bridge back to it or it's
inert.

## Delta category: **rediscovered**

The reasoning chain (read-set monotonicity → durable log vs. ephemeral
worker state → why branch-isolation is the wrong default for bookkeeping
data) landed on the same underlying principle that trunk-based development
and event-sourcing conventions state directly, without having looked either
up first. No correction to the corpus, no new framing it lacks — the value
here is that the "rediscovery" wasn't abstract: this repo's own operational
history (~129 orphaned first-principles branches, one closed-unmerged PR)
is a live, unintentional case study of exactly the failure the principle
predicts, and the reasoning explains *why* it happened (a review-gated
branch default silently applied to a use case with no reviewer) rather than
just noting that it did.

## Commentary

The interesting part isn't the principle — it's cheap to look up. It's that
deriving it from primitives *first* made the repo's own state legible as a
symptom rather than as background noise to route around. If I'd gone
straight to "no backlog file, self-generate a question" without asking *why*
there was no backlog file, I'd have missed that this task has been quietly
producing near-zero cumulative value for ~4.5 months. That's the actual
finding worth surfacing, independent of the spike mechanics.
