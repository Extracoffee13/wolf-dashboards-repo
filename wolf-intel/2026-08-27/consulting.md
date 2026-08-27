# WOLF Consulting Pulse — 2026-08-27

Daily synthesis of strategy-firm white papers and research, filtered for relevance to The Construct (Brand 9 / signage / Florida homebuilders / real estate; Hartley Capital / PE roll-ups / agent AI / hedge fund ops; AI agents & agent ops at scale generally).

**Method note:** Scanned McKinsey (incl. MGI), BCG (incl. BCG Henderson Institute), Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger, plus arXiv cs.AI / econ.GN / q-fin for the week of Aug 24–27, 2026. Direct WebFetch to most firm domains was blocked by network egress policy in this environment, so dates and details below are search-snippet-derived and cross-referenced, not scraped from the live index pages — treat exact publish dates as approximate pending a human spot-check. Firms with nothing confirmed inside the 24–48h window (Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger) are noted at the bottom for completeness; none cleared the ≥3 relevance bar with a confirmed recent date.

---

## 1. McKinsey/QuantumBlack — "The State of AI in 2026" (annual global survey)

**Firm:** McKinsey (QuantumBlack) · **Source:** [mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai) · **Date:** ~Aug 25–26, 2026 (survey of 1,719 professionals; media coverage dated in-window)

**Summary:** McKinsey's flagship annual AI survey finds enterprise adoption is now broad but value capture remains thin: only 6% of organizations qualify as "AI high performers" delivering ≥5% EBIT impact from AI, even as 80% of individual workers self-report productivity gains. The standout datapoint is agentic AI's growth curve — 40% of $1B+-revenue organizations are now scaling AI agents in production, up from 27% a year ago — but deployment is still concentrated in IT/coding, knowledge management, and service ops rather than spread enterprise-wide. McKinsey's core argument: the bottleneck isn't the models, it's organizational redesign — workflow, culture, and role restructuring around agents, not tooling, is what separates the 6% from everyone else.

**What it means for The Construct:** This is the clearest outside confirmation yet that agent adoption at scale is becoming table stakes for large orgs while most of them still can't convert it to P&L — which is exactly the wedge Hartley Capital's agent-ops-inside-a-roll-up thesis is betting on: the moat isn't having agents, it's having the operating discipline to make them earn.

**Score: 5** — changes/validates a thesis we hold (agent execution discipline as the differentiator, not agent access).

---

## 2. BCG — "Capital Allocation Takes More Than Good Instincts"

**Firm:** BCG · **Source:** bcg.com/publications/2026/ (exact slug unverified — WebFetch blocked; flag for manual link check) · **Date:** ~Aug 25, 2026

**Summary:** BCG's analysis of multi-business companies finds only 30% trade above the sum of their parts, and the gap is explained by capital-allocation discipline rather than strategic quality — specifically cognitive biases like narrow framing and status-quo anchoring that keep capital flowing to legacy business lines instead of the highest-return unit. Their prescription: invest at the individual-business level rather than the aggregate-portfolio level, and set explicit portfolio-role-based allocation rules (fund, harvest, exit) rather than relying on instinct or precedent.

**What it means for The Construct:** Direct application to Hartley Capital's roll-up model — this is a testable checklist (business-level capital rules, explicit fund/harvest/exit labeling per acquired unit) worth running against the current portfolio before the next allocation cycle.

**Score: 4** — sharpens an existing thesis (roll-up capital discipline as a source of alpha, not just deal sourcing).

---

## 3. arXiv (cs.AI/cs.MA) — "Markets, Not Planners: Decentralized Orchestration of LLM Agents with Private Information"

**Source:** [arXiv:2608.23867](https://arxiv.org/abs/2608.23867) · **Date:** Aug 24, 2026

**Summary:** Introduces AgentLance, a repeated labor-market mechanism in which LLM agents bid on tasks using private cost information and self-maintained strategy notes, with a VCG-style payment rule that rewards honest bidding; winning agents can subcontract through the same market. The paper's headline result is a warning about the status quo: centralized planner-style orchestration (a single dispatcher agent assigning work) is manipulable — inserting one biased preference into the planner nearly doubles a favored agent's share of tasks, with no market mechanism to correct it.

**What it means for The Construct:** A concrete argument against building WOLF/PRAXIS-style agent coordination around a single centralized dispatcher long-term — worth a design review of whether the current inbox/routing pattern has the same single-point manipulability this paper flags, before it's load-bearing at scale.

**Score: 4** — sharpens the agent-ops-architecture thesis with a specific, testable failure mode.

---

## Other items scanned, below the ≥3 bar or unconfirmed in-window

- **BCG — "AI-Driven IT Modernization: Six Myths CIOs Must Avoid"** (~Aug 25) — guardrails/governance for AI-assisted modernization; useful background only, not portfolio-specific. Score 3, cut for space.
- **arXiv cs.AI — "Recursive Experiential–Working Memory Evolution for Long-Horizon Agent Harnesses"** ([2608.24876](https://arxiv.org/abs/2608.24876), Aug 25) — improved long-horizon agent task success via memory architecture. Relevant background for agent-ops reliability; Score 3.
- **arXiv cs.AI — "Tunable Tool-Call Rates in LLM Agents via Representation Steering"** ([2608.25198](https://arxiv.org/abs/2608.25198), Aug 25) — inference-time steering of tool-use behavior without prompt engineering. Score 3.
- **KPMG — Q2'26 Pulse of Private Equity** — PE deal/exit data, EMEA concentration in AI infra/energy; date uncertain, likely late July, outside strict window. Score 3 if re-confirmed in-window.
- **Deloitte — agentic-AI governance/control-plane series** ("only 21% have mature agent-governance models") — evergreen 2026 Tech Trends content, no confirmed fresh publish date this week. Score 3 if re-dated.
- **EY — "AI washing" governance piece** (~Aug 3) — outside window.
- **Roland Berger, PwC, Strategy&, Oliver Wyman, Bain** — nothing found confirmed inside the 24–48h window that cleared the relevance bar. Most topically relevant recent items from these firms (Oliver Wyman's agentic-AI-in-banking series, PwC's Agent Powered Performance survey, Strategy&'s agentic AI in retail/HR) are dated Jan–Jul 2026.
- **arXiv econ.GN — "The Dynamic Trade-Off of Dual-Class Shares"** ([2608.25972](https://arxiv.org/abs/2608.25972), Aug 26) — governance/control-vs-value trade-off in dual-class structures; moderate relevance to Hartley Capital structuring, Score 2–3.
- **arXiv q-fin — "Equilibrium in Closed Constant-Function Market Maker Economies"** ([2608.23915](https://arxiv.org/abs/2608.23915), Aug 24) — AMM/DeFi market-microstructure theory. Low relevance. Score 1.
