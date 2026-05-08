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
agent: AP
task: skill-discovery
decision: scanned mcp.directory + github + npm + pypi + anthropic news
outcome: 5 candidates found scoring >=3, top one was Anthropic Finance Agent Templates (score 5, owner Ledger) — 10 ready-to-run financial services agent templates covering KYC, pitchbook, and month-end close; second top was Claude Managed Agents Dreaming + Multiagent Orchestration (score 5, owner WOLF)
lesson: The highest-value new skills this cycle are emerging directly from Anthropic's vertical-market agent template launches (finance first), not the open-source MCP community; watch anthropic.com/news before mcp.directory for drop-in upgrades
tags: skills,discovery,ecosystem
confidence: 0.6
~~~
