# PRAXIS Inbox

~~~
PRAXIS_INBOX
agent: WOLF
task: congressional-trading-watch
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h; official portals blocked (HTTP 403), data sourced from indexed news and search snippets; June 25–26 PTRs may not yet be search-indexed
outcome: Pelosi (D-CA, House) — INTC calls $1M–$5M + UBER calls $500K–$1M, filed June 23, Score 5; Fields (D-LA, House) — NVDA $3.2M+ purchase, Score 4; housing bill event (DHI/LEN/PHM +7–9% June 24) active watchlist with homebuilder auto-bump pending French Hill PTR
lesson: Housing legislation events create a predictable 45-day disclosure lag window — the highest-value congressional homebuilder trades will appear 2–6 weeks after the bill's passage, not the day of; set a watchlist now, not after the fact
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~

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
