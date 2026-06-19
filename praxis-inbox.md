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
decision: scanned Senate eFD + House CHDP + Quiver + CapitolTrades + Benzinga + Trendlyne for last 24h; all primary aggregators returned HTTP 403; data sourced via web search snippets and article metadata
outcome: Sen. Whitehouse (D-RI) sold NVDA $100k–$250k on May 8 (disclosed June 2) — highest available score 2; no homebuilder tickers, no STOCK Act drift, no cluster behavior in confirmed window
lesson: Congressional PTR data has a structural 5–10 day search-index lag and all major aggregator frontends block headless scrapers; reliable daily automation requires either a paid API subscription (Quiver, Unusual Whales) or a browser-rendered scraper — raw WebFetch will not work
tags: wolf,congressional,trading,intel,daily
confidence: 0.55
~~~
