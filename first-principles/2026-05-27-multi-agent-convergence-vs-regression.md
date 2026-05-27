# Spike: Multi-Agent Convergence vs. Regression

**Date:** 2026-05-27  
**Question:** What determines whether a multi-agent AI system converges to better decisions than its best individual agent, or regresses to the mean?  
**Relevance:** WOLF Committee architecture (Generalist, Quant, Skeptic, Operator) — directly governs whether the four-role panel is net-additive or noise.

---

## Step 2 — First-Principles Derivation

### Primitive 1: Information theory — independence is load-bearing

The only mechanism by which averaging agents improves over the best single agent is variance reduction through independent errors. If n agents each have error probability p and their errors are independent, ensemble error falls toward zero as n grows. But if errors are correlated — same training corpus, same world model, same prompting pattern — the committee amplifies the shared failure rather than canceling it. A committee of three identical agents is still one agent wearing three hats.

**Implication:** Diversity of error distribution, not diversity of persona label, is the actual variable.

### Primitive 2: Specialization must be genuine

A committee outperforms its best member only when each marginal agent introduces information the best agent genuinely lacks. This requires:

1. Different epistemic lenses (a quant reading correlations vs. an operator reading execution friction)
2. A mechanism that surfaces the specialist's signal rather than washing it out
3. Some weighting function that reflects track record — equal-weight voting assumes equal competence, which is almost never true

If the "Quant" and "Generalist" arrive at conclusions through the same chain of reasoning on the same data, their nominal difference is cosmetic. They are not adding independent signal; they are confirming each other.

### Primitive 3: Aggregation mechanism determines whether minority signal survives

How votes combine determines outcome:

- **Simple majority vote** — cancels random noise but also cancels contrarian insight. One correct dissenter gets outvoted by two wrong agreers.
- **Weighted by past accuracy** — theoretically optimal, but requires enough history to estimate weights, and conditions shift.
- **Adversarial critique (Skeptic role)** — explicitly surfaces failure modes of the consensus view. This is asymmetric in expected value: if the Skeptic is wrong when consensus is right, the cost is a slight delay. If consensus is wrong and the Skeptic is right, the cost avoided is catastrophic correlated error. The Skeptic's role therefore has higher expected marginal value than adding another agreeing agent.

**Implication:** The WOLF Committee's explicit Skeptic role is structurally the highest-value seat.

### Primitive 4: Deliberation sequence determines whether anchoring corrupts independence

Two extreme protocols:

- **Poll then aggregate** — each agent forms a view before seeing others. Independence preserved. But no learning from peers.
- **Observe then respond** — each agent sees prior agents' outputs before forming its own view. Anchoring effect corrupts independence; the second and third agents are partially reasoning from the first agent's conclusion.

The optimum: **(1) independent formation → (2) structured reveal → (3) adversarial challenge → (4) final vote with named reasoning.** Named reasoning matters because it forces agents to commit to a falsifiable chain, making errors findable rather than hidden in averaged numbers.

### Synthesized First-Principles Answer

**A multi-agent system beats its best individual agent when:**
1. Agents have genuinely independent error distributions (different training, lenses, failure modes — not just different persona names)
2. The aggregation mechanism preserves rather than washes out specialist minority positions
3. At least one adversarial role is structurally protected from being outvoted
4. Deliberation proceeds independent-first, so early agents don't anchor later ones

**It regresses to the mean (or worse) when:**
- Agents share training data and world models → correlated errors, no variance reduction
- Simple majority vote destroys contrarian signal
- Agents see each other's outputs before forming independent views → anchoring
- No track-record weighting → wrong specialist equals right generalist

---

## Step 3 — Corpus Answer

**Source 1: "Representational Collapse in Multi-Agent LLM Committees" (arXiv 2604.03809)**  
Across 100 GSM8K questions with three Qwen2.5-14B agents, mean cosine similarity of hidden representations is 0.888, effective rank 2.17 out of a theoretical 3.0. The paper names this failure mode *representational collapse* and finds it worsens on harder tasks. Diversity-Aware LLM Committee (DALC) protocol achieves 87% on GSM8K vs. 84% for self-consistency by explicitly weighting diverse representations.

**Source 2: "Multi-Agent Teams Hold Experts Back" (arXiv 2602.01011)**  
Teams engage in *integrative compromise* — averaging expert and non-expert views — rather than appropriately weighting superior knowledge. Compromise correlates negatively with performance and worsens with team size.

**Source 3: "Diversity Empowers Intelligence" (arXiv 2408.07060)**  
Groups with average resolve rate 26.6% collectively solve 54.3% of issues with an oracle reviewer. DEI-guided committee surpasses best individual agent (34.3% vs. 27.3% resolve rate for SWE-bench).

**Summary of orthodox view:**  
The corpus confirms that (a) correlated errors are the primary failure mode, (b) diversity of representation — not just persona — is the necessary condition for outperformance, (c) equal-weight aggregation (integrative compromise) is a known failure mode that worsens with team size, and (d) diversity-aware consensus protocols measurably rescue performance.

---

## Step 4 — Delta Analysis

**Category: rediscovered**

My first-principles derivation arrived at the same core claims as the corpus:
- Correlated errors are load-bearing (✓ confirmed by cosine similarity 0.888 result)
- Genuine diversity of representation required, not just persona labels (✓ confirmed by DEI-guided committee work)
- Equal-weight aggregation / integrative compromise is a failure mode (✓ named and confirmed)
- Adversarial structure preserves minority signal (✓ implicit in DALC's diversity weighting)

**What the corpus adds that I missed:**
- *Representational collapse* as a named, measurable phenomenon with a specific metric (cosine similarity of hidden states)
- The observation that collapse *worsens on harder tasks* — I predicted correlated errors are bad but didn't derive the task-difficulty intensification. In hindsight: harder tasks have narrower solution paths, so same-model agents converge even more on the same wrong reasoning chain. That's derivable but I didn't push the chain far enough.
- A named algorithm (DALC) with a specific diversity-weighting mechanism

**What first-principles got right that the corpus mostly glosses over:**
- The deliberation sequence (independent formation → reveal → adversarial → final vote) as a structural design requirement. The corpus focuses on representation diversity but underspecifies *when* agents should see each other's outputs.
- The asymmetric expected value of the Skeptic role — the corpus notes adversarial diversity is helpful but doesn't quantify why one adversarial agent is worth more than an additional agreeing specialist.

---

## Commentary

This spike validates the WOLF Committee's four-role structure. Generalist + Quant + Skeptic + Operator is not arbitrary — it maps cleanly onto the diversity-of-lens requirement. The structural risk is prompt-level anchoring: if WOLF's orchestration layer shows each agent the prior agent's output before asking for its own view, the committee collapses toward the first responder's framing regardless of role labels.

**Concrete recommendation:** In WOLF's committee deliberation protocol, require independent blind formation for each role before any role sees another's output. Reveal and challenge only in the adversarial phase.

The "harder tasks worsen collapse" finding is the most operationally valuable corpus addition: in high-volatility or high-ambiguity market conditions (precisely when the committee is most needed), same-model agents will converge the most. This is when an independent Skeptic with a genuinely different reasoning path matters most — and when the committee is most likely to have failed silently if no structural safeguard exists.
