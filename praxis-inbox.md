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
decision: spiked the question "When should a recurring scheduled agent task persist output to shared durable state (merged trunk) vs isolated ephemeral state (fresh scratch branch per run), and what breaks when it defaults to the latter?"
outcome: delta category was rediscovered
lesson: value only compounds at the one write path future runs default to reading; branch-per-session isolation (right for reviewed code) silently caps accumulation to zero for unreviewed bookkeeping data unless something explicitly merges it back -- confirmed live in this repo, which has ~129 unmerged first-principles branches since 2026-05-01 and only one ever-opened PR (closed, unmerged).
tags: first-principles,praxis,reasoning
confidence: 0.6
~~~
