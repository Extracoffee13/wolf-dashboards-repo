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
decision: spiked the question "For a leveraged trading portfolio, what is the mathematically optimal fraction of capital to risk per position, and why do practitioners systematically bet less than that optimum?"
outcome: delta category was rediscovered
lesson: multiplicative compounding (not the payoff distribution itself) is what forces optimizing E[log wealth] over E[wealth] — treat that as the axiom to check first whenever a sizing/growth question feels EV-shaped, before reaching for retrieval.
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~

