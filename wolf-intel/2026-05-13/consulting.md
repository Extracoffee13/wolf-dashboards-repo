# WOLF Consulting Pulse — 2026-05-13

**Agent:** WOLF | **Routine:** consulting-pulse | **Coverage window:** May 11–13, 2026

---

## Scan Coverage

| Firm | Status | Papers 24-48h |
|------|--------|---------------|
| McKinsey / MGI | Scanned via search | 1 relevant (May 12) |
| BCG / BHI | Scanned via search | 0 in window |
| Bain | Scanned via search | 0 in window |
| Deloitte | Scanned via search | 0 in window |
| KPMG | Scanned via search | 1 (Q1 Pulse, late April) |
| EY | Scanned via search | 0 in window |
| PwC | Scanned via search | 1 (April 13) |
| Strategy& | Scanned via search | 0 in window |
| Oliver Wyman | Scanned via search | 0 in window |
| Roland Berger | Scanned via search | 0 in window |
| arXiv cs.AI | Scanned | 2 relevant (May 2026) |
| arXiv econ.GN | Scanned | 0 scored ≥3 |
| arXiv q-fin | Scanned | 0 scored ≥3 |

*Note: All firm websites returned HTTP 403 for direct page fetches; coverage sourced through web search index.*

---

## Papers Scored ≥3

---

### Paper 1 — Score: 4/5

**Title:** Authorization Propagation in Multi-Agent AI Systems: Identity Governance as Infrastructure

**Source:** arXiv preprint 2605.05440 (submitted May 2026)

**URL:** https://arxiv.org/abs/2605.05440

**Executive Summary:**
This paper formalizes what it calls the "authorization propagation problem" — the challenge of maintaining correct, bounded permissions as non-human AI principals retrieve data, delegate subtasks, and synthesize results across dynamically changing trust boundaries in a multi-agent system. The author (Prakash, 2026) identifies three distinct sub-problems — transitive delegation (does Agent B inherit Agent A's rights?), aggregation inference (does combining outputs reveal data none of the inputs had permission to expose?), and temporal validity (do permissions granted at task initiation hold across the full execution timeline?). The paper proposes Invocation-Bound Capability Tokens (IBCTs) — a token architecture that fuses identity, attenuated authorization, and provenance binding into an append-only chain, with two wire formats: compact JWT for single-hop and Biscuit tokens with Datalog policies for multi-hop delegation. Benchmarks show 0.049ms verification latency with 100% adversarial rejection across 600 attack attempts. The central normative claim: identity governance is not a compliance wrapper — it is engineering infrastructure that must be evaluated continuously, enforced at every interaction boundary, and designed *before* orchestration logic is allowed to scale. A companion paper (MAGIQ, arXiv 2605.06933) extends this into post-quantum cryptographic guarantees for agentic governance systems.

**What it means for The Construct:**
Hartley Capital's agent AI build-out faces exactly this problem the moment it moves beyond single-agent tasks to orchestrated pipelines (deal flow screening → portfolio monitoring → LP reporting). The paper is the pre-flight checklist: any agentic architecture that doesn't engineer authorization propagation at the wire level is accumulating silent liability — not just regulatory risk, but the failure mode where an agent synthesizes and leaks confidential portfolio company data it was never individually authorized to touch. Build the IBCT token layer before the orchestration layer, not after.

---

### Paper 2 — Score: 4/5

**Title:** Investment and AI Agent Deployment Surge as Execution Becomes the Differentiator

**Source:** KPMG Global AI Quarterly Pulse Survey Q1 2026

**URL:** https://kpmg.com/us/en/media/news/q1-ai-pulse2026.html

**Executive Summary:**
KPMG's Q1 2026 Global AI Pulse (released late April 2026, covering ~1,900 senior executives across 11 countries) documents a structural shift in enterprise AI deployment posture: the differentiation has moved from whether firms are investing in AI to whether they can execute at scale. Key findings: (1) 63% of organizations now require human validation of all AI agent outputs — up from 22% in Q1 2025, a 3x jump that signals widespread loss of confidence in autonomous agent reliability without governance infrastructure. (2) Only 11% of organizations consistently realize measurable AI value — the same 11% who report treating AI as a coordinated enterprise-wide system rather than a collection of pilots. (3) Average projected AI spend over the next 12 months: $207M — nearly double the prior year. (4) Workforce readiness, not technology access, is now the primary constraint cited by lagging organizations. The report frames the 89%/11% split as the defining competitive dynamic of 2026: the gap between orgs that bought AI and orgs that operationalized it is not narrowing; it is widening.

**What it means for The Construct:**
The 63% human-validation rate is Hartley Capital's competitive aperture — most PE-adjacent firms deploying AI agents are effectively deploying expensive automation with a human rubber-stamp on every output, destroying the latency and scale advantages that make agentic AI valuable in the first place. A Hartley operating model that engineers trust-verified, governance-native agents (per paper #1) can operate in the 11% club while competitors are building oversight bureaucracies around unreliable agents. This also sharpens the Brand 9 thesis: any signage or homebuilder client deploying AI for design workflow, permit automation, or contractor coordination is likely in the 89% — a clear upsell surface for structured AI operating model advisory.

---

### Paper 3 — Score: 3/5

**Title:** Three-quarters of AI's economic gains are being captured by just 20% of companies

**Source:** PwC 2026 AI Performance Study (April 13, 2026)

**URL:** https://www.pwc.com/gx/en/news-room/press-releases/2026/pwc-2026-ai-performance-study.html

**Executive Summary:**
PwC's 2026 AI Performance Study (1,217 senior executives, 25 sectors, predominantly large-cap public companies) finds that 74% of AI's measurable economic value is being captured by 20% of organizations — and that the leading organizations are distinguished not by technology access but by strategic intent: they are using AI to drive revenue growth and business model reinvention rather than cost reduction. The top-performing AI companies deliver financial outcomes 7.2x higher than the median. The study introduces the concept of "AI fitness" — a composite of technology adoption, data infrastructure, governance maturity, and workforce capability — and finds that most organizations are optimizing only one or two of these dimensions while neglecting the others. Chief Data and Analytics Officers are under mounting pressure as the ROI window narrows: the window for catching the 20% is closing, but the remaining 80% are not standing still.

**What it means for The Construct:**
Useful background calibration for Hartley Capital's fund thesis — the 7.2x performance multiplier is a compellingly defensible number for LP conversations about why AI-native portfolio operations are an alpha source, not just a cost line. Less operationally urgent than Papers 1 and 2.

---

## Below Threshold

| Title | Firm | Score | Reason Skipped |
|-------|------|-------|----------------|
| McKinsey MGI — Skills in the AI Age (May 12, 2026) | McKinsey | 2 | Workforce/reskilling focus; no direct signage, RE, or PE/fund angle |
| Bain Global PE Report 2026 (Feb 2026) | Bain | 2 | Outside 48h window; already in prior briefings |
| BCG Inside the AI-First PE Firm (Jan 2026) | BCG | 2 | Outside window; well-covered territory |
| Deloitte Private Survey — AI Shift (Apr 28, 2026) | Deloitte | 2 | Directionally consistent but no new thesis |

---

## Scan Metadata

- **Firms scanned:** 10 strategy firms + MGI + BHI
- **arXiv categories:** cs.AI, cs.MA, econ.GN, q-fin
- **Fetch method:** Web search index (direct site fetches returned 403)
- **Confidence in coverage:** 0.65 (search index may lag 12-24h on some publications)
