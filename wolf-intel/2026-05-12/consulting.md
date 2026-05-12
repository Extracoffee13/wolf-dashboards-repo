# WOLF Consulting Pulse — 2026-05-12

**Scan window:** May 10–12, 2026  
**Firms scanned:** McKinsey / MGI, BCG / Henderson Institute, Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger  
**Academic sweep:** arxiv cs.AI, econ.GN, q-fin (top 3 relevant)  
**Filter:** Brand 9 / FL real estate / signage / homebuilders · Hartley Capital / PE roll-ups · Agent AI / multi-agent ops

---

## Papers Scored ≥3

---

### [SCORE: 4] How Agentic AI Can Reshape Real Estate's Operating Model

**Firm:** McKinsey & Company  
**Source:** https://www.mckinsey.com/industries/real-estate/our-insights/how-agentic-ai-can-reshape-real-estates-operating-model  
**Published:** March 4, 2026 (surfaced prominently in May 2026 recommendation queues)

**Executive Summary**

McKinsey's real estate practice argues that most operators have confused AI *experimentation* with AI *transformation*. Summarizing leases and drafting memos generate no compound value; what generates value is redesigning the end-to-end domain — the full workflow, permissions, integrations, and governance — around what agents can now execute autonomously. The paper identifies four high-leverage domains for agentic redesign: (1) maintenance and facilities (shifting from "dispatch" to "done automatically"), (2) leasing and tenant experience, (3) asset and portfolio management, and (4) development and construction oversight. McKinsey Global Institute pegs the addressable value at $430–$550 billion annually in real estate, construction, and development combined. The key unlock is domain-level redesign: organizations that have built agent-ready permission frameworks and integration layers are pulling away from those still running point tools on legacy systems.

**What It Means for The Construct**

For Brand 9, this is the framework that separates wayfinding/signage operators who add an AI chatbot from those who rebuild estimating, permitting, and installation scheduling around agent workflows — the latter can price faster, bid more jobs, and carry fewer coordinators. Florida homebuilders are in the same trap: agentic redesign of punch-list management, subcontractor dispatch, and inspection workflows is where the real cost arbitrage lives, and Brand 9 is positioned to surface this to developer clients as a competitive differentiator in the signage/wayfinding RFP process.

**Score: 4** — sharpens the thesis that domain-level AI workflow redesign (not tool adoption) is the dividing line in real estate operations.

---

### [SCORE: 4] Inside the AI-First Private Equity Firm

**Firm:** Boston Consulting Group  
**Source:** https://www.bcg.com/publications/2026/inside-the-ai-first-private-equity-firm  
**Published:** 2026 (BCG Publications — confirmed via search May 2026)

**Executive Summary**

BCG surveyed and profiled PE firms across three operational tiers it labels DEPLOY, RESHAPE, and INVENT. The diagnostic finding: the overwhelming majority of PE firms are stuck in DEPLOY — issuing portfolio-wide mandates to buy AI tool licenses without changing a single workflow. Firms generating measurable return from AI have progressed to RESHAPE, which means redesigning core functions (deal sourcing, due diligence, portfolio monitoring, exit preparation) around AI-first logic rather than bolting AI onto legacy processes. INVENT-tier firms — a small minority — are using AI to create net-new revenue lines or business models inside portfolio companies. In sourcing specifically, AI now scans thousands of targets against proprietary criteria at a scale no human team can match; firms that have operationalized this report a compounding advantage in proprietary deal flow. The study cautions that most PE-AI value projections for 2025 missed because firms never left DEPLOY mode, and fewer than one in five portfolios has been systematically moved toward RESHAPE.

**What It Means for The Construct**

Hartley Capital's roll-up thesis should be evaluated against this taxonomy immediately: any acquisition candidate running AI in DEPLOY mode is an opportunity — the operational gap is measurable and the path to RESHAPE is a value creation lever that acquirers who understand this framework can price and execute on others cannot. The risk is that Hartley itself stays in DEPLOY on its own operations while the firms it's competing against for deals have already moved to RESHAPE.

**Score: 4** — sharpens the roll-up thesis by giving a three-tier operational diagnostic that maps directly to deal diligence and value creation planning.

