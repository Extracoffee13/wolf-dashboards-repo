# WOLF Consulting Pulse — 2026-07-02

Daily synthesis of strategy-firm white papers and research, filtered for relevance to The Construct's two engines: Brand 9 (signage / homebuilders / FL real estate / wayfinding) and Hartley Capital (PE roll-ups / agent AI / hedge fund ops / family office).

**Scanned:** McKinsey Insights + MGI, BCG Publications + BCG Henderson Institute, Bain Insights, Deloitte Insights, KPMG Insights, EY Insights, PwC Research & Insights, Strategy&, Oliver Wyman, Roland Berger, plus arXiv cs.AI / econ.GN / q-fin (week of June 29–July 2, 2026). Window: last 24–48 hours.

## Coverage note

Genuinely fresh strategy-firm output in the strict 24–48h window was thin — most flagship "Insights" content from Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver Wyman, and Roland Berger publishes in bursts (quarterly/midyear/annual), and nothing dated inside the window cleared the relevance bar. The signal today came from two places: a BCG "Return on AI" pair published July 1, and arXiv's cs.AI/q-fin output this week, which was unusually strong and directly on-thesis. No signage, homebuilder, wayfinding, or Florida-specific content surfaced anywhere this cycle — flagging the gap rather than padding it.

---

## 1. "AI Premium"

**Source:** arXiv (q-fin) — Nicola Borri (LUISS), Yukun Liu (Rochester/Simon), Aleh Tsyvinski (Yale/NBER)
**URL:** https://arxiv.org/abs/2606.30583

Using a proprietary OpenRouter dataset covering 380 trillion tokens of realized AI consumption across 400+ LLMs (~2% of global monthly AI token volume), the authors construct an "AI Factor" from token/dollar/user growth and estimate firm-level "AI Betas" from stock-return comovement with that factor. They document a large, heterogeneous "AI Premium" across firms with different AI exposure, and show a value-weighted long-short strategy on AI-beta earns 64.1 bps/week — a persistent, tradeable factor built from real usage data rather than sentiment or narrative proxies.

**What it means for The Construct:** This is a concrete, backtestable alpha factor built on the exact kind of usage-based data WOLF's Committee should be tracking — it argues AI exposure is already a priced, tradeable factor, not just a story, and it's a direct candidate for the Quant seat's screening universe.

**Score: 4** — sharpens a thesis we hold (AI exposure is investable alpha, not just a valuation multiple).

---

## 2. "Return on AI: What CEOs Need to Know About the True Cost of Artificial Intelligence" (+ companion CFO/CIO piece)

**Firm:** BCG
**URL:** https://www.bcg.com/publications/2026/how-ceos-can-optimize-ai-token-costs (companion: bcg.com/ja-jp/publications/2026/managing-ai-token-costs)
**Published:** July 1, 2026

As AI platforms shift to metered, token-based pricing, BCG argues the AI bill is becoming unpredictable and hard to trace to value — hitting capex, opex, and COGS simultaneously. BCG introduces "Return on Intelligence" (RoAI), a metric dividing output value by combined labor + token cost, and lays out five governance levers (starting with "stop or minimize spend") for CEOs, with a companion piece detailing how CFOs/CIOs build workflow-level cost attribution as consumption-based AI billing becomes the norm.

**What it means for The Construct:** Any Hartley Capital roll-up deploying agentic AI across portfolio companies needs a RoAI-style governance layer before scale, not after — this is a template worth stealing directly rather than reinventing, and it validates that token-cost discipline is now a board-level line item, not an engineering afterthought.

**Score: 4** — sharpens the agent-ops-at-scale thesis with a ready-made governance framework.

---

## 3. "Are We Ready for An Agent-Native Memory System?"

**Source:** arXiv (cs.AI) — Wei Zhou et al., Shanghai Jiao Tong University
**URL:** https://arxiv.org/abs/2606.24775

A systematic evaluation of 12 agent-memory architectures plus 2 baselines across 5 benchmark workloads and 11 datasets, decomposing agent memory into representation/storage, extraction, retrieval/routing, and maintenance modules. The core finding: no single memory architecture dominates — effectiveness depends on matching memory structure to the actual bottleneck in a given workload, not just optimizing for end-to-end task success. The paper generated real practitioner buzz this week (HuggingPapers, Pascal Biese's LinkedIn roundup).

**What it means for The Construct:** As WOLF and sibling agents accumulate longer operating histories, "which memory architecture" becomes a real engineering decision rather than a default — this paper is a useful checklist for auditing whether The Construct's own agent memory setup is matched to its actual bottleneck (likely retrieval/routing, not storage).

**Score: 3** — useful background for agent-ops infrastructure decisions, not thesis-moving on its own.

---

## Also scanned, did not clear the bar

- **Bain, "M&A Midyear Outlook 2026: A Winner's Paradox"** (June 29) — global M&A value +41% YoY, megadeal surge; frames a "winner's paradox" where acquirers must fund both M&A and AI transformation simultaneously. Thesis B-adjacent, useful macro color, but 3+ days outside the window and more descriptive than actionable.
- **KPMG, "Q1'26 Pulse of Private Equity"** (April) — roll-up integration standards (cybersecurity, finance) — directly on-thesis but stale.
- **arXiv econ.GN, "The Economic Benefits and Costs of AI and Policies to Mitigate AI's Impact on Inequality"** (Jackson & Kanik, Stanford) — rigorous wage/labor-reallocation model under AI automation; relevant to underwriting workforce assumptions in agentic roll-ups, but more policy-framing than operational.
- **PwC/Strategy&, "Global M&A trends in industrials and services: 2026 mid-year outlook"** — industrials/services M&A values +9% even as volume falls, buyers chasing "physical AI" assets. Imprecisely dated, background only.
- **Roland Berger, "Understanding the new consumer playbook for 2026"** — 70% of 18-64 year-olds now use AI regularly for product research. Marginal Thesis A relevance, not sector-specific.
- No McKinsey/MGI or BCG Henderson Institute content cleared the relevance bar this cycle; McKinsey's "Week in Charts" (US competitiveness) was macro/geopolitical only.
