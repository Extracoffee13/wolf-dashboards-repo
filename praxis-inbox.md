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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h; direct portals returned 403, data sourced from aggregators indexed through June 5 2026
outcome: top filing — Rep. Josh Gottheimer (D-NJ) bought MSFT call options $758K–$1.62M on May 19 (disclosed June 3); Intelligence Committee NSA/Cyber Ranking Member; $325 strike expired June 18 — score 5
lesson: committee overlap is the clearest signal: when a member sits on the exact oversight committee for a company's primary government revenue stream (Intel Committee + Microsoft DOD cloud) and buys short-dated calls, the information asymmetry risk is structural, not coincidental
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
