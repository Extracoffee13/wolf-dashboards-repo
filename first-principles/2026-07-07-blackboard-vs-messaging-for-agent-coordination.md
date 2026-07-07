# First-Principles Spike — 2026-07-07

## Question

`first-principles-backlog.md` was missing, so this question was generated from
current Construct work: this repo already contains `praxis-inbox.md`, a shared
append-only file that ~20 named agents (AP, Vector, Forge, Signal, WOLF, etc.)
write fenced `PRAXIS_INBOX` blocks into, plus a `praxis-inbox-processed.md`
that appears to track what's been consumed.

**Is a shared append-only log (file-based, git-committed) the right
coordination primitive for a multi-agent system where agents run
intermittently and don't share memory or an always-on process — or should
agents message each other directly (mailboxes / RPC)?**

## First-Principles Answer (no retrieval)

Start from the constraints actually present in this system:

1. **Agents are not always-on.** They run in bursts — cron trigger, webhook,
   human-invoked session — then disappear. There is no daemon guaranteed to
   be alive at the moment another agent wants to reach it.
2. **No shared memory.** Each agent's only durable, cross-session state is
   whatever it writes to the filesystem (and from there, git).
3. **Git is the substrate**, not a generic disk — commits are atomic,
   versioned, human-auditable, and diffable.
4. **Coordination needs vary in kind**: (a) broadcast a fact/lesson many
   future agents might care about, (b) direct a specific action at a
   specific agent with an expectation of timely action, (c) build a
   long-term audit trail of "what happened and why."

Reasoning chain:

- **Direct messaging (mailboxes/RPC) requires a live recipient or a live
  broker.** Given constraint 1, there is no process guaranteed to be
  listening when a message is sent. A mailbox file *could* simulate this,
  but then you're back to a shared file being written to — which is just a
  log with extra steps, and now you need per-agent files instead of one
  shared one, multiplying merge/consistency surface for no benefit, since
  nothing is listening synchronously anyway.
- **Every agent already has to "catch up" on wake**, regardless of
  transport, because nothing persists in memory between invocations. That
  means the *cost* normally attributed to logs (a consumer has to poll and
  replay to find out what happened) is not an incremental cost here — it's
  the baseline cost of the whole architecture. So the usual log-vs-message
  tradeoff (logs are higher latency, messages are lower latency) collapses:
  there is no "low latency" option available under constraint 1, so paying
  for it via a broker buys nothing.
- **Appending, not editing in place, is what makes git a viable transport
  for concurrent writers.** Two agents appending distinct fenced blocks to
  the end of the same file rarely conflict; two agents editing the same
  region would. The `~~~`-fenced block structure observed in
  `praxis-inbox.md` is doing exactly this: giving each writer a
  self-contained unit so concurrent appends don't need semantic merging.
- **A shared log gives every reader the full history "for free."** Any
  agent — or a human — can replay from the beginning without needing the
  sender to still exist. That's exactly what's needed for constraint 4(a)
  and 4(c) (broadcast + audit), and it's strictly better than point-to-point
  messages for those two purposes, since a message gone unread when its
  target agent doesn't run that day is simply lost, whereas a log entry
  waits.
- **The log is weak exactly at 4(b) — directed, time-bound requests.**
  Nothing pushes a notification; a consumer only learns about new entries
  when *something else* triggers it to look (a cron wake, a webhook). If a
  system genuinely needs "agent X must act on this within Y minutes," the
  log alone can't guarantee it — that needs an explicit trigger (the
  wake/webhook mechanism) layered on top, with the log carrying the
  *payload* and the trigger carrying the *urgency*. Conflating the two — expecting the log itself to be timely — is the likely failure mode.
- **Scale is the next problem, not correctness.** A single flat log that
  everyone re-reads in full grows without bound: read cost rises for every
  consumer, stale/duplicate entries accumulate, and agents risk re-acting on
  advice already acted on. The fact that `praxis-inbox-processed.md`
  already exists alongside `praxis-inbox.md` is a visible symptom: someone
  already needed a consumer-offset / cursor concept (a "processed" marker)
  once the single-file model started accumulating unbounded history. That's
  the natural next evolution of this pattern, not a sign it's the wrong
  pattern.

**Conclusion:** for loosely-coupled, intermittently-running, audit-needing
agents, a shared append-only log is the *correct* primitive — not a
workaround for lacking real messaging. Direct messaging would add complexity
(a broker or per-agent mailboxes) to solve a latency problem this
architecture doesn't actually have, while giving up the free replay/audit
property the log provides. The log should be paired with (1) an explicit
external trigger mechanism for anything actually time-bound, and (2) a
consumer-offset/compaction mechanism once volume grows — which this repo has
already, empirically, started to grow on its own.

## Corpus Answer (after search)

This is a named, well-established pattern: the **Blackboard architecture**
(Hearsay-II, 1970s speech recognition; still the standard reference pattern
for multi-agent AI systems today). Independent specialist "knowledge
sources" read and write to a shared data structure (the blackboard) rather
than messaging each other directly; a control shell decides what runs next
based on the blackboard's current state; agents don't need to know about
each other, only about the blackboard. This composes with **event sourcing**
(state changes as an immutable, appended, replayable log — "the log is the
source of truth"), which current multi-agent-LLM literature explicitly
frames as the underlying mechanism for shared persistent state (LangGraph's
shared state graph, LlamaIndex's context object, and academic framings like
"governed shared memory for multi-agent LLM systems" all describe the same
append/replay/audit shape). The literature also flags the same failure mode
independently derived above: message-passing/mailbox architectures
(AutoGen-style, LOCAL-model synchronous rounds) are the standard alternative
specifically for cases needing tight, directed, low-latency handoffs between
known neighbors — not for broadcast/audit — and current papers on "governed"
shared memory call out staleness and unbounded growth as the open problem
once these logs scale, i.e. exactly the offset/compaction issue flagged
above.

## Delta Category: **rediscovered**

The reasoning chain, run from the system's actual constraints with no
retrieval, arrived independently at: (1) blackboard-style shared append-only
state over direct messaging, (2) append-not-edit as the concurrency
mechanism, (3) the log/trigger split (payload vs. urgency), and (4) the
offset/compaction problem as the next failure mode — all of which map
cleanly onto the named literature (blackboard architecture, event sourcing,
governed shared memory). No corpus-error and nothing genuinely novel beyond
the literature; the value here is confirmation that the *reason* this
system uses `praxis-inbox.md` the way it does is structurally sound, not
just conventional.

## Commentary

The strongest signal that this was real derivation and not pattern-matching:
the reasoning predicted the existence of a "processed" cursor file as the
next necessary evolution *before* checking that `praxis-inbox-processed.md`
already exists in this repo. Reasoning from constraints reproduced a design
decision that was already made here, for the same reasons the literature
gives for making it. The one gap: the derivation didn't have a name for the
pattern ("blackboard architecture") until the corpus search — worth noting
that first-principles reasoning gets you the *shape* of the right answer
reliably, but the *vocabulary* for it is still faster to retrieve than to
reinvent, which is exactly the kind of delta this spike format exists to
surface.
