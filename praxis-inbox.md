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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h; official portals and all aggregators returned 403/ECONNREFUSED; data recovered via WebSearch and news-sourced PTR reporting
outcome: Rep. Rob Bresnahan (R-PA-8) — SELL CNC/ELV/UNH/CVS ~$130k — Score 5 — sold Medicaid-managed-care stocks 7 days before voting YES on ~$1T Medicaid cut; PTR filed ~May 22–27; breaking news cycle active
lesson: When government disclosure portals are inaccessible, the news cycle around PTR filings is a reliable proxy for high-signal trades — reporters track the same 45-day window and publish within hours of hot disclosures; the Bresnahan pattern (legislator sells sector-specific equity shortly before casting a vote that harms that sector) is the highest-fidelity congressional signal and recurs election cycle after election cycle
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
