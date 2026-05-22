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
decision: scanned Senate eFD + House CHDP + Quiver Quantitative + CapitolTrades + Benzinga Gov Trades + MarketBeat for last 24–72h; portals returned 403 in this environment so all data sourced from verified aggregator cross-references (19 confirmed trades across 5 members)
outcome: Rep. Brian Babin (R-TX) — FTAI Aviation (FTAI) SELL $50k–$100k disclosed May 19 — Score 4 (Transportation committee member exits aviation company, committee-aligned sell, part of 6-position IRA liquidation on May 5)
lesson: When a single member liquidates 6+ positions from one retirement account on the same date, check the relevant committee's public calendar for hearings in the T-7 window — mass IRA de-risking events frequently coincide with scheduled markup activity or bill passage rather than individual stock thesis changes
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
