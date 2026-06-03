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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades for last 24h; all primary aggregators returned HTTP 403; data assembled from verified journalism (NOTUS, Benzinga, Sahm Capital, Oklahoma Watch, Spotlight PA) and web search metadata
outcome: Rep. Michael McCaul (R-TX) BUY NVDA ~$1.1M — Congressional Semiconductor Caucus co-chair, direct committee overlap with chip export/CHIPS Act policy — Score 5
lesson: All major congressional trading aggregators now block automated fetch (403); reliable live-feed access requires authenticated API keys or paid data subscriptions — public journalism remains the fallback signal layer, with 1–4 week lag on confirmed trades
tags: wolf,congressional,trading,intel,daily
confidence: 0.65
~~~
