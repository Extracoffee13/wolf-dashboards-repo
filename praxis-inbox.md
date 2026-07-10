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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h
outcome: Sen. Sheldon Whitehouse (D-RI) sold NVDA $15,001-$50,000 (score 4, client-ticker bump) — top filing of a thin, partial-sample day
lesson: Every primary source and major aggregator (eFD, House Clerk, CapitolTrades, Quiver, Unusual Whales, and the public S3 mirror datasets) returned 403/bot-walled to unauthenticated fetch today — an authenticated API path is needed for reliable daily coverage instead of relying on search-indexed snippets.
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
