# WOLF Brief — Consulting Pulse
**2026-05-07 · Filtered to The Construct universe**

---

## The Surprise: The Best Argument Against Multi-Agent AI Just Dropped on arXiv

Most of the strategy press this week is still celebrating multi-agent systems as the architecture of the enterprise AI future. McKinsey's latest (and it's good — more below) keeps using the phrase. PwC surveyed 767 ops leaders and 57% are "comfortable" assigning agents to autonomous corrective action.

Nobody is talking about [arXiv 2604.02460](https://arxiv.org/abs/2604.02460).

The paper is titled *Single-Agent LLMs Outperform Multi-Agent Systems on Multi-Hop Reasoning Under Equal Thinking Token Budgets* and it says what the title says: once you equalize total compute, the multi-agent architecture advantage on complex reasoning tasks disappears. The benchmarks that made multi-agent look better were apples-to-oranges — the multi-agent system was simply getting more total thinking tokens. Control for that, and a single well-prompted model is as good or better.

Why does this matter for the ~18-month window where everyone from BCG to your portfolio companies' CIOs is selling multi-agent architecture as a premium offering? Because **most of the AI agent spend being approved right now is justified, at least partly, on reasoning-quality grounds.** If that justification is contested science, the ROI models get a lot harder.

The genuine advantages of multi-agent that survive this paper — parallelism, role isolation, fault tolerance, observability — are real but less exciting to put in a deck. They're infrastructure advantages, not intelligence advantages.

---

## The Supporting Data from McKinsey

McKinsey dropped ["Agents for Growth"](https://www.mckinsey.com/capabilities/growth-marketing-and-sales/our-insights/agents-for-growth-turning-ai-promise-into-impact) this week and it's worth your 10 minutes. The central finding is that AI agent ROI is a function of decisional mapping — finding the exact decisions and handoffs in a workflow and embedding agents there — not broad deployment. Companies 3x more likely to scale agents are the ones treating them as "managed talent" with accountability frameworks, not as software releases.

The vocabulary in this piece is directly portable to homebuilder and commercial real estate pitches: the physical customer journey (arrival → navigation → transaction → egress) is a sequence of decisions and handoffs. Monument signage and wayfinding are the decisional infrastructure of that journey. The analogy is tighter than it sounds when you're standing in a ground-floor sales center explaining why the sign package matters.

---

## Why Most Readers Haven't Seen This

The arXiv paper is in cs.AI, not in any of the journals where strategy consultants look. It surfaced in the AAMAS 2026 proceedings context (the academic multi-agent systems conference), which means the people who build the systems saw it; the people who buy the systems have not. The gap between those two groups is approximately where The Construct should be standing right now.

McKinsey's piece will be in every CIO's inbox by end of week. The arXiv finding won't be. That asymmetry has a shelf life of maybe 90 days before someone translates it for the business press.

---

## If I'm Wrong

**Falsifiable prediction, graded August 7, 2026:**

> Multi-agent architectures will continue to be adopted at scale in enterprise settings through Q3 2026, with no material pullback in vendor investment or consulting spend, *despite* the compute-equalization finding — because the market is not buying reasoning quality, it's buying organizational legibility (a visible AI org chart). By August 7, if fewer than two major consulting firms have published a piece explicitly walking back the "multi-agent = better reasoning" claim, the compute-equalization result has failed to move practice, and this brief was wrong about the window of asymmetric knowledge.

---

*WOLF Consulting Pulse · May 7, 2026 · Not investment advice · Sources behind paywall or academic access where noted*
