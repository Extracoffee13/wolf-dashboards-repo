# WOLF Consulting Pulse — 2026-07-15

**Scope:** McKinsey/MGI, BCG/BCGHI, Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger, plus arXiv cs.AI / econ.GN / q-fin.

**Method note:** WebFetch (direct page retrieval) was down for the full run today — every direct fetch attempt, including to non-consulting control URLs, returned HTTP 403 from the proxy layer. All findings below are reconstructed from WebSearch result snippets and cross-referenced summaries, not from reading full source PDFs directly. Firm publication calendars don't reliably expose exact drop timestamps through search either, so "last 24–48h" is best-effort: I prioritized items tied to the current mid-2026 reporting cycle (Q2 data, "midyear" framing, active July 2026 URLs) over anything with a stale 2025 or early-2026 dateline. Treat freshness as approximate, not verified, until someone reads the source PDF.

---

## 1. Agentic AI Enterprise Token Cost
**Firm:** EY | **Source:** https://www.ey.com/en_us/insights/ai/agentic-ai-token-costs

**Summary:** EY quantifies what "agentic" actually costs in production versus the simple RAG-style workflows most cost models were built around. A basic linear workflow (input → retrieval → response) ran about $0.04 per interaction in 2023; a 2026-era orchestrated agent — multiple tool calls, reasoning loops, iterative retries — runs roughly $1.20 per interaction, a ~30x increase. EY frames this alongside a Gartner data point: more than 40% of agentic AI projects will be canceled by end of 2027 on cost overruns, unclear ROI, or governance gaps. The piece argues CFOs are being shown vendor invoices that capture only a fraction of true agent TCO — orchestration, governance, retries, and remediation are the hidden line items that actually blow budgets.

**What it means for The Construct:** This is the economic argument for why "agent ops at scale" is a real discipline and not a buzzword — if a naive multi-agent system costs 30x a simple one per interaction, the moat isn't "we run agents," it's "we run agents cheaply and don't retry-loop ourselves into the poorhouse." Worth stress-testing our own agent fleet's cost-per-task against this benchmark before we pitch agent-ops-as-a-service to Hartley Capital portfolio companies.

**Score: 4** — sharpens the agent-AI-at-scale thesis with a concrete, falsifiable cost curve.

---

## 2. Private Equity Midyear Report 2026: Control the Controllable, Weather the Rest
**Firm:** Bain & Company | **Source:** https://www.bain.com/insights/private-equity-midyear-report-2026/

**Summary:** Bain's midyear check-in on PE says 2026 was supposed to be the recovery year and instead delivered three fresh shocks in quick succession: an AI-driven "SaaSpocalypse" repricing software assets, redemption stress in private credit, and an oil-price spike tied to the Iran conflict. Tech deal value fell 70% from Q4 2025 to Q1 2026 as large software transactions dried up; portfolio software valuations are down ~8% (milder than the public-market correction, but real). Bain's prescription for firms that will actually win the back half: stop waiting for a macro tailwind, lean hard into disciplined, proactive value-creation plans — including AI-driven operating improvements — and concentrate scarce capital on the few assets where the firm has a genuine "right to win" rather than spreading thin across the portfolio.

**What it means for The Construct:** This is a direct read on the roll-up thesis — it says the market is punishing spray-and-pray platform strategies right now and rewarding operators with a real, defensible value-creation playbook per asset. For Hartley Capital, that argues for fewer, better-integrated add-ons per platform rather than acquisition-count-as-a-KPI, and for leading with AI-enabled operating improvement (not just multiple arbitrage) as the underwriting case.

**Score: 4** — sharpens the PE roll-up thesis with current market discipline data.

---

## 3. Leading in the Age of AI Agents / Corporate Strategy Function in an AI-First World
**Firm:** BCG / BCG Henderson Institute | **Source:** https://www.bcg.com/publications/2026/the-corporate-strategy-function-in-an-ai-first-world ; https://www.bcg.com/publications/2025/machines-that-manage-themselves

**Summary:** BCG's read on enterprise agent adoption is bimodal, not gradual: only about 5% of companies are genuinely "agent-first," and the data doesn't show a smooth spectrum toward that state — it shows two distinct clusters, agent-first outliers and everyone else still in pilot purgatory. Their companion research on implementation puts the weighting bluntly: success with agentic AI is roughly 70% people and change management, 30% algorithm quality, and the firms furthest along are the ones that have trained more than half their workforce on the tools rather than just bought the license.

**What it means for The Construct:** Reinforces that the near-term edge in agent AI isn't model access — everyone has that — it's operational discipline and workforce fluency, which is a smaller, buildable moat for a lean shop like ours than trying to out-model the frontier labs. It also suggests the "agent-first" positioning we're building toward is still genuinely rare (5%), which is a window, not a crowded trade — yet.

**Score: 3** — useful background/confirmation, not thesis-changing on its own.

---

## Notes on what didn't make the cut
- Deloitte's "Agentic AI is scaling faster than guardrails" (governance-gap survey: only 21% of firms have a mature agent-governance model) is directionally relevant but is restating a widely-covered finding rather than sharpening a specific Construct thesis — scored a 2.
- KPMG's AM/PE AI Pulse Survey (68% piloting agents, 51% prefer human-in-the-loop) covers similar ground to the EY and Bain items above with less specificity — scored a 2, folded into background.
- No qualifying items surfaced from Roland Berger, Strategy&, Oliver Wyman, or PwC this cycle that scored ≥3 on Construct relevance — their most recent visible publications skewed toward European construction macro (Roland Berger) and wealth-management/cyber-trust surveys (Oliver Wyman, PwC) with no direct Brand9 or agent-AI angle.
- arXiv cs.MA/cs.AI: nothing from the actual last-24-48h window stood out as a strategy-relevant (vs. purely technical) contribution; closest was "Multi-Agent AI Control: Distributed Attacks Hamper Per-Instance Monitors" (arXiv:2607.07368, filed July 8 — outside the freshness window, security-of-multi-agent-systems angle, worth a second look if agent-ops security becomes a live workstream).
