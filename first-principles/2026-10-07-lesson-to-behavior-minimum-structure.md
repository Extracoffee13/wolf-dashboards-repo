# Spike 2026-10-07 — What is the minimum structure a multi-agent system needs so a recorded "lesson" actually changes future behavior?

**Process note (honesty):** the backlog was missing, so I generated this question. The first-principles chain below was reasoned from primitives; the corpus searches were fired in the same tool batch, so I did not see results before committing to the chain, but the file itself was written after results returned. Treat the "no retrieval" purity as ~85%, not 100%.

## First-principles answer

**Primitives.** An agent's behavior at time t+1 is a function of (a) its weights/instructions, (b) the context it is handed, (c) the world state. A "lesson" is a piece of text. Text only changes behavior if it enters (a) or (b) at decision time. So the problem decomposes into a pipeline, and a lesson fails if any link breaks:

1. **Capture** — an event is observed and a candidate lesson is written. Needs a trigger (someone/something notices a delta between expected and actual).
2. **Fidelity** — the lesson states a cause, not just an outcome. "X failed" changes nothing; "X failed because assumption A was false" is actionable.
3. **Scope** — the lesson names the condition under which it applies (when does it fire). Without a scope it is either never retrieved or retrieved everywhere (over-generalization).
4. **Storage** — durable, addressable location, outside any single agent's ephemeral context.
5. **Routing/retrieval** — at the moment of a future decision of the same class, the lesson is *in the context*. This is the crux: a lesson in a file nobody reads is equivalent to no lesson. Retrieval must be keyed on the situation, not on the lesson's author or date.
6. **Compliance** — the agent, having seen it, acts differently. For an LLM this is mostly free if the lesson is in-context and unambiguous; for a human org it is the hard part. For machines the better move is to remove the choice: convert the lesson into a gate/check/default that executes regardless of whether anyone "remembers".
7. **Verification** — a measurable test that the behavior actually changed (the same failure did not recur). Without it you cannot distinguish a working lesson from a decorative one, and bad lessons (wrong causal story) persist forever.
8. **Decay/revision** — lessons are hypotheses. Needs a way to retire or revise them, or the store accrues contradictions and false generalizations.

**Minimum viable set.** Strip to what cannot be removed: a *write path* (capture with cause+scope), a *read path keyed to situations* (retrieval into context at decision time), and a *feedback signal* (did the failure recur). Everything else (ranking, summarization, decay) is optimization. Notably, the strongest form is not memory at all: **promote the lesson into an enforcement mechanism** (a gate, a lint, a default) so behavior changes without depending on recall. The hierarchy of strength: gate > in-context rule > searchable note > unread file.

**Implication for this ecosystem.** An inbox that agents append to (capture) with no read path at decision time and no recurrence check is only step 1+4. It records; it does not teach. The missing links are retrieval-by-situation and verification.

## Corpus answer

- **Reflexion / ExpeL / Voyager** (agent literature): write verbal post-mortems into episodic memory, prepend to next attempt; ExpeL extracts contrastive rules of thumb; Voyager stores *executable* skills in a library, i.e. promotes lessons into reusable code. Known risks flagged: self-reinforcing error and over-generalization from one context. ([survey](https://arxiv.org/pdf/2603.07670), [Reflexion summary](https://www.promptlayer.com/glossary/reflexion))
- **Argyris/Schön** (organizational learning): most "lessons learned" are single-loop (tactic fixes) and leave governing assumptions untouched; defensive routines block the revision that would make the lesson stick. ([infed](https://infed.org/mobi/?p=396))

## Delta category: **rediscovered** (with one partial novel framing)

Matches: capture→store→retrieve-into-context loop (Reflexion); over-generalization and self-reinforcing error (= my scope and decay/revision links); cause-not-outcome fidelity (= double-loop: modify the governing assumption, not just the action); promote-to-executable (= Voyager skill library).

Slight extra framing not seen in the results: an explicit **strength hierarchy** (gate > in-context rule > searchable note > unread file) and treating **recurrence of the failure as the only valid verification**. Not enough to call it novel; the corpus likely has it under "poka-yoke"/error-proofing, which I did not search.

## Commentary

Durable takeaway for the Construct: count a lesson as learned only when a gate or situation-keyed retrieval exists and recurrence is checked. Audit praxis-inbox.md for lessons that have neither.
