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
outcome: 5 candidates found scoring >=3, top one was boring-marketing-skills (local-business + AI-search skill pack, score 4)
lesson: New listings now land first in the official MCP registry (hosted remote MCPs) and on GitHub agent-skills topics. Those topics are full of identical star-farmed clone repos, so a repo's star count means nothing until its owner and creation date are checked. PyPI has no keyword search API and needs a different approach.
tags: skills,discovery,ecosystem
confidence: 0.6
~~~
