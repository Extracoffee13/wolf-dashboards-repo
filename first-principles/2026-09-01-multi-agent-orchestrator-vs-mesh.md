# First-Principles Spike — 2026-09-01

## Question

For a multi-agent system where subtasks have varying degrees of
interdependency, should agents coordinate through a central orchestrator
(hub-and-spoke) or communicate peer-to-peer (mesh), and what determines the
crossover point between the two?

## First-Principles Answer (derived without retrieval)

Start from the primitives that actually constrain an LLM-agent system:
agents are processes with a *bounded* context window; every message one
agent sends must be read into the receiving agent's context, which costs
tokens, time, and attention (more context = more dilution risk); tasks have
a dependency graph (some subtasks are independent and parallelizable, some
need another agent's output before they can proceed); failures happen
(an agent can err, stall, or hallucinate) and left unchecked they propagate
to whatever reads that agent's output; and eventually *someone* has to
decide the system is done and produce one coherent final result.

**Hub-and-spoke (orchestrator-worker).** A central node holds the task
state, decomposes it into subtasks, dispatches them, and collects results.
Message count scales O(N) with the number of workers, since each worker
only ever talks to the hub. Crucially, each worker's context stays small —
only its own subtask and inputs — so workers are isolated from each other's
noise. The hub absorbs everything, which means the hub's context is the
system's real bottleneck: it must hold enough of every worker's output to
synthesize a final answer, so this architecture strains once the number or
size of worker outputs grows large. Failure isolation is clean: a worker
that errors is visible only to the hub, which can retry or reassign without
any other worker ever seeing the failure. Global coherence is nearly free,
because the hub is the only party that needs a global view — it can
arbitrate conflicting outputs and decide termination unilaterally. The
weaknesses are a single point of failure (a stalled or wrong hub stalls or
corrupts everything) and a serialization tax: dispatch and collection happen
through one node, so throughput is capped by how fast the hub can issue and
absorb calls.

**Mesh (peer-to-peer).** Every agent can talk to every other agent
directly. Potential channels scale O(N²), and since every message costs
tokens to read, total communication cost grows much faster than hub-and-
spoke as N increases. There's no single context bottleneck, but there are
now many small ones — any agent that must stay coherent with several peers
has to hold all of their state, so the "one big bottleneck" of the hub is
traded for "several medium bottlenecks" distributed across the mesh. Failure
propagates faster and more widely: without a checkpoint, one agent's bad
output can flow directly into N-1 others before anything catches it.
Coherence is the hard part — nobody has a global view by default, so the
system needs an implicit or explicit consensus step (shared scratchpad,
voting, last-writer-wins), which adds rounds and messages that hub-and-spoke
gets for free via the hub's default global view.

**The crossover.** Two variables decide it: how separable the subtasks are,
and how many agents are involved. If the task graph is map-reduce shaped
(subtasks are independent, only the final synthesis needs everything),
hub-and-spoke wins outright — it's cheaper, isolates failures, and gives you
a natural termination point for free. If a small number of agents (roughly
2-3) need tight, continuous bidirectional exchange — genuine back-and-forth
negotiation over a shared artifact — routing every message through a hub
adds a wasted hop, since the hub isn't performing real synthesis in that
loop, only relay; a direct channel is strictly better there. As agent count
grows, the math forces the issue regardless of task shape: mesh cost grows
quadratically while hub cost grows linearly, so past roughly 4-6 agents,
some form of hub-and-spoke is the only economically viable topology, purely
from token-cost arithmetic — independent of any argument about coordination
quality. The natural resolution for large swarms is a *tree*: hierarchical
orchestration, where each hub manages a bounded number of children (workers
or sub-orchestrators), which extends hub-and-spoke's benefits — context
isolation, near-linear cost, clean failure boundaries — to arbitrarily large
systems by bounding fan-out at each level instead of letting any single
agent (hub or otherwise) absorb the whole system's state.

**Conclusion:** default to hierarchical hub-and-spoke orchestration for
multi-agent work; reserve direct peer channels for small, tightly-coupled
subgroups (2-3 agents in genuine negotiation) nested *within* that
hierarchy, not as the top-level topology.

## Corpus Answer

Searched web corpus (Anthropic's published multi-agent research system
writeup and general agent-orchestration-pattern literature, Sept 2026).
Findings:

- Anthropic's production multi-agent research system (Claude Research) uses
  exactly this: an orchestrator-worker pattern, a lead agent that decomposes
  a query and delegates to subagents which run in parallel. It reports a
  90.2% performance improvement over single-agent systems on internal evals.
- Their published effort-scaling rule operationalizes the same
  decomposability variable I derived by feel: 1 agent for simple
  fact-finding, 2-4 subagents for direct comparisons, 10+ for complex
  open-ended research — i.e., topology/fan-out is chosen by how separable
  the task is, matching the "map-reduce shaped tasks favor hub-and-spoke"
  conclusion above.
- Corpus explicitly names the same bottleneck: "the orchestrator becomes a
  context window bottleneck because it must hold the full task description,
  all worker results, and enough context to synthesize a final answer,"
  and names hierarchical delegation (bounding what each level must hold) as
  the fix — this is the same tree/hierarchy resolution derived above.
- Corpus names mesh/swarm communication as scaling O(N²) and flags the same
  failure mode (no global state owner → overlapping/contradictory writes)
  that I derived from the "nobody has a global view by default" primitive.
- Corpus adds empirical specifics I did not and could not derive from
  primitives alone: multi-agent orchestration costs ~15x the tokens of a
  single chat interaction, and a concrete throughput ceiling example (a
  3-second orchestrator call against 20 waiting workers ≈ 6.7 tasks/sec
  decomposition throughput).

## Delta Category

**rediscovered**

## Commentary

The reasoning chain landed on the same architecture (hierarchical
orchestrator-worker), the same deciding variable (task decomposability vs.
agent count), and the same two failure-mode arguments (context-window
bottleneck at the hub; no-global-state races in mesh) that Anthropic's own
production system and the broader orchestration-pattern literature converge
on — without having read any of it first. That's a reasonably strong
validation signal for the underlying reasoning method (bound the
constraints — context, cost-per-message, dependency graph, failure
propagation — then let the topology fall out of the arithmetic).

What first-principles reasoning could *not* produce were the empirical
numbers: the ~15x token-cost multiplier and the specific throughput-ceiling
arithmetic are facts about how these particular systems behave in practice,
not things derivable from architectural primitives alone. That's the
expected shape of the gap between reasoning and retrieval — reasoning gets
you the right shape of the answer and the right variables to check;
retrieval is still required to pin down the actual constants.
