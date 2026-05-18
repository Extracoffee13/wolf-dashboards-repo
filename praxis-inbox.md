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
decision: scanned Senate eFD + House CHDP + Quiver Quantitative + CapitolTrades + Trendlyne + Benzinga congressional beat for last 24h; most recent indexed batch covers disclosures filed May 7–12 (transactions mid-April to early May); no confirmed new PTRs stamped May 17–18 surfaced in aggregators at scan time
outcome: top filing — Rep. Maria Elvira Salazar (R-FL), UNH + CARR + C + GS buys, $200K–$850K total, Financial Services Committee member, Score 4
lesson: committee-jurisdiction overlap is the sharpest signal in congressional flow — members on Financial Services buying bank stocks and Foreign Affairs buying defense contractors recur as the highest-confidence pattern; size alone is a weaker filter than ticker-to-committee alignment
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
