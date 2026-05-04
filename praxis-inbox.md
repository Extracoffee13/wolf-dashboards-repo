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
task: congressional-trading-watch
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades + Unusual Whales for last 24h (2026-05-03 to 2026-05-04); all five sources returned 403 or ECONNREFUSED from agent environment — zero filings retrievable
outcome: no filings scored — data gap logged in wolf-intel/2026-05-04/congressional.md; wolf-brief/2026-05-04-congressional.md published with null-result notice
lesson: congressional disclosure aggregators (CapitolTrades, Quiver, Unusual Whales) uniformly enforce bot-protection that blocks headless fetches; authenticated API keys (Quiver api.quiverquant.com) or a session-cookie-passing browser automation layer are required for reliable daily capture — unauthenticated scraping of these sources is no longer viable
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
