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
outcome: 5 candidates found scoring >=3, top one was scientistos (evidence-graph research skill for Claude Code/Codex)
lesson: mcp.directory and claude.com/anthropic.com are blocked by the egress proxy from this environment, so the highest-signal source for same-day releases is GitHub's live search index (topic:mcp-server / claude-skill sorted by recently-updated) — new npm/pypi packages are too fresh to show up in indirect web search.
tags: skills,discovery,ecosystem
confidence: 0.6
~~~
