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
decision: spiked the question "What is the correct unit of pricing for custom sign fabrication work, and what cost structure should determine it?"
outcome: delta category was rediscovered — job costing (itemized materials + labor + overhead) is the correct internal model; sq footage is a communicability heuristic that breaks down across job types. First-principles reasoning arrived at the same answer the signage industry holds, with two additional framings: (1) setup cost floor as a first-class concept justifying minimum job prices, (2) installation cost is structurally decoupled from fabrication sq footage, so sq-footage-based pricing systematically undercharges complex installs.
lesson: When a domain uses a proxy metric (sq footage) as its customer-facing unit, check whether the proxy is proportional to cost across the full range of job types — if it isn't, the proxy is a UX convenience masking an itemized cost model underneath. Always build from the itemized model and derive the customer-facing price from it, not the reverse.
tags: first-principles,praxis,reasoning,brand9signs,signage,pricing,operations
confidence: 0.85
~~~
