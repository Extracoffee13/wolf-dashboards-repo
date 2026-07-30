# PRAXIS Inbox

~~~
PRAXIS_INBOX
agent: AP
task: praxis-daily-review
decision: Capture velocity is zero — both inbox files were missing and had to be initialized; no agent has written a packet yet.
outcome: All agents (AP, Vector, Forge, Signal, Cipher, Spectra, Oracle, Nexus, Ledger, Atlas, Sentinel, Venture, Equity, Alpha, WOLF, Keystone, Cornerstone, Charlie, Architect) are currently quiet; AP is the only active contributor via this bootstrap block.
lesson: The inbox files must exist in the repo before any agent can contribute; always seed them on first deploy so the local watcher has a valid target.
tags: praxis,meta,review,daily
confidence: 0.7
~~~

~~~
PRAXIS_INBOX
agent: WOLF
task: consulting-pulse
decision: scanned 10 strategy firms + arxiv for last 24-48h, filtered to Construct-relevant
outcome: top paper is arXiv's HANDBOOK.md long-context agentic instruction-following benchmark (frontier agents fail to follow standing corporate policy on up to 64% of long-horizon runs despite completing the task) — paired with BCG's 2026 investor survey showing institutional investors now demand milestone-based AI ROI proof, not narrative. Sharpens the thesis that agent-AI deployments need a policy-adherence metric separate from task-completion metrics before they're pitched as proof points to LPs.
lesson: The most decision-useful signal this cycle came from a same-week arXiv preprint, not the named strategy firms — Big 3/Big 4 insight pages were nearly dry on fresh (24-48h) Construct-relevant material and mostly blocked direct fetch (403s), so arXiv is currently the higher-signal, lower-latency source for the agent-AI-at-scale theme specifically.
tags: wolf,consulting,research,strategy,daily
confidence: 0.65
~~~

~~~
RESEARCH_TARGETS
routine: wolf-consulting-pulse
date: 2026-07-30
targets:
  - kind: research-deep
    topic: What would an auditable, long-horizon policy-adherence benchmark (in the style of arXiv's HANDBOOK.md) look like as due-diligence criteria for AI agents deployed inside a PE roll-up's back office, and which existing frameworks or vendors already measure "did the agent follow the SOP" as distinct from "did the agent finish the task"?
  - kind: x-pulse
    topic: institutional investor and LP sentiment on agentic AI ROI proof standards and "agent washing" skepticism, July 2026
~~~
