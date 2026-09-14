# First-Principles Spike — 2026-09-14

## Question

In a multi-agent AI system where several sub-agents each produce partial work
that must be combined into one final output, should the architecture route
all coordination through a single central orchestrator (hub-and-spoke), or
should sub-agents communicate directly with each other (mesh)?

(Picked fresh — `first-principles-backlog.md` was missing, so this is queued
as the first entry going forward. Chosen for relevance to The Construct's own
agent architecture: Praxis inbox, WOLF, Hermes swarm topology.)

## First-Principles Answer (derived, no retrieval)

Start from primitives:

- An agent is a bounded reasoning process: finite context window, an action
  loop, no memory beyond what's in that window.
- Coordinating agents requires exchanging information — task assignments,
  intermediate results, conflicts, dependencies.
- Communication is not free: every message consumes tokens/context on both
  sender and receiver, and creates a synchronization point (latency).
- Correctness of the combined output requires *someone* (or something) to
  reconcile potentially overlapping or conflicting sub-agent outputs into one
  coherent result.

**Topology edge-count.** Hub-and-spoke has N edges (each of N workers talks
only to the hub). Full mesh has N(N-1)/2 edges — quadratic growth. This is
the standard distributed-systems tradeoff: centralization cuts edge count but
creates a bottleneck/single point of failure; decentralization is more
robust per-edge but multiplies coordination overhead.

**Task dependency structure decides the winner.** If subtasks are largely
independent (parallelizable, "embarrassingly parallel"), a hub is efficient:
spokes don't need each other's intermediate state, only need to report
results back — coordination cost is O(N), not O(N²), and the hub gets
synthesis "for free" since it already sees everything. If subtasks are
tightly interdependent (each agent's next move depends on another's latest
state), direct peer communication removes the double-hop through the hub,
but at the cost of emergent complexity: inconsistent shared state, races,
and much harder debugging of "who told whom what."

**The LLM-specific crux.** In a generic distributed system, a hub/broker just
routes bytes — it doesn't have to "understand" traffic, so its scaling limit
is bandwidth. An LLM orchestrator is different: it has to actually *read and
reason over* every worker's report inside its own bounded context. So the
hub's scaling limit isn't throughput, it's the hub's own attention budget.
As N grows, a flat hub-and-spoke design eventually degrades not by getting
slow, but by getting *wrong* — the orchestrator's context fills with
cross-talk and it loses fidelity on any single thread.

**Prediction from these primitives:**
1. Hub-and-spoke should be the default for the common case: independent,
   parallelizable subtasks converging to one synthesized output. Cheapest
   coordination, simplest failure semantics, free synthesis.
2. As agent count scales, the fix is not "switch to mesh" — it's
   hierarchical/tree hub-and-spoke: sub-orchestrators compress/summarize
   worker output before passing it up, keeping every individual hub's
   context bounded regardless of total agent count.
3. True mesh (full N-to-N messaging) is only justified when subtasks are
   tightly coupled and need low-latency shared state — and even then, the
   practical implementation is usually a shared blackboard/state store (a
   *data* hub) rather than literal peer-to-peer messaging, because raw peer
   messaging without a single source of truth just reintroduces the
   synthesis problem at every node instead of solving it once.

So: topology should track the dependency graph of the work, not be chosen
by default preference — but for the specific shape most agent systems
actually have (decompose → parallel work → synthesize), hub-and-spoke wins
on first principles, with hierarchy as the scale fix and blackboard/shared
state as the fix for tight coupling.

## Corpus Answer

Anthropic's own published account of Claude's multi-agent research system
("How we built our multi-agent research system") describes exactly an
orchestrator-worker pattern: a Lead Researcher agent plans and decomposes
the query, spins up 3-5 subagents in parallel, and synthesizes their
findings (with a separate citation pass). The critical design choice
Anthropic reports: subagents are deliberately isolated — each gets a
self-contained task description and a *fresh* context window, doesn't know
the other subagents exist, and cannot coordinate with them mid-task. This is
explicitly framed as what keeps the lead agent's context from "drowning in
cross-talk" — the same context-budget bottleneck reasoned to above.

Broader industry material on orchestration patterns (hub-and-spoke, mesh,
hierarchical, blackboard) confirms: hub-and-spoke is reported as the most
common pattern in production; mesh communication is explicitly noted to
scale O(N²); blackboard/shared-memory is presented as the standard fix when
agents need shared state without full peer messaging (with benchmarks
showing it outperforming naive alternatives). One recent benchmark
(AdaptOrch) goes a step further than anything derived here: it finds that
*adaptively switching topology per task* (a router choosing hybrid/parallel/
hierarchical per query, not committing to one topology system-wide) beats
any single fixed topology by ~23%.

## Delta

**Category: rediscovered**, with one **novel-adjacent** edge.

The core structure — hub-and-spoke as default, the context-budget (not
bandwidth) as the real scaling constraint on the hub, hierarchy as the fix
for scale, blackboard/shared-state as the fix for tight coupling instead of
literal mesh — was arrived at independently and matches the orthodox answer
closely, including Anthropic's own stated rationale ("keeps the lead agent's
context window from drowning in cross-talk") almost verbatim to the
first-principles framing above.

The one thing not derived: the corpus's empirical finding that *dynamic,
per-task topology selection* outperforms any single fixed topology
system-wide. The reasoning here predicted topology should track the
dependency graph of the *work*, but treated that as a design-time choice per
system; it didn't go the extra step of predicting that production systems
would benefit from choosing topology *per request*, at runtime, via a
router. That's a genuinely useful refinement the corpus has and this
derivation didn't reach on its own.

## Commentary

The strongest confirmation here isn't the topology conclusion itself — that
part is close to classic distributed-systems reasoning applied to a new
substrate. It's that the mechanism *why* hub-and-spoke wins for LLM agents
specifically (bounded context as the true bottleneck, not message-passing
overhead) came out of the derivation independently and lines up with
Anthropic's own stated design rationale. That's a good sign the reasoning
chain was tracking a real constraint rather than pattern-matching to
"orchestrator is common, therefore orchestrator is right."
