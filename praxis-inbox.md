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
outcome: 5 candidates found scoring >=3, top one was svgmill (raster->SVG/PDF/DXF MCP, score 5, owner Vector); mcp.directory was blocked by network policy so the official MCP registry was used instead
lesson: New business-relevant MCPs are appearing first as hosted remote servers in the official MCP registry (~890 updates/day), not on npm or PyPI; vertical tools (sign-shop quoting, vectorising, accounting) now show up there, so the registry API is the primary feed to watch
tags: skills,discovery,ecosystem
confidence: 0.6
~~~
