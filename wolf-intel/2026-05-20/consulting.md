# WOLF Consulting Pulse — 2026-05-20

**Agent:** WOLF | **Task:** consulting-pulse | **Scan window:** May 18–20, 2026 (extended to May 14 for high-relevance items published in the same week)

**Firms scanned:** McKinsey / MGI · BCG / BCG Henderson · Bain · Deloitte · KPMG · EY · PwC · Strategy& · Oliver Wyman · Roland Berger  
**Arxiv:** cs.AI · econ.GN · q-fin (week of May 5–20, 2026)

---

## Papers Scored ≥ 3

---

### 1. BCG — "The AI-First Real Estate Company: An Opportunity for Structural Advantage"
**Score: 4 — Sharpens a thesis**  
**Published:** May 14, 2026  
**URL:** https://www.bcg.com/publications/2026/the-ai-first-real-estate-company-advantage

**Executive Summary**  
BCG's latest in its "AI-First Company" series turns the lens on real estate and delivers a damning benchmark: only 25% of real estate firms qualify as AI leaders compared to 40% cross-industry, and the sector invests roughly half the cross-industry average in AI—lagging even asset-heavy peers like utilities. The report maps quantified value pools by segment: development companies could unlock 400–700 bps of margin uplift via construction-site AI assistants, procurement optimization, and timeline compression (~30% faster project delivery); investment management could gain 300–400 bps IRR uplift across the deal lifecycle; and facility/property management could capture 200–300 bps EBIT improvement through invoice automation and predictive maintenance. BCG argues that the window for structural advantage is narrow and closing—the firms that act in 2026 will entrench data moats and operating-model advantages that laggards cannot buy their way into later. The prescriptive ask is direct: real estate CEOs must function as Chief AI Officers, pick two or three high-impact bets, and launch enterprise-wide AI upskilling rather than fragmented pilots.

**What it means for The Construct**  
Brand 9 should be positioned explicitly as the *AI-first signage and wayfinding partner* for homebuilders—a sector that is six years behind the AI adoption curve is primed to pay for vendors who bring the capability rather than expecting in-house build. For Hartley Capital evaluating any real estate-adjacent roll-up, this data supports embedding a hard AI-adoption delta into the value-creation thesis from day one; a target firm in the bottom quartile of AI adoption is not a discount—it is a liability unless there's a credible operational plan to close the gap within 18 months.

---

### 2. arxiv cs.MA / cs.AI — "Authorization Propagation in Multi-Agent AI Systems: Identity Governance as Infrastructure"
**Score: 4 — Sharpens a thesis**  
**Authors:** Krti Tallam  
**Submitted:** May 6, 2026  
**arXiv ID:** 2605.05440  
**URL:** https://arxiv.org/abs/2605.05440

**Executive Summary**  
This paper identifies and formalizes a security problem distinct from prompt injection that has been quietly accumulating risk in every production multi-agent system: *authorization propagation*. The core argument is that when non-human principals (agents) retrieve data, delegate subtasks, and synthesize results across organizational and system boundaries, classical access-control models—RBAC, ABAC, ReBAC—do not hold their invariants. The paper names three sub-problems: (1) *transitive delegation*, where permission chains compound beyond intended scope; (2) *aggregation inference*, where individually authorized data fragments combine to expose unauthorized conclusions; and (3) *temporal validity*, where permissions granted at task initiation are stale by execution time. From these, the author derives seven structural requirements for authorization architectures in multi-agent systems, arguing the problem must be solved at the *workflow* level, not the tool or model level. The framing—identity governance as infrastructure—positions this as an engineering primitive, not a compliance add-on.

**What it means for The Construct**  
Any agent-ops build at Hartley Capital's portfolio companies—or Hartley's own investment research infrastructure—needs identity governance wired in before the first production workflow, not retrofitted after a data-leakage incident. The seven structural requirements in this paper are a practical checklist; teams that skip it are accumulating liability at the same pace they're accumulating agent capability.

---

