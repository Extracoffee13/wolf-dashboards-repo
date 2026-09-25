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
decision: spiked the question "From first principles, why does the Kelly criterion determine optimal position sizing for a strategy with a known win rate and payoff ratio?"
outcome: delta category was rediscovered
lesson: multiplicative (compounding) processes require optimizing expected log-wealth, not expected wealth — that structural fact, not the formula itself, is what should be checked first before trusting any sizing rule.
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~
