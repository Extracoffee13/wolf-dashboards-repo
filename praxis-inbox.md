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
decision: spiked the question "What discount rate should be used to value a small, founder-operated business with no public equity/observable beta, and is CAPM/WACC even the right tool?"
outcome: delta category was rediscovered
lesson: when a standard financial tool (CAPM/WACC) depends on a premise (a diversified marginal investor pricing an observable beta) that plainly doesn't hold for the situation at hand (an undiversified owner of a private company), don't patch the tool — rebuild the estimate additively from the same first principle (compensate exactly for uncertainty borne by the party actually bearing it) instead of forcing borrowed proxy data into machinery built for a different premise
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~
