# First-Principles Spike — 2026-06-24

## Question

**What are the irreducible primitives that make a sign effective — derived from physics, cognition, and economics rather than industry convention?**

*Generated from context: Brand 9 Signs operations, signage industry primitives.*

---

## Step 1 — First-Principles Answer (no retrieval)

### Starting primitives

1. A sign is an artifact that encodes information into a perceptual medium (light, shape, symbol, text).
2. Human attention is a finite, selective resource — the true scarce input the sign must compete for.
3. Sign effectiveness = the probability that a desired viewer behavior occurs as a result of sign exposure.

### Layer 1 — Perception (necessary condition): Signal-to-Noise Ratio

A sign must first be distinguishable from its background. This is a pure physics problem: contrast in luminance, chrominance, shape, or motion. A sign indistinguishable from its surround is, by definition, not a sign — it has merged back into environment texture. No amount of message quality recovers this failure. Contrast is therefore not a design preference; it is the boundary condition for the sign's existence.

**Derived rule:** Any sign budget spent on message content before solving contrast is wasted.

### Layer 2 — Preattentive Capture (~100–200ms): Biological Override

Human visual processing has two stages. Stage 1 (preattentive) runs before conscious awareness, scanning for threat/reward signals using crude heuristics: saturated warm color, motion, angular shapes, faces, abrupt luminance discontinuities. This stage operates at ~10ms per feature in parallel across the visual field. If a sign passes this gate, the brain routes conscious attention to it. If it fails, the sign is processed as background and discarded.

This gate cannot be bypassed by good typography or clever copy. It operates on physical signal properties only.

**Derived rule:** A sign must win Stage 1 through physical properties (color, motion, contrast) before any cognitive content matters.

### Layer 3 — Decode Speed: The Physics Constraint

A vehicle at 35 mph covers 51 feet per second. Roadside signs are useful across roughly a 150-foot viewing arc → ~3 seconds of processing time. At typical adult reading speed of ~250 words/minute ≈ 4.2 words/second, and accounting for scanning overhead (the sign isn't presented left-to-right in a known rhythm like a page), effective decode throughput drops to roughly 2–3 word-equivalents per second.

Practical ceiling: **5–7 words or equivalent visual units** within a mobile-viewer context. This figure isn't an aesthetic convention — it is derivable from: viewer velocity + viewing arc + cognitive decode rate.

For pedestrian contexts (slower velocity, longer dwell), the ceiling rises, but the multiplicative structure stays the same.

**Derived rule:** Message complexity is bounded by viewer velocity. Violating this bound doesn't produce a partially-effective sign — it produces a zero-effective sign, because the viewer exits the window before decode completes.

### Layer 4 — Relevance: The Economic Filter

Even a fully decoded sign does nothing unless its message connects to an active or dormant need in the viewer. The brain performs rapid relevance classification on decoded content and discards non-matches within ~300ms. A sign advertising "TIRE REPAIR" to a driver with a slow leak activates an urgent need; the same sign to a driver with new tires is nearly invisible to behavior, despite being seen and decoded.

Relevance cannot be manufactured from sign content alone; it must meet a pre-existing state in the viewer. However, placement can dramatically increase the base rate of relevant viewers (tire shop near a highway on-ramp sees more distressed drivers than a tire shop in a residential neighborhood). This is why **location is the dominant variable in sign effectiveness** — it controls the relevance prior across the viewer population.

### Synthesis — The Multiplicative Model

```
Effectiveness = Contrast × Preattentive Salience × Decode Completion × Relevance
```

These four factors are **multiplicative, not additive.** A zero in any single term drives total effectiveness to zero regardless of performance on the other three. This is the structural insight that industry checklists miss: they present these as a menu of features, implying partial credit. The multiplicative model says there is no partial credit — a highly relevant, well-designed sign in the wrong location (zero relevant viewers) is worthless.

### Corollaries

- **Location > Design.** Location controls the Relevance prior across viewer population. A brilliant sign in the wrong location fails. A mediocre sign in the right location succeeds.
- **Simplicity is physics, not aesthetics.** The word-count ceiling is a derived constraint from viewer velocity and cognitive throughput, not a stylistic preference.
- **Contrast before content.** Solving visibility is a prerequisite, not a co-equal design dimension.
- **Emotion amplifies retention but doesn't substitute for relevance.** Humor, surprise, and aspiration improve memory encoding and second-exposure effects, but only after a relevance trigger fires.

---

## Step 2 — Corpus Answer (retrieved from standard knowledge)

The signage industry and advertising research literature converges on several frameworks:

**Sign Research Foundation / OAAA:** Effective signage criteria include: legibility (letter size, font, contrast), visibility (placement, lighting, obstructions), message brevity (5-7 words for vehicular audiences), color contrast (rule of thumb: 70% contrast ratio), and location/zoning compliance.

**Outdoor advertising research (Bhargava & Donthu, various):** Empirical studies confirm message brevity and contrast as primary drivers of recall. Location (traffic count × demographic match) is identified as the dominant economic variable in OOH (out-of-home) advertising ROI.

**Behavioral economics lens (Kahneman / System 1-2):** System 1 (fast, automatic) governs most sign perception. Effective signs operate on System 1 triggers: simplicity, familiarity, visual salience. System 2 engagement (reading complex copy) requires voluntary dwell time, which mobile viewers rarely provide.

**Industry heuristics (USSC Sign Standards, ISA guidelines):** Letter height formulas for viewing distances, contrast requirements, word-count maximums — all presented as empirically-derived rules rather than derived from first principles.

---

## Step 3 — Delta Analysis

**Category: REDISCOVERED**

The first-principles derivation independently arrived at the same practical outputs the corpus presents (5-7 words, contrast primacy, location dominance, System 1/preattentive processing). The conclusions are not novel.

However, the **framing is structurally different:**

| Dimension | Corpus Framing | First-Principles Framing |
|-----------|---------------|--------------------------|
| Structure | Additive checklist (feature menu) | Multiplicative model (any zero = total failure) |
| Word count | Empirical rule-of-thumb | Derived from velocity × cognitive throughput |
| Contrast | Design preference / aesthetic | Boundary condition for sign's existence |
| Location | Important factor | Dominant variable controlling the Relevance prior |
| Simplicity | "Best practice" | Hard physical constraint |

The multiplicative vs. additive framing is the most operationally significant difference. A practitioner using a checklist allocates improvement budget across all factors proportionally. The multiplicative model says: **identify the zeroed or near-zero factor first and fix that; all other improvements are wasted until that's solved.**

This reorders the diagnostic workflow for Brand 9 Signs client consultations:
1. Is the sign visible at all? (Contrast check)
2. Does it pass preattentive capture? (Color/motion/size)
3. Can it be decoded within the viewer's window? (Velocity-adjusted word count)
4. Is it placed where relevant viewers exist? (Location as Relevance prior)

Only after all four pass zero-check does refinement within each factor matter.

---

## Commentary

The spike validates the reasoning chain but surfaces a productive reframe: the industry operates with an additive mental model, which misallocates improvement effort. The multiplicative model is a better diagnostic tool for client work.

For agent architecture: the same multiplicative structure likely applies to agent effectiveness (an agent that can't perceive the right context = zero, regardless of reasoning quality). Worth a follow-up spike.

**Confidence in first-principles derivation:** 0.82  
**Confidence in delta category (rediscovered):** 0.78