---

### [SCORE: 3] AI Agents Are Scaling Faster Than Their Guardrails

**Firm:** Deloitte  
**Source:** https://www.deloitte.com/us/en/insights/topics/emerging-technologies/ai-agents-scaling-faster.html  
**Published:** 2026 (Deloitte Insights — State of AI in the Enterprise series)

**Executive Summary**

Deloitte's enterprise AI survey (3,000+ C-suite and director-level respondents) surfaces a structural governance gap that has become the defining enterprise AI risk of 2026: only 21% of organizations have a mature governance model for agentic AI, yet 74% plan moderate-to-extensive deployment by 2027. The actual production deployment rate today is just 11%. This means the next 18 months will see a large cohort of organizations deploying agents into production with immature oversight — a scenario Deloitte projects will lead to more than 40% of today's agentic AI projects being cancelled by 2027 due to cost overruns, unexpected complexity, or security incidents. The report finds that the organizations with the strongest outcomes are *not* moving fastest; they are starting with lower-risk use cases while simultaneously building governance infrastructure, then scaling from a tested foundation.

**What It Means for The Construct**

For Hartley Capital's evaluation of AI-native and AI-adopting portfolio candidates, the 11% production deployment stat is a useful benchmark — any portfolio company claiming AI agent ROI but not in the 11% is selling a roadmap, not a result. For Brand 9's own internal agent tooling decisions, this is a governance warning: the signage/wayfinding workflow automation play requires human-in-the-loop guardrails early or the project becomes a liability.

**Score: 3** — useful background; anchors the governance gap as a due diligence variable.

---

### [SCORE: 3] Reinforcement Learning for LLM-based Multi-Agent Systems through Orchestration Traces

**Source:** arxiv.org — cs.AI  
**arxiv ID:** 2605.02801  
**URL:** https://arxiv.org/abs/2605.02801  
**Submitted:** May 4, 2026

**Executive Summary**

This paper is the most technically precise account of how multi-agent LLM systems can be trained to orchestrate better — and where the science has not yet caught up with the practice. The authors decompose orchestration into five learnable sub-decisions: *when to spawn* a sub-agent, *whom to delegate to*, *how to communicate*, *how to aggregate* results, and *when to stop*. They survey eight reward design families (including parallelism speedup, split correctness, aggregation quality) and connect academic RL methods to production systems at Anthropic (Claude Code), OpenAI (Codex), and Kimi (Agent Swarm). The key finding that will age well: **no explicit RL training method yet exists for the stopping decision** — the hardest of the five to get right in production, and the one most responsible for runaway agent loops, cost explosions, and task abandonment failures. The authors release an 84-entry tagged paper pool and a JSON schema for replayable orchestration traces.

**What It Means for The Construct**

For any team building agent pipelines at Hartley Capital or in support of Brand 9 operations: the stopping decision gap is the current production risk everyone is underestimating. Until RL-trained stopping logic ships in production orchestration frameworks, every agentic workflow needs explicit human-defined termination conditions and cost ceilings — this is architecture, not configuration.

**Score: 3** — useful background with direct implications for agent ops architecture decisions.

---

## Papers Scanned but Scored <3

- **PwC AI Performance Study 2026** ("74% of AI value captured by 20% of companies"): Directionally useful but well-publicized, no new thesis.
- **Bain Global Private Equity Report 2026** (Outlook: Gaining Traction): Macro PE cycle read; no new operator-level signal.
- **Roland Berger European PE Outlook 2026**: European deal flow signal, not directly relevant to FL real estate.
- **BCG Global Asset Management Report 2026** (Rebuilding for an AI-First World): Asset management angle, limited Construct relevance.
- **McKinsey State of AI Trust 2026** (Agentic Era): Covers governance trust broadly; Deloitte report is sharper on governance gaps.

---

## Firms with No Relevant New Pubs in Window

KPMG, EY, Strategy& (PwC), Oliver Wyman: No publications directly scoring ≥3 against Construct filter in this scan window.

---

*WOLF Consulting Pulse is filtered research synthesis, not investment advice.*
