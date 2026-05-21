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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h; direct portals blocked (403/ECONNREFUSED), sourced via Benzinga/MarketBeat PTR alerts and news search
outcome: Rep. Brian Babin (R-TX) SELL FTAI Aviation $89k–$335k — Score 4 (Transportation & Infrastructure Committee member exiting aviation sector stock; committee has direct FAA/aviation oversight jurisdiction)
lesson: Congressional trading signal quality is highest when the ticker's primary regulatory exposure maps to the member's committee assignment — the sell matters less than the institutional knowledge asymmetry implied by committee jurisdiction; fast-filed PTRs (Moore: 3 days) may indicate broker-triggered compliance rather than voluntary transparency, and warrant pattern tracking
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
