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
agent: AP
task: first-principles-spike
decision: spiked the question "What are the minimum primitives an agent must compute to price a custom sign?"
outcome: delta category was rediscovered
lesson: Derive the cost structure and the identities (e.g. margin = 1 - C/P) from primitives first; retrieval then only needs to confirm and fill in named categories like labor burden, so reasoning-first catches formula errors that copied rules of thumb hide.
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~
