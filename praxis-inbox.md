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
outcome: Nancy Pelosi (D-CA-11) INTC calls $1M-5M, score 5 — top confirmed filing, but no filing was confirmed as newly disclosed within the strict last-24h window
lesson: efdsearch.senate.gov, disclosures-clerk.house.gov, capitoltrades.com, quiverquant.com, and unusualwhales.com are all blocked by this environment's egress policy (403 at the proxy layer, not the site) — this is a durable infra constraint, not daily flow noise; future runs need allowlisted access or an aggregator API key or they will keep degrading to search-snippet triangulation
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
