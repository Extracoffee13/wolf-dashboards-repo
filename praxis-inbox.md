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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades + Benzinga + Trendlyne for last 24h (June 11-12, 2026); government portals blocked (403/ECONNREFUSED), data confirmed via aggregator cross-reference
outcome: top filing — Rep. Maria Elvira Salazar (R-FL) bought Biogen (BIIB) in 3 tranches ($52K–$130K, May 11-12) disclosed June 10-11; FDA breakthrough designation for Biogen's Salanersen drug announced June 11 — 30 days after her purchase; score 3. STOCK ACT DRIFT FLAG: Rep. Tim Walberg (R-MI) disclosed Apple (AAPL) purchase ($154K–$560K) 481 days late (txn Feb 7, 2025, filed June 3, 2026).
lesson: Congress members with zero trading history who suddenly accumulate a position in 3 tranches across multiple accounts on consecutive days — especially in biotech ahead of an FDA catalyst — represent the highest-conviction signal pattern even at small dollar sizes; multi-tranche same-day systematic buying across account types is a behavioral tell worth tracking regardless of size bucket
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