### 3. Deloitte — "From Operators to Orchestrators: 2026 Global Technology Leadership Study"
**Score: 3 — Useful background**  
**Published:** May 1, 2026  
**URL:** https://www.deloitte.com/us/en/about/press-room/2026-global-technology-leadership-study-release.html

**Executive Summary**  
Deloitte surveyed 660+ technology leaders globally (Dec 2025–Feb 2026) and identified a fundamental role-shift underway: technology leaders are being forced from *operators* (run uptime, manage cost) to *orchestrators* (coordinate AI agents, shape strategy, drive enterprise outcomes). Three tensions define the moment: (1) the value mandate—79% say delivering measurable enterprise value is their top priority; (2) distributed orchestration—71% of organizations now have five or more tech leaders, so coordination is the core competency; and (3) resource squeeze—41% of tech leaders report that the business sees them as unable to keep up, yet tech spending is rising only modestly. The critical tension: 81% say they are confident they can scale AI, but 75% simultaneously acknowledge their operating model must fundamentally change to do so. The gap between stated confidence and structural readiness is the central finding.

**What it means for The Construct**  
The "orchestrator" framing is the cleanest articulation yet of why Hartley Capital's highest-leverage investment is not AI tools but the coordination layer above them—the infrastructure, governance, and operating model that routes agents, routes authority, and routes value back to owners. The 81%/75% tension is the business development angle: nearly every potential portfolio company believes they can scale AI and knows they structurally cannot.

---

## Also Scanned — Below Threshold or Outside Core Scope

| Publication | Firm | Notes | Score |
|---|---|---|---|
| The Future of Digital Assets in Finance | BCG (May 18) | Capital markets / payments focus, not Construct-relevant | 2 |
| Global Principal Investors Report 2026: As Scale Grows, So Does Ambition | BCG | PE scale dynamics, sovereign wealth; useful PE context but not action-forcing | 2 |
| Inside the AI-First Private Equity Firm | BCG | Strong PE/agent AI angle but overlaps heavily with #1 and #2 above | 2 (covered) |
| Synthetic Customers Earn Their Stripes | Bain (May) | Interesting for Brand 9 campaign testing; not yet actionable at scale | 2 |
| Pulse of Private Equity Q1'26 | KPMG (May) | Deal volume hit 5-yr low (19,682); useful macro context | 2 |
| Roland Berger AI Value Gap | Roland Berger | 90% of firms report AI returns lagging spend; confirms #3 above | 2 |
| EY Loyalty Market Study 2026 | EY (May) | Customer loyalty / digital engagement; not Construct-relevant | 1 |
| KPMG Global General Counsel Outlook 2026 | KPMG (May) | Legal function transformation; not relevant | 1 |
| Deep Learning for Solving Dynamic Models in Economics | arxiv econ.GN | Macro modeling; not relevant | 1 |
| Authorization Delegation in A2A Protocol | arxiv (May 14) | Adjacent to #2; less foundational | 2 |

---

## Arxiv Honorable Mentions (week of May 5–20)

- **2605.05440** — Authorization Propagation in Multi-Agent AI Systems *(scored above)*
- **cs.MA/current** — Dynamic Attentional Context Scoping for isolated per-agent steering in multi-agent LLM orchestration (ICLR 2026 Workshop) — directly relevant to agent ops at scale; watch for full paper
- **ARIES** — Scalable Multi-Agent Orchestration for real-time surveillance (AAMAS 2026) — orchestration patterns transferable to PE deal-monitoring agents
- **APWA** — Distributed Architecture for Parallelizable Agentic Workflows (CAV 2026) — foundational parallelism patterns for Hartley's research agents

---

*WOLF Consulting Pulse is generated by scanning 10 major strategy firm publication feeds and arxiv. Scored for relevance to Brand 9 (signage/wayfinding/FL real estate/homebuilders) and Hartley Capital (PE roll-ups/agent AI/family office). Scores: 5=thesis-changing, 4=thesis-sharpening, 3=useful background, <3=skip.*
