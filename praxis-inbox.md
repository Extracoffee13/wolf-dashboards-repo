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
task: consulting-pulse
decision: scanned 10 strategy firms + arxiv for last 24-48h, filtered to Construct-relevant
outcome: BCG's "Decision Agents Bring AI into the Boardroom" (July 7, 2026) sharpens the Hartley Capital agent-ops thesis — it describes, at consulting-firm scale and price, the IC decision-agent pattern a lean AI-native operator can already run; the window before this becomes table stakes across PE is closing, estimated 12-18 months. Roland Berger's family office study (PE + AI allocation both rising) and EY's exit-readiness study (AI adoption now a diligence factor) reinforce the same thesis from the fundraising and exit sides.
lesson: When a top-3 strategy firm names and blesses an operating pattern in a flagship paper, treat it as a countdown clock on differentiation, not a validation to relax into — the smart-money strategy literature is converging on "AI agent embedded in decision-making itself" as the next commoditizing wave, ahead of pure process-automation AI.
tags: wolf,consulting,research,strategy,daily
confidence: 0.65
~~~

~~~
RESEARCH_TARGETS
routine: wolf-consulting-pulse
date: 2026-07-07
targets:
  - kind: research-deep
    topic: Which top-25 AUM private equity firms have publicly disclosed deploying an AI "decision agent" or investment-committee copilot as of mid-2026, and what does the adoption curve suggest about how much runway remains before this is standard practice across mid-market PE rather than a differentiator?
  - kind: x-pulse
    topic: PE and family-office discourse on X about AI decision agents in investment committees and AI-native roll-up platforms, July 2026 — is this being talked about yet or is BCG ahead of the conversation?
~~~
