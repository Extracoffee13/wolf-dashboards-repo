# First-Principles Spike — 2026-08-12

## Question

Why does monument-sign letter height scale roughly linearly with approach speed, and what's the actual constant (ft of viewing distance per inch of letter height)?

*(Source: generated for today's spike — the backlog file didn't exist yet, so this run seeded `first-principles-backlog.md` with five candidate questions relevant to Construct work and picked this one, since it's a direct signage-industry primitive for Brand 9 Signs.)*

## First-Principles Answer (derived before any lookup)

Reading a monument sign while driving is a full sensory-motor pipeline with a time budget, not a static optics problem. A driver approaching at speed `v` must: (1) detect the sign exists, (2) fixate and resolve the letterforms into a recognized word, (3) decide whether it's their destination, (4) execute a maneuver (decelerate/turn) if so. The physical constraint is that the sign must still be *legible* — individual letters resolvable into a word — at the moment the driver's remaining distance equals what that whole pipeline needs.

**Time budget.** Detection/orientation (~0.5–1s) + reading/comprehension of an unfamiliar 1–3 word proper noun under divided attention (~1–2s of *usable* legible glance-time, not a single clean fixation) + decision (~0.5–1s) + reaction latency before the physically separate braking/turning phase begins (~1–1.5s). Central estimate: T ≈ 4 seconds of required legibility, before deceleration distance is even added on top.

**Distance requirement.** D = v × T. This is the range at which the sign must already be legible, not merely visible (a large high-contrast rectangle is *detectable* from much farther away than its text is *readable*).

**Optics of legibility.** A letter of height h subtends angle θ = h / L at the eye (small-angle approx), where L is viewing distance. Human foveal acuity resolves detail to ~1 arcminute under ideal, static, high-contrast, pre-known-target conditions (that's the literal Snellen chart construction). But sign-reading in a moving vehicle stacks several degradations on top of clinical acuity: vehicle vibration/motion, divided attention with the primary driving task, no priming (a business name is not a small forced-choice optotype set — full open-set letter recognition is required), and only fractional-second glances since eyes must return to the road. Reasoning from how much each of these should degrade effective resolution, I expected the real threshold to land roughly 5–15x worse than clinical acuity — i.e., somewhere in a 5–15 arcminute range for whole-letter-height legibility under time pressure, with no principled way from physiology alone to pin down a single value inside that range.

**Combining them.** Required letter height h = θ_min × v × T. This makes the relationship between letter height and approach speed **linear**, for any fixed legibility-angle threshold and fixed reading-time budget — which answers the "why linear" half of the question directly: it falls out of h = θ_min·v·T being linear in v with everything else held constant.

**The constant.** The industry's "feet of viewing distance per inch of letter height" ratio is just L/h = 1/θ_min. Picking a working value of θ_min ≈ 7 arcmin (≈0.00204 rad) as a plausible midpoint of my 5–15 arcmin degradation estimate gives L/h ≈ 41 ft per inch of letter height. Sanity-checking against remembered real-world signage: a 40 mph arterial shopping-center monument sign under this model wants h ≈ 5.75–6 inches of primary copy (T=4s, L=235ft) — which matches typical real monument-sign primary copy in that speed context. A 55 mph highway pylon sign under the same fixed-T model under-predicts real observed letter heights (predicts ~8in, real ones run noticeably larger, 12–18in+), which is itself a useful finding: a single fixed T doesn't hold across the whole speed range — higher-speed/higher-stakes contexts plausibly need a longer effective T (more distractions, more complex maneuvers, more competing sign clutter) or a stricter θ_min, meaning the true relationship is likely mildly super-linear in practice even though the base mechanism (h = θ_min·v·T) is linear.

**Predicted constant, stated as a range:** ~20–80 ft of viewing distance per inch of letter height, center estimate ~40 ft/inch, driven entirely by uncertainty in θ_min (5–15 arcmin).

## Corpus Answer

The sign industry formalizes exactly this as the **Legibility Index (LI)**, published by the US Sign Council (USSC) — "Sign Legibility, Overview and Calculation Methodology." Required letter height (inches) = viewing distance (ft) ÷ LI. LI varies by font, case, color/contrast, and illumination:

- A commonly cited *general* rule of thumb: **~30 ft of viewing distance per inch of letter height** ("letters are legible from 30 feet per inch of height").
- A more conservative version widely repeated in sign-shop marketing copy: **~10 ft per inch** (i.e., "add 1 inch of letter height per 10 ft of distance") — this is the floor/safe-default version, not the research-derived one.
- USSC's own published example value: **LI ≈ 22** for externally-lit black Helvetica capitals on a white background — i.e., ~22 ft/inch for that specific (good but not best-case) font/contrast combination. Best-case simple sans-serif/high-contrast combinations push higher; poor combinations (script fonts, low contrast, non-illuminated) push the ratio down, sometimes well under 20.

So the accepted real-world range runs roughly **10–50 ft/inch** depending on conditions, centered practically around **20–30 ft/inch** for realistic (not best-case) signage.

Sources:
- [Sign Legibility Index background — Signs.com Blog, "Signage 101 - Letter Height Visibility"](https://www.signs.com/blog/signage-101-letter-height-visibility/)
- [Letter Sizing Calculator — The Sign Chef](https://www.thesignchef.com/letter-sizing-calculator)
- [Sign Letter Height Visibility Chart — Signazon](https://www.signazon.com/help-center/sign-letter-height-visibility-chart.aspx)
- [Letter Height Visibility Chart — Pannier Graphics](https://www.panniergraphics.com/blog/letter-height-visibility-chart-for-outdoor-sign-readability)
- [4 Critical Factors for Signage: Letter Size and Visibility — Stouse](https://www.stouse.com/4-critical-factors-for-signage-letter-size-and-visibility/)

## Delta

**Category: rediscovered**

The derivation independently arrived at the same core mechanism the industry actually uses — a fixed angular-legibility threshold converted into a linear "feet of distance per inch of letter height" constant (which is precisely what USSC's Legibility Index *is*, algebraically: LI = L/h = 1/θ_min in the right units). The derived range (20–80 ft/inch, center ~41) overlaps the accepted range (10–50 ft/inch, practical center ~22–30) but sits on the optimistic/high side — implying my assumed θ_min (7 arcmin) was a bit more forgiving than what real-world font/contrast/lighting conditions actually deliver (the corpus's implied θ_min for LI=22 is closer to ~13 arcmin). That's a legitimate, explainable miss: clinical/ideal-condition reasoning tends to underestimate how much real fonts, real contrast, real weather, and real driver attention degrade legibility versus a lab acuity test.

The secondary finding — that a single fixed reading-time budget T under-predicts observed letter heights at highway speeds, implying the true speed relationship is mildly super-linear rather than strictly linear — is not something the standard LI formula itself asserts (LI treats letter-height-vs-distance as a fixed ratio independent of speed, applied post-hoc by choosing a required viewing distance for the road's speed). This is closer to a **novel** framing detail riding on top of an otherwise rediscovered result: real signage codes typically increase the *required viewing distance* input for higher-speed roads (which is well established, e.g. AASHTO/MUTCD-adjacent sight-distance guidance), but the derivation reached that same conclusion by noticing the fixed-T model's residual error at highway speed, rather than by citing traffic-engineering sight-distance tables. Net categorization stays **rediscovered** since the core LI mechanism was independently reconstructed and lands in the right ballpark.

## Commentary

The exercise validates that "legibility index" is not an arbitrary sign-industry convention — it's the necessary consequence of two physical facts (visual acuity is angular, and a moving observer has a fixed time budget) that anyone reasoning carefully from optics + traffic psychology would reconstruct. The place the derivation was weakest was quantifying the "real-world degradation factor" from clinical acuity to functional roadside legibility — that number (θ_min in the 7–15 arcmin range) is fundamentally empirical, not derivable from physics alone, and the corpus's actual measured value sits at the harder end of my guessed range. That's a good calibration signal: physics-only reasoning nails the *functional form* reliably but is systematically optimistic on *empirical constants* that depend on real fonts, real weather, and real distracted humans — worth remembering before ever quoting a first-principles number as a spec without checking it against a measured constant.
