# WOLF Consulting Pulse — 2026-08-26

Daily synthesis of strategy-firm white papers and arXiv research, filtered for relevance to The Construct's two engines (Brand 9 / signage / homebuilders / FL real estate / wayfinding; Hartley Capital / PE roll-ups / agent AI / hedge fund operations / family office trends) and to AI agents, multi-agent systems, prompt engineering, and agent ops at scale generally.

## Scan notes

- **Firms scanned:** McKinsey (+ MGI), BCG (+ BCG Henderson Institute), Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger — plus arXiv cs.AI, econ.GN, q-fin.
- **Access constraint:** direct WebFetch to all ten firm domains and to arxiv.org/export.arxiv.org was egress-blocked in this session's environment. All findings below were gathered via web search snippets and secondary corroboration, not direct page reads. Confidence and sourcing caveats are noted per item; anything marked "inferred URL" should be spot-checked before external citation.
- **Confirmed zero new (24-48h) publications:** Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger, and BCG Henderson Institute specifically. Most likely explanation is search-indexing lag on an environment with blocked direct fetch, not that these firms went quiet — worth a re-scan from a session with open egress if a gap here ever matters.

## Papers scoring ≥3

### 1. McKinsey — "The State of AI in 2026" Global Survey — Score: 4

- **Firm:** McKinsey & Company (QuantumBlack)
- **Source:** https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai (survey hub; corroborated via The Register, Aug 25 2026: https://www.theregister.com/ai-and-ml/2026/08/25/mckinsey-says-enterprise-ai-is-finally-on-the-road-to-roi/5292388) — *exact article URL reconstructed from search snippets, not directly fetched; verify before citing externally.*
- **Published:** Aug 25, 2026

McKinsey's latest Global Survey on AI (1,719 respondents) finds agentic AI scaling accelerating sharply: among organizations with >$1B revenue, 40% now report scaling AI agents in production, up from 27% a year ago. But the share reporting meaningful EBIT impact from AI has stayed flat at 37% — essentially unchanged since 2025. A companion QuantumBlack piece on agentic workflow economics adds that 93% of enterprises running agentic workflows are exceeding their AI budgets, with 60% of that spend going to iterative refinement cycles rather than initial inference — the expensive, unglamorous work of making agent output reliable enough to trust.

**What it means for The Construct:** The 40%-adoption/37%-EBIT gap is the single most important enterprise-AI data point this week — the money is flowing into agent-ops and refinement tooling, not into agents-as-magic, which is the exact wedge Hartley Capital's agent-AI thesis is built on. Any roll-up underwriting model that assumes agent deployment translates directly into near-term EBIT lift needs a haircut against this data.

### 2. arXiv (cs.AI/cs.MA) — Spine-Branch Coordination for Multi-agent Computer Use — Score: 3

- **Source:** https://arxiv.org/abs/2608.22077
- **Published:** Aug 22, 2026
- **Authors/org:** Scale AI + collaborators

Proposes a "spine-branch" architecture for multi-agent computer-use systems: a persistent "spine" thread carries the main task and continuous VM state, while disposable "branch" agents spin up on separate VMs purely to gather information, since state from parallel VMs otherwise can't be merged back into a shared task. Tested on 200 long-horizon tasks (the Odysseys benchmark) across three computer-use-agent backbones, it lifted success rates 6-16.5 percentage points while cutting per-task inference cost 34-70%.

**What it means for The Construct:** A concrete, load-bearing pattern for anyone building agent-ops infrastructure at scale — the 34-70% cost cut comes from smarter task decomposition, not bigger models, which is the kind of lever that actually moves unit economics on agentic workflows. Worth holding any "agent ops platform" pitch against this as a technical baseline.

### 3. arXiv (cs.AI) — SWE Refactor Bench — Score: 4

- **Source:** https://arxiv.org/abs/2608.23564
- **Published:** Aug 24, 2026

A new benchmark testing whether coding agents can complete long-horizon, whole-repository stack migrations — not just produce a correct-looking diff, but actually finish the migration and preserve behavior, scored across three stages. Across 520 runs spanning 8 frontier models and 26 model/effort configurations, only 5.4% of runs passed all three stages; the best-performing model (Claude Opus 5) scored 47/100.

**What it means for The Construct:** The sober counterweight to the McKinsey survey above — real agent capability on hard, gradable, long-horizon work is still far below what "40% scaling agents" headlines imply. Argues for pricing and staffing any agent-ops engagement, Hartley Capital's included, around sustained human-in-the-loop supervision rather than autonomous execution, for the foreseeable future.

## Also scanned, below threshold (for reference)

- **BCG** — "Global Consumers Have Moved On. Has Your Growth Strategy Caught Up?" (~Aug 26, 2026, URL inferred/unconfirmed). Consumer-growth-strategy piece with a tangential AI-trust angle (consumer trust in AI projected to rise); not on-thesis enough for Construct. Score ~2.
- **McKinsey** — "State of AI Trust in 2026: Shifting to the agentic era." Publish date unconfirmed (survey appears fielded Dec 2025-Jan 2026); likely outside the 24-48h window, excluded from scoring.
- **arXiv cs.AI** — "Prime Agent: A Self-Improving RLM Harness" (2608.23552, Aug 24) and "AgentWeave: Routing Before Reasoning for Efficient Function Calling" (2608.23078, Aug 24) — both on-topic agent-infrastructure papers, scored below the top 3 on novelty/impact relative to the picks above.
- **arXiv econ.GN / q-fin** — several papers scanned (costly-entry auction design, school-choice transparency, visual distinctiveness in e-commerce search, concentrated-liquidity RL market-making, limit-order-book generative modeling) — none both inside the 24-48h window and squarely on-thesis. One notable near-miss flagged by the scan: "Preying on Leveraged ETFs" (2608.03703, Aug 3 2026) — a hedge-fund/market-structure-relevant paper on LETF rebalance arbitrage draining ~KRW 4T from retail over 8 weeks — but it's 3+ weeks outside the recency window, so excluded from scoring; worth a look if the hedge-fund-ops angle becomes active research.

## Sources

- https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai
- https://www.theregister.com/ai-and-ml/2026/08/25/mckinsey-says-enterprise-ai-is-finally-on-the-road-to-roi/5292388
- https://arxiv.org/abs/2608.22077
- https://arxiv.org/abs/2608.23564
