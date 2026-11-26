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
outcome: 5 candidates found scoring >=3, top one was @imgly/codesign-mcp (print-ready PDF/design engine over MCP, score 4)
lesson: This cycle's useful new capability shipped as npm packages that bundle an Agent Skill with a contract-derived MCP server (codesign-mcp, ffmpeg-skill), not in the directories; npm keyword search beats directory listings for freshness, and mcp.directory/modelcontextprotocol.io need allowing in network policy.
tags: skills,discovery,ecosystem
confidence: 0.6
~~~
