# WOLF Consulting Pulse — 2026-07-30

Daily synthesis of strategy-firm white papers + arXiv research, filtered for relevance to The Construct's two engines: **Brand 9** (signage / homebuilders / FL real estate / wayfinding) and **Hartley Capital** (PE roll-ups / agent AI / hedge fund ops / family office).

Scanned: McKinsey + MGI, BCG + BCG Henderson Institute, Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger, plus arXiv cs.AI / econ.GN / q-fin (week of Jul 24–30).

**Methodology note:** Direct fetch of every firm's insights landing page (mckinsey.com, bcg.com, pwc.com, oliverwyman.com, rolandberger.com, etc.) returned HTTP 403 in this environment — all dates/titles below are reconstructed from search-indexed snippets and cross-corroboration, not live-page reads. Confidence is flagged per item. True same-day (Jul 29–30) hits were scarce this cycle; the two Theme-2 firms with the deepest agent-AI coverage (McKinsey, BCG) had exactly one verifiable in-window item each, and Bain/Deloitte/KPMG/EY/PwC/Strategy&/Oliver Wyman produced no confirmed in-window hits on either theme. arXiv was the most productive source this cycle — three of its papers land squarely on the "AI agents / agent ops at scale" theme, and IDs 2607.253xx–2607.271xx are confirmed posted Jul 28–29.

---

## 1. HANDBOOK.md: A Benchmark for Long-Context Agentic Instruction Following
**Source:** arXiv (cs.AI) · Panavas, Minus, Monton, Ray, Garre, Mehta, Chen · [arxiv.org/abs/2607.25398](https://arxiv.org/abs/2607.25398) · posted ~Jul 28, 2026
**Score: 4/5 — sharpens a thesis**

The paper drops LLM agents into a simulated company (files, email, Slack/Jira/calendar-style tools) governed by a 20–124 page corporate handbook, then measures whether the agent actually *follows the standing policy* over long, multi-step tool-use sessions — not just whether it completes the assigned task. Frontier models pass as low as 36.2% of the time: agents routinely complete the task while silently violating a compliance rule buried pages earlier in the handbook. The benchmark isolates a failure mode that task-completion metrics (the ones vendors quote) systematically hide — an agent can look 95% "successful" by task count while quietly breaking your SOPs on a third of runs.

**What it means for The Construct:** Any agent layer we (or a portfolio company) run across back-office systems needs a policy-adherence check independent of task-completion metrics — "did it finish the ticket" is the wrong KPI; "did it also follow the handbook while finishing the ticket" is the one that prevents a compliance surprise in a roll-up with newly-merged SOPs.

---

## 2. Investors Believe in AI—Now They Want Results
**Source:** BCG (Global Investor Survey, 544 investors / ~$35T AUM, 16 countries) · [bcg.com/publications/2026/building-investor-confidence-in-ai-strategy](https://www.bcg.com/publications/2026/building-investor-confidence-in-ai-strategy) · ~Jul 28, 2026 (date corroborated via secondary sources, page itself 403'd on direct fetch)
**Score: 4/5 — sharpens a thesis**

BCG's 2026 investor survey (fielded Mar–Apr 2026) finds institutional investors still believe in AI's economic case — 74% expect productivity gains, 69% expect margin gains — but patience for unproven "AI story" valuations is running out. Return-on-capital rigor as a stated investor priority rose 8 points year-over-year to 33%, and the report frames this as a pivot from "prove you're using AI" to "prove the milestone-based return." Investors are asking for the same discipline on AI capex they'd ask of any other capital allocation.

**What it means for The Construct:** Hartley Capital's pitch to LPs and family offices on AI-agent-driven value creation needs to lead with milestone-based ROI proof points (cost-per-task, time-to-payback, headcount delta), not an "AI-enabled" narrative — the market has already moved past taking that story at face value.

---

## 3. Family offices adjust asset allocation to meet evolving challenges (DACH Family Office Study)
**Source:** Roland Berger · [rolandberger.com/en/Insights/Publications/Family-offices-adjust-asset-allocation-to-meet-evolving-challenges.html](https://www.rolandberger.com/en/Insights/Publications/Family-offices-adjust-asset-allocation-to-meet-evolving-challenges.html) · reported "July 2026," exact day unverified
**Score: 3/5 — useful background**

Survey of 88 DACH-region family offices: 88% now rate geopolitical upheaval as a significant-to-very-significant challenge (up from 65% the prior year), and over half plan to *increase* private equity allocations despite that risk read. AI ranks as a top-3 sector priority (45%) alongside infrastructure and healthcare — family offices are treating AI exposure as a distinct allocation line, not just a portfolio-company feature.

**What it means for The Construct:** Family offices are simultaneously more risk-averse on macro and more willing to lean into PE + AI specifically — that's the exact combination Hartley Capital's roll-up-plus-agent-AI thesis should be underwriting toward when sourcing LP capital; the risk framing should acknowledge geopolitical caution while leading with the PE/AI allocation appetite.

---

## Also scanned, scored below 3 (skip — logged for completeness)

- **McKinsey Global Institute, "The global balance sheet 2026: Imbalance and divergence"** (~Jul 23, outside window) — macro/valuation-froth thesis relevant to hedge fund positioning, but outside the 48h window and not agent/PE-specific enough to score 3+ this cycle.
- **KPMG Global AI Pulse Q2 2026** (~Jun 24) and **KPMG Global Family Office Compensation Benchmark** (~Jun 2026) — both good background on agent-scaling stats and family-office tech adoption, but ~5 weeks stale; hold for a future cycle if no fresher hit displaces them.
- **Bain, "Private Equity Midyear Report 2026: Control the Controllable, Weather the Rest"** (~Jun 8–23) — explicitly calls for agentic AI across PE fund ops; strong thesis fit but 6+ weeks old.
- **arXiv 2607.27155 (OmegaUse-OfficeVal)** and **2607.22445 (Dynamic Capability Scoping for Enterprise AI Agents)** — both solid agent-ops papers (economic grounding of agent labor substitution; least-privilege governance for multi-entity agent access) but bumped by the top 3 on freshness/directness this cycle.
- **KPMG Global Tech Report 2026: Automotive, Deloitte Weekly Global Economic Update** — in-window but too tangential (automotive-specific; generic macro tracker) to score above 2.
- No Theme 1 (Brand 9 / signage / homebuilders / FL real estate) hits scored ≥3 this cycle across any firm — closest tangential items (Deloitte CRE Outlook, PwC/ULI Emerging Trends in Real Estate 2026) were stale annual reports, not fresh publications.

## Confidence caveats

All four firm-group scans hit HTTP 403 on direct WebFetch to primary insight pages; every date above is reconstructed from search snippets rather than a verified page load. Recommend a manual click-through on items 1–3 before quoting exact figures externally.
