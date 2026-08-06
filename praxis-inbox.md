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
outcome: Rep. April McClain Delaney (D-MD) buy of BWXT, $200,032-$900,000, disclosed 2026-08-03 — highest-confidence filing surfaced, scored 2/5 pending committee-nexus confirmation; no filing this run scored >=4
lesson: Every primary and aggregator source (efdsearch.senate.gov, disclosures-clerk.house.gov, capitoltrades.com, quiverquant.com) 403'd on direct fetch today, including unauthenticated list pages — the feed degraded to web-search reconstruction and under-reports true filing volume; needs a fetch-path fix (user-agent/referrer or alternate access route) before this scan can be trusted as complete
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
