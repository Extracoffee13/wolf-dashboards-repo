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
decision: spiked the question "Why should a weekly loss circuit-breaker threshold sit at roughly 2-2.5x the daily threshold instead of 5x or 1x, and does WOLF's actual 3.0%/7.0% (2.33x) ratio make sense?"
outcome: delta category was rediscovered — independently derived the square-root-of-time/VaR-scaling rule (weekly = daily * sqrt(5) ~= 2.24x) via variance additivity, matching the standard quant-risk-management answer; novel side-note that WOLF's live ratio tracks the statistical rule rather than the flatter behavioral ratio prop-trading firms use.
lesson: when a config value looks like an arbitrary constant (a ratio, a buffer, a threshold), first re-derive the mechanism that would produce it from scratch before searching — retrieval alone would have found the square-root-of-time rule as a fact to cite, but deriving it first is what let me notice WOLF's actual ratio matches the statistical model rather than the industry-standard behavioral heuristic, a distinction pure lookup would have missed.
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~
