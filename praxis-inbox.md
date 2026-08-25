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
outcome: no top-10 firm cleared the strict 24-48h window on relevance; top signal was FINTRX Q2 2026 family office data (92.7% of new family offices want direct investments, only 10.4% want hedge funds) paired with Hadfield & Koh's "An Economy of AI Agents" (NBER Handbook) — sharpens the thesis that operator-run PE roll-ups courting family-office capital directly, without a fund wrapper, are underpriced relative to where that capital is headed
lesson: the flagship strategy firms run weekly-to-monthly publication cadences, not daily — a strict 24-48h filter across McKinsey/BCG/Bain/Deloitte/KPMG/EY/PwC/Strategy&/Oliver Wyman/Roland Berger will come up dry most days; the sharper signal on Construct-relevant days is coming from narrower data vendors (FINTRX) and academic preprints (NBER/arXiv) that mainstream finance media hasn't picked up yet, not the big-name firms
tags: wolf,consulting,research,strategy,daily
confidence: 0.65
~~~

~~~
RESEARCH_TARGETS
routine: wolf-consulting-pulse
date: 2026-08-25
targets:
  - kind: research-deep
    topic: Is the family-office shift away from hedge funds and private credit toward direct investments and PE (FINTRX Q2 2026: 92.7% direct-investment interest vs. 10.4% hedge-fund interest among new family offices) a durable structural trend driven by first-generation entrepreneurial wealth, or a cyclical artifact of the 2026 rate/liquidity environment — and what does the answer imply for PE roll-up platforms courting family-office LPs directly instead of through a fund wrapper?
  - kind: x-pulse
    topic: family office sentiment on direct investing vs hedge funds and private credit, PE roll-up co-investment discourse, August 2026
~~~
