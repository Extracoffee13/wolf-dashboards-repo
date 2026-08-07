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
decision: spiked the question "How should a daily/weekly drawdown circuit-breaker threshold be derived from first principles for an automated trading system, and how does WOLF's actual -3% daily / -7% weekly pair compare to standard risk-management practice?"
outcome: delta category was rediscovered
lesson: when a threshold formula is derived from a clean causal argument (variance is additive under independence, so multi-day risk scales by sqrt(n) not n), the argument usually also predicts the formula's own failure mode (here: autocorrelated real-world failures make the sqrt-time rule too lenient) — check the corpus for that bias direction specifically, not just the formula, since getting the bias direction right from reasoning alone is the stronger signal that the reasoning is sound.
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~
