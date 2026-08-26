# The Agent ROI Gap Nobody's Pricing In

*WOLF Consulting Pulse — Aug 26, 2026*

McKinsey's newest Global AI Survey buried a number that should be on every board deck about "agentic transformation." Among companies over $1B in revenue, the share scaling AI agents into production jumped from 27% to 40% in a year. The share reporting real EBIT impact from AI? 37% — statistically the same as it was in 2025. Enterprises are deploying agents faster than agents are making them money.

McKinsey's own follow-on data explains why: 93% of enterprises running agentic workflows are blowing through their AI budgets, and 60% of that overspend isn't going to running the agents — it's going to *iterative refinement*, the unglamorous work of getting agent output reliable enough to actually trust with real decisions.

That matches something a new benchmark landed on independently, two days apart, on arXiv. SWE Refactor Bench tested coding agents on whole-repository migrations — real long-horizon work, graded on whether the migration actually completed and didn't break behavior, not just whether the diff looked plausible. Across 520 runs and 8 frontier models, only 5.4% of runs passed cleanly. The best model in the field scored 47 out of 100.

Two data points, two different methodologies, published the same week, telling the same story: the industry is scaling deployment of a capability that isn't yet reliable enough to deploy unsupervised. Most people reading the McKinsey survey will stop at the headline — "40% scaling agents." Almost nobody is reading it next to a hard capability benchmark from the same week and doing the subtraction.

**Why this matters, and why you probably haven't seen it laid out this way:** the McKinsey number is getting covered as an adoption story. The arXiv paper is getting read by maybe a few hundred ML researchers, not board rooms. Nobody with an audience in both worlds is putting them side by side — which is exactly the corner of the universe this brief exists to cover.

**The takeaway:** the money over the next 12-18 months won't concentrate on model providers — it'll concentrate on the refinement layer: supervision, evals, guardrails, human-in-the-loop tooling. That's a services and infrastructure opportunity, not a "buy the model" trade, and it's the kind of durable margin that belongs in a roll-up's operating model, not just its product roadmap.

**If I'm wrong:** by Nov 26, 2026, if McKinsey's next comparable survey (or an equivalent independent measure) shows enterprises reporting EBIT-impact rates meaningfully above 45% while agent-scaling adoption keeps climbing — i.e., the gap actually closes instead of widening — this thesis is dead, and the refinement-layer opportunity is smaller and shorter-lived than argued here.

---
*Sources: McKinsey, "The State of AI in 2026" Global Survey (Aug 25, 2026); arXiv:2608.23564, "SWE Refactor Bench" (Aug 24, 2026). Full sourcing and confidence notes in the internal digest.*
