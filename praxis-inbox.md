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
outcome: Bain's "12 is the new 5" (PE buyouts now need ~10-12% EBITDA growth vs ~5% a decade ago to hit 2.5x) read against Roland Berger's fresh family-office data (capital rotating hard into PE/direct deals, out of VC/crypto) sharpens the Hartley Capital roll-up thesis toward operator-quality selection, not deal volume
lesson: the highest-value signal this week wasn't inside any single report — it was in the gap between a PE-strategy publication and a wealth-management publication that never cite each other; cross-vertical reading is where the edge is, and BCG's token-meter/RoAI piece is a direct operational mirror for The Construct's own agent fleet, not just external research
tags: wolf,consulting,research,strategy,daily
confidence: 0.65
~~~

~~~
RESEARCH_TARGETS
routine: wolf-consulting-pulse
date: 2026-07-08
targets:
  - kind: research-deep
    topic: Given Bain's "12 is the new 5" EBITDA growth requirement for PE buyouts to clear a 2.5x return, what specific operating-leverage levers (AI-agent-driven cost reduction, headcount ratio compression, back-office automation) are top PE roll-up operators actually demonstrating to LPs today, and which ones are provably driving the growth delta vs. just marketing language?
  - kind: x-pulse
    topic: family office and PE allocator sentiment on "AI operating model" as a roll-up due diligence requirement, Q3 2026
~~~
