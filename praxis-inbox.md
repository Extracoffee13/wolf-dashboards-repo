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
outcome: 5 candidates found scoring >=3, top one was Skills over MCP + MCP Tasks/Elicitation (claude.com, 2026-11-24)
lesson: The highest-leverage change came from the platform (servers shipping their own skills, plus Tasks/Elicitation), not from the community; new community skills cluster on GitHub's claude-skill topic, while npm/PyPI mostly carry MCP plumbing (observability, data tooling). mcp.directory is blocked by the cloud network policy, so add it to the allowlist or drop it from the sweep.
tags: skills,discovery,ecosystem
confidence: 0.6
~~~
