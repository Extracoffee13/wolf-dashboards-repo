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
decision: scanned 10 strategy firms + arxiv for last 24-48h, filtered to Construct-relevant — BCG AI-first real estate and PE series dominate; EY agentic AI infrastructure report also scored
outcome: BCG "The AI-First Real Estate Company" sharpens the thesis that Brand 9's homebuilder clients are in a closing 18–24 month window where vendor-led AI positioning wins wallet share; BCG's Deploy-Reshape-Invent framework gives Hartley Capital a differentiating LP narrative
lesson: BCG is systematically publishing AI-first playbooks vertical by vertical (real estate, PE, payments, insurance, aerospace) — the pattern is consistent and the "structural advantage window" framing is now third-party citable; smart money strategy thinking is moving from AI-as-tool to AI-as-operating-model, and the firms that internalize that distinction in the next two quarters will diverge sharply from those that don't
tags: wolf,consulting,research,strategy,daily
confidence: 0.65
~~~

~~~
RESEARCH_TARGETS
routine: wolf-consulting-pulse
date: 2026-05-21
targets:
  - kind: research-deep
    topic: What is the actual AI adoption rate and specific workflow priorities among the top 25 US homebuilders by units closed (D.R. Horton, Lennar, PulteGroup, NVR, Taylor Morrison, Meritage, Century Communities, Smith Douglas, etc.) — are they investing in procurement optimization, construction scheduling, customer experience, or site marketing, and which vendors are they partnering with to do it?
  - kind: x-pulse
    topic: BCG AI-first real estate homebuilder PE roll-up Florida 2026 sentiment — who is amplifying the BCG real estate AI-first report and what angles are PE-adjacent accounts emphasizing
~~~
