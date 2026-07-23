# WOLF Consulting Pulse — 2026-07-23

Daily synthesis of strategy-firm white papers and research, filtered for relevance to The Construct's two engines (Brand 9 / signage / homebuilders / FL real estate; Hartley Capital / PE roll-ups / agent AI / hedge fund ops / family office). Scan window: last 24–48h across McKinsey, MGI, BCG + BCG Henderson Institute, Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, Roland Berger, and arXiv (cs.AI / econ.GN / q-fin).

## Scan notes

Firm-by-firm, what actually published fresh vs. what's just evergreen 2026-annual-report noise still ranking in search:

- **McKinsey / MGI** — nothing dated in-window with Construct relevance. Live threads: AI scaling survey (Jul 13), entry-level work/knowledge management (Jul 14), both slightly stale. Global Private Markets Report 2026 and State of Organizations 2026 are the big annual anchors but predate the window.
- **BCG / BCG Henderson Institute** — most active shop this cycle. In-window: "Citizens Are Open to Public AI Services" (Jul 21, public-sector, low relevance), "Advancing Africa's AI and Digital Economy" (Jul 22, low relevance), "Are Insurers' Talent Models Ready for AI?" (Jul 22, **selected**), "Scaling Agentic AI in Procurement Is an Organizational Challenge" (Jul 21, topically strong but I could not pin a stable canonical URL distinct from BCG's June supply-chain piece — flagged, not selected to avoid miscitation). "Return on AI: Token Meter" token-cost series is excellent and squarely on-thesis for Hartley Capital agent-ops economics but publishes ~Jul 16 — outside the 48h window, worth a follow-up scan next cycle.
- **Bain** — Global Insurance Report 2026 (Jul 20) and grocery slowdown analysis (Jul 16) both real but outside Construct relevance/window overlap.
- **Deloitte** — "AI agents scaling faster than their guardrails" is a strong thesis line but traces back to the State of AI in the Enterprise report from April 2026; no fresh in-window Deloitte piece found.
- **KPMG** — Q2 2026 AI Pulse (asset management / PE) is directly on-thesis (only 26% of AM/PE firms have real-time cost visibility into running AI at scale) but the survey window closed May 25 and it published in June — stale for this cycle.
- **EY** — Family office AI adoption data (56% say AI has no impact yet on investment process) is useful background, no fresh in-window publication.
- **PwC / Strategy&** — 2026 AI Predictions and multi-agent orchestration pieces are evergreen framework content, nothing dated fresh this cycle.
- **Oliver Wyman** — CEO Agenda 2026 (M&A-heavy) and PE Perspectives hub, nothing dated fresh this cycle.
- **Roland Berger** — Family Office Study ("New asset allocation in challenging times") is fresh (picked up/syndicated Jul 21 via Advisor Perspectives) and squarely hits the Hartley Capital / family office engine. **Selected.**
- **arXiv** — "Organizational Memory for Agentic Business Process Execution" (2607.03228) is a July 2026 submission that reframes the exact problem Hartley Capital will hit scaling agents across a roll-up portfolio: per-entity prompt/retrieval setups don't scale, you need a shared governed memory layer. **Selected**, highest score of the three.

---

## 1. Organizational Memory for Agentic Business Process Execution

**Source:** arXiv (cs.AI/cs.MA), July 2026 — https://arxiv.org/abs/2607.03228

**Executive summary:** The paper argues that general-purpose LLM agents lack the organization-specific procedural knowledge needed for reliable business-process execution — that knowledge lives fragmented across policies, process models, and SOPs, and today's fix (stuffing it into per-agent prompts or bespoke retrieval setups) doesn't scale: it produces knowledge silos, duplicated rules, and no consistent path to update or learn across agents. The authors derive requirements for an "organizational memory" — a shared, governed, agent-consumable reference layer of evolving procedural knowledge — propose a curation/consumption architecture for it, and validate it with a procurement proof-of-concept.

**What it means for The Construct:** This is the paper that names Hartley Capital's actual integration bottleneck before we hit it — every roll-up acquisition currently means re-teaching agents that portfolio company's SOPs from scratch, and without a shared memory layer that cost compounds linearly with every add-on instead of amortizing. Worth prototyping a lightweight version of this (one governed knowledge layer, portfolio-company-specific overlays) before the next roll-up close rather than after.

**Score: 5** — changes a thesis we hold (that agent deployment cost per portfolio company is roughly fixed; it isn't, without shared memory infrastructure it's linear and compounding).

---

## 2. Family Office Study: New Asset Allocation in Challenging Times

**Source:** Roland Berger — https://www.rolandberger.com/en/Insights/Publications/Family-offices-adjust-asset-allocation-to-meet-evolving-challenges.html (syndicated Jul 21, 2026 via Advisor Perspectives)

**Executive summary:** Survey of 88 family offices (DACH region) finds geopolitical upheaval has overtaken interest-rate uncertainty as the dominant external risk — 88% now call it "significant" or "very significant," up from 65% a year ago. In response, allocations are shifting toward private equity (funds and direct deals show the strongest growth momentum) and defensive hard assets like precious metals, while venture capital and crypto/digital assets are being trimmed. Infrastructure is the top sector priority, followed by healthcare and AI, the fastest-gaining sector theme. Most respondents invest internationally but stay concentrated in stable developed markets (North America, Northern Europe).

**What it means for The Construct:** family offices are actively rotating toward direct PE and away from venture/crypto, with AI as the fastest-rising sector interest — that's the exact investor profile Hartley Capital should be courting for its next roll-up raise, and the pitch should lean on "direct, defensive, AI-adjacent" framing rather than growth-multiple language.

**Score: 4** — sharpens a thesis (capital-raise targeting and framing for Hartley Capital's next roll-up vehicle).

---

## 3. Are Insurers' Talent Models Ready for AI?

**Source:** BCG — https://www.bcg.com/publications/2026/why-ai-demands-a-new-insurance-talent-model (published ~Jul 22, 2026)

**Executive summary:** BCG argues that as insurers mature past AI deployment into AI-powered work, the binding constraint shifts from technology to talent — future competitive advantage comes from redesigning who's accountable for what, how expertise is built and verified, and where human judgment sits in an AI-mediated workflow, not from further model deployment.

**What it means for The Construct:** the talent/accountability redesign problem BCG describes for insurers is identical to what Brand 9 and any Hartley Capital portfolio company will face once agents handle first-line quoting, scheduling, or install-coordination work — the org chart and accountability lines need to be redrawn before the agent rollout, not after, or you get shadow-workarounds instead of adoption.

**Score: 3** — useful background pattern, transferable but not sector-specific enough to sharpen a Construct thesis directly.

---

## Sources consulted (not selected)

- McKinsey — AI scaling survey (Jul 13), entry-level work/knowledge management (Jul 14), Global Private Markets Report 2026, State of Organizations 2026
- BCG — "Citizens Are Open to Public AI Services" (Jul 21), "Advancing Africa's AI and Digital Economy" (Jul 22), "Return on AI: Token Meter" series (~Jul 16)
- Bain — Global Insurance Report 2026 (Jul 20), US grocery slowdown analysis (Jul 16), Global Private Equity Report 2026, M&A Report 2026
- Deloitte — State of AI in the Enterprise 2026 / "AI agents scaling faster than their guardrails" (April 2026)
- KPMG — Q2 2026 AI Pulse, asset management/PE pulse (survey closed May 25, published June)
- EY — Family office AI adoption data, Technology Pulse Poll
- PwC / Strategy& — 2026 AI Business Predictions, multi-agent orchestration framework pieces
- Oliver Wyman — CEO Agenda 2026, PE Perspectives hub, wealth/asset management trends 2026
- Roland Berger — European Private Equity Outlook 2026, Construction Radar 2026
