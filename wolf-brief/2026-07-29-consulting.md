# The dark horse: your orchestration layer is your P&L, not your model

*WOLF Consulting Pulse, 2026-07-29*

Everyone watching AI spend is watching the wrong line item. A 32-author Writer paper quietly dropped on arXiv this month found that swapping the *orchestration layer* around a fixed set of frontier models — same models, same tasks, same quality bar — cut cost per task 41%, wall-clock time 44%, and tokens per task 38%. Nobody touched the model. They touched the harness: how context gets assembled, how tools get exposed, how turns get sequenced.

That's the surprise most people building agent stacks haven't priced in yet, because "which model" is the sexy decision and "how is the harness wired" is the boring one nobody budgets time for. The paper's term for the default failure mode is "token maxing" — teams buy capability with tokens (longer reasoning traces, more turns, wider tool payloads) faster than the task actually needs it, and falling per-token prices hide the bleed until someone runs the controlled comparison.

**Why you haven't seen this:** it's an arXiv preprint from a mid-tier AI vendor, not a headline from a Big Four AI-adoption survey — the kind of thing that shows up in nobody's LinkedIn feed unless they're already deep in agent-ops weeds. Meanwhile Bain's midyear PE data confirms the roll-up trade is now *the* dominant buyout structure (75.9% of U.S. deals by count are add-ons, up from ~60% a decade ago) — but raises the bar to "12 is the new 5": today's platforms need roughly 2.4x the EBITDA growth that used to clear the bar, and Bain is explicit that AI-driven operating leverage, not multiple expansion, is how winners get there.

**Put together:** the roll-up trade is more crowded and less forgiving than it was a decade ago, and the paper explains exactly where the operating leverage Bain is gesturing at actually comes from — not "add more AI," but a disciplined orchestration layer that gets the same output for 40% less spend. That's an operating-model edge, not a model-selection edge, and it's cheap to build if you go looking for it now instead of after the multiple-expansion window closes.

**If I'm wrong:** grade this in 90 days (by 2026-10-27) — if harness/orchestration-layer optimization hasn't become a named line item in at least one more major consulting firm's agentic-AI framework (BCG, McKinsey, Deloitte, or PwC) by then, this was a one-vendor curiosity, not a shift in where the real savings live.

---
*Full digest with sourcing: `wolf-intel/2026-07-29/consulting.md`*
