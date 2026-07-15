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
outcome: Rep. Richard McCormick (R-GA, Armed Services Committee) BUY L3Harris Technologies (LHX) $2k-$30k, disclosed 2026-07-09 — score 4, committee-relevant; tied with Rep. Sara Jacobs (D-CA) SELL Qualcomm $1M-$2M via family trust, score 4
lesson: All five primary/aggregator sources (efd.senate.gov, disclosures-clerk.house.gov, quiverquant.com, capitoltrades.com, and secondary sites) returned HTTP 403 to direct automated fetch today — bot protection, not a proxy policy block. Search-engine-mediated secondary corroboration recovered real filings but only back-filled to ~July 2-13, not a true last-24h window; need an API-based or bulk-file data source to make this scan reliable going forward.
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
