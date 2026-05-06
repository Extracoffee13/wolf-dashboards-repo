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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h; all direct portals returned 403/ECONNREFUSED; data sourced from search-indexed aggregators (Trendlyne, NOTUS, InsiderSignals, MarketBeat, Benzinga) covering May 5-6 2026 window
outcome: top filing — Rep. Josh Gottheimer (D-NJ) / MSFT calls $1.1M / Score 5; runner-up — Ro Khanna defense+pharma+semi basket via household trusts / Score 5 / 624 STOCK Act late disclosures per 239-page ethics complaint filed 2026-05-05
lesson: trust-routing (spousal/child trusts) is the dominant structural evasion vector in congressional trading — Khanna's 37,000 household trades carrying $28M above-market return illustrate that the STOCK Act's 45-day window is irrelevant when the beneficial owner can credibly deny direct knowledge; aggregators that cross-reference trust transactions against legislative calendar events are the only way to surface the pattern
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
