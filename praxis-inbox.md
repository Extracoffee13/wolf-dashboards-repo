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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades + Benzinga Gov Trades for last 24h; aggregators returned 403 on direct fetch, data sourced via search indexing through ~June 12 disclosure date
outcome: DHI (D.R. Horton) 6-member cluster buy pattern (32/18 buy/sell, 51 trades in 2026) + Tim Moore (R-NC) LGIH flip trade ($180K–$450K sell, Financial Services Committee) — both homebuilder auto-flags at Score 5; also: Rep. Daniel Webster (R-FL) 416 days late on REXR sale (2nd STOCK Act violation)
lesson: homebuilder cluster accumulation (DHI, LGIH) is the most persistent 2026 congressional trading signal — 6+ members across both parties holding the same sector while housing policy is active legislation is a structural tell, not coincidence; the Tim Moore LGIH flip (buy→sell in 6 days by a Financial Services Committee member) is the highest-signal individual trade in the dataset
tags: wolf,congressional,trading,intel,daily,homebuilder,DHI,LGIH,STOCK-Act-violation
confidence: 0.65
~~~
