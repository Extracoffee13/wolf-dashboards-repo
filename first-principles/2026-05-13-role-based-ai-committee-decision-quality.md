# First-Principles Spike — 2026-05-13

## Question

Does role-based deliberation in a multi-agent AI committee (e.g., Generalist / Quant / Skeptic / Operator) produce genuine decision quality improvement, or does it simulate diversity while reusing the same underlying model weights?

*Relevant to WOLF Brief's four-role Committee architecture and The Construct's agent ecosystem design.*

---

## Step 2 — First-Principles Derivation

### Primitives

1. A decision is a probability-weighted choice among alternatives. Quality = how accurately the weights reflect actual outcome probabilities.
2. Bad decisions arise from: (a) distributional bias — systematic mispricing of outcome classes baked into the reasoner's priors; (b) path-dependent anchoring — the first-generated hypothesis conditions all subsequent reasoning; (c) framing effects — which features are made salient by the question's presentation; (d) coverage failure — whole classes of considerations are never generated.
3. A large language model generates a response by sampling an autoregressive trajectory through a high-dimensional latent space. The trajectory is highly sensitive to its initial activation pattern.

### Chain of Reasoning

**Same weights = same distributional biases.**
If all roles run on identical model weights, the systematic errors embedded in the training distribution are present in every role. A Skeptic role cannot question a fact the model systematically overweights if that overweighting is in the weights themselves — not in the prompt.

**Different role prompts = different initial activation patterns.**
Even on the same weights, a role prompt that biases toward critique ("find what's wrong") fires measurably different activations at token 0 than a role prompt biased toward synthesis. In autoregressive generation, early divergence in the trajectory accumulates — the Skeptic's generation path forks away from the Generalist's early enough to explore different regions of the hypothesis space.

**Therefore: role separation corrects path-dependent errors, not distributional errors.**
- *Corrected by role separation:* anchoring on the first-generated thesis, confirmation bias within a local context window, framing effects from how the prompt was phrased.
- *Not corrected:* base-rate neglect baked into training, systematic underweighting of tail events the model rarely saw labeled, cultural biases in training data.

**Structural antagonism is a real mechanism.**
Forcing a Skeptic role into existence means the model must generate critique — even when its default posture would be cooperative. This isn't theatrical: it changes which activations are reinforced during the generation, which changes the output. A single-model single-prompt run will under-generate critique because critique requires explicitly questioning the model's own prior output.

**The improvement is real but bounded.**
The useful metaphor: not "many minds deliberating" but "one mind forced to take multiple runs from different starting positions." Multiple starting positions = better coverage of the hypothesis space. But all runs share the same blind spots — the terrain itself has the same valleys regardless of where you start.

**For a trading committee specifically:**
- Role separation adds value for: surfacing bear cases the bullish default framing skips, stress-testing a position before committing, catching internal contradictions.
- Role separation adds little value for: correcting for recency bias in the training data, handling genuinely out-of-distribution macro regimes, assessing risks in asset classes under-represented in training.

### Prediction Going into Corpus Search

The literature will confirm: (a) role-prompted multi-agent generates more diverse outputs than single-prompt; (b) improvement is real for locally-induced biases; (c) shared weights mean shared blind spots role separation cannot fix. Delta likely **rediscovered**. Expect the corpus to add a nuance I haven't derived — possibly about how alignment training (RLHF) interacts with role flexibility.

---

## Step 3 — Corpus Answer

**MAR (Multi-Agent Reflexion, 2024/2025)** explicitly separates acting, diagnosing, critiquing, and aggregating across persona-distinct agents. Its framing: single-agent self-critique repeatedly reinforces the same mistakes; separating roles reduces this. Matched mechanism.

**"12 Angry AI Agents" (arxiv 2605.01986)** evaluates jury-style multi-agent deliberation; finds structured deliberation improves quality but convergence dynamics depend heavily on role assignment and turn order.

**CHI 2026 — "Can AI Deliberate?"** finds deliberative quality emerges when *structure and conviction converge*; analytic reasoning style provides a scaffold that stabilizes deliberation even with the same base model.

**SuperAnnotate multi-agent survey (2026)** and **MAR paper** both note: even when agents are prompted with different personas, their underlying reasoning strategies often remain uniform — consistent with my weights = shared biases argument.

**Key additive finding from corpus:** The intensity of RLHF alignment training — not raw model capability — is the primary determinant of deliberative flexibility in multi-agent settings. A heavily RLHF-tuned model is *less* flexible in adopting genuine critique roles because the alignment training has overwritten the adversarial activation patterns. I did not derive this from first principles.

**"Team of Rivals" paper (arxiv 2601.14351):** explicitly recommends orchestrating structured adversarial roles for organizational intelligence — convergent with my structural antagonism mechanism but framed institutionally rather than informationally.

---

## Step 4 — Delta

**Category: `rediscovered`**

The core mechanism — role separation corrects path-dependent biases but not distributional biases; the improvement is "multiple starting positions on one mind" not "many minds" — is confirmed by the corpus. I arrived at it independently before searching.

**One additive corpus finding:** RLHF alignment intensity suppresses genuine adversarial role adoption. Heavily aligned models are less able to take Skeptic positions authentically because the alignment training has attenuated the adversarial activation pathways. This is a real constraint on the WOLF Committee architecture that I did not derive: *the same alignment that makes the model safe makes it a worse Skeptic*.

**Practical implication for WOLF/Construct:** The Skeptic role in the committee should receive an explicit adversarial system prompt that overrides cooperative defaults — not just a label, but a structurally antagonistic instruction set. Otherwise RLHF alignment will cause the Skeptic to hedge toward the Generalist's view.

---

## Commentary

The "many minds" framing is actively misleading for same-model role committees. The better frame — "multiple starting positions on one generator" — makes the limits and the genuine value both immediately legible. Roles are worth doing; they just fix a different class of errors than most practitioners expect them to fix. Design the role prompts to aggressively counteract anchoring (where they work), not to compensate for training data gaps (where they don't).
