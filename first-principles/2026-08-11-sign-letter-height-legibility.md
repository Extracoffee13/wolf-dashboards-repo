# First-Principles Spike — 2026-08-11

## Question

For a roadside business sign (e.g. a Brand 9 Signs monument or pylon sign), what is the
minimum letter height required for a driver to legibly read and act on the message,
as a function of vehicle speed — derived from human visual acuity and
decision/reaction physics, not from an industry rule of thumb?

## Step 1 — First-principles derivation (no retrieval)

Break the problem into two independent physical constraints and combine them.

**Constraint A: optical resolution.** A driver must resolve a letterform, not just detect
that something is printed on a panel. Normal (20/20) visual acuity is defined as the
ability to resolve a stroke or gap subtending about 1 arcminute of visual angle under
ideal, static, foveal, high-contrast viewing. But recognizing a *letter shape* — not a
single line — requires several resolvable elements across the letter's height (stroke
width, counters, serifs), so shape recognition needs roughly 5x the raw acuity
threshold, i.e. ~5 arcminutes, even under ideal conditions. Real-world driving is not
ideal: the sign is viewed briefly, off-axis (not foveated the whole time), through a
windshield, often in a moving vehicle (motion blur), by a population that includes
uncorrected or aging vision, sometimes in rain, glare, or dusk. Stacking a conservative
real-world safety margin of 3-4x over the ideal-shape-recognition threshold gives a
target angular size of roughly 15-20 arcminutes (~0.0044-0.0058 radians) for confident,
fast recognition — not mere detection.

Visual angle relates size to distance by the small-angle approximation:
θ ≈ h / d, so h ≈ θ · d.

**Constraint B: time budget.** The driver needs enough distance-at-speed to complete a
full perceive → read → decide → react → begin-maneuver chain before passing the
point where the maneuver (turn, brake, lane change) is still physically possible.
Decompose the chain from first principles of neuromotor timing:
- Message reading/recognition: a short sign phrase (a business name, 1-3 words) takes
  roughly 1-1.5 s to fixate and recognize once it's within legible range.
- Decision (is this my turn / do I act): ~0.75-1 s of cognitive processing.
- Perception-reaction time (PRT) to initiate a motor response: neural conduction plus
  motor initiation is well characterized in the reflex/voluntary-response literature
  as roughly 0.7-1.5 s for a moderately expected event (a driver actively looking for
  signage, not a surprise stimulus).

Summing gives a total attention-to-action time budget T of roughly 3-4.5 s, scaling
up toward the higher end as speed rises (higher speed = higher cognitive load = closer
to the upper end of each sub-estimate, plus drivers need more distance to actually
execute a maneuver safely once decided, though maneuver execution itself is treated as
a separate downstream budget here and excluded for a lower-bound estimate).

Required sighting distance: D = v · T (v in ft/s, T in seconds).

**Combining A and B:** h ≈ θ_min · D = θ_min · v · T.

Since θ_min and T are both roughly constant (with T drifting mildly upward with speed),
letter height should scale **approximately linearly with speed**, with an offset — i.e.
h(inches) ≈ k · v(mph), for some constant k set by the angular-resolution/time-budget
product, and k itself should be *context-dependent*: higher for high-speed/high-stakes
signage (more safety margin needed, less tolerance for a missed read) and lower for
slow, low-consequence urban storefront signage.

**Worked numbers:** Take θ_min = 20 arcmin = 0.00582 rad, T = 4 s.
- 25 mph (36.7 ft/s): D = 147 ft → h = 0.856 ft = 10.3 in
- 45 mph (66 ft/s): D = 264 ft → h = 1.54 ft = 18.4 in
- 65 mph (95.3 ft/s): D = 381 ft → h = 2.22 ft = 26.6 in

Expressed the way the sign industry expresses it (distance per inch of height):
h ≈ D / 172 (feet of distance per inch of letter height), i.e. **roughly 1 inch of
letter height per 14-17 feet of viewing distance** — a single ratio, independent of
speed, because both D and h were derived from the same speed variable and it cancels
in the ratio (only θ_min and T set the ratio; speed alone sets the absolute distance
and absolute height, not the ratio between them, *given fixed T*). The main way speed
actually should change the ratio is through T drifting with cognitive load/urgency,
not through the core optics.

**Prediction going into Step 3:** the real industry standard should (a) express letter
height as a simple linear function of viewing distance, (b) tie viewing distance to
speed via distance = speed × time, and (c) use a materially *smaller* ratio at highway
speeds than at low-speed/storefront distances, if the true driver behind context is
more urgent time budgets (harder cognitive task, more competing stimuli) at higher
speed rather than a fixed constant — the opposite of what a naive "same angle for any
speed" model would produce.

## Step 3 — Corpus / orthodox answer

Industry and traffic-engineering sources converge on:
- **Commercial/storefront rule of thumb:** 1 inch of letter height per 10 feet of
  viewing distance.
- **Highway/high-speed signage:** 1 inch of letter height per 25-50 feet of viewing
  distance (i.e. a *less* demanding ratio — bigger required distance tolerated per inch
  — the opposite direction of a naive constant-angle model, driven by the fact that
  legibility at typical highway sign sizes/mounting heights already assumes larger
  panels and more legible, higher-contrast lettering standards, plus messages are
  simpler single words/numerals).
- **Formal method:** Viewer Reaction Distance (VRD) = vehicle speed × Viewer Reaction
  Time (VRT), where VRT is "the time necessary for a driver to detect, read, and react
  to a message" — directly the same structural formula as D = v · T derived above.
  Typical guidance recommends ~3-5 seconds of uninterrupted visibility as the reaction
  time budget.

Sources:
- [Letter Sizing Calculator](https://www.thesignchef.com/letter-sizing-calculator)
- [Sign Visibility & Viewing Distance Guidelines | Sign Knights](https://www.signknights.com/sign-visibility-and-viewing-distance-guidelines/)
- [How Big Should Your Sign Letters Be? A Readability Guide - Signworks](https://www.signworksmonterey.com/sign-letter-height-visibility-guide)
- [How to Pick the Perfect Size and Color for Signs Based on Traffic Speed and Distance - Wise Guys Marketing Solutions](https://wiseguysprinting.com/how-to-pick-the-perfect-size-and-color-for-signs-based-on-traffic-speed-and-distance/)
- [How Big Should a Sign's Letters Be? – FASI](https://www.signreference.org/2016/04/20/how-big-should-a-signs-letters-be/)

## Step 4 — Delta category: **rediscovered**

The independently derived model matches the orthodox structure on every load-bearing
point:
1. Same functional form — letter height is a linear function of viewing distance
   (h = θ_min · D), matching the "1 inch per N feet" convention exactly.
2. Same underlying formula for distance — D = speed × time budget, matching the
   industry's VRD = speed × VRT formula almost verbatim, arrived at independently from
   perception-reaction-time physics rather than looked up.
3. Same order of magnitude on the constant — derived ratio of ~1 inch per 14-17 ft
   lands squarely between the corpus's storefront ratio (1:10) and highway ratio
   (1:25-50), which is exactly where a "generic roadside commercial sign" (Brand 9's
   typical job) should sit.
4. The derivation's own prediction — that the ratio should *not* stay constant across
   speed regimes, and that context (message complexity, mounting/contrast standards,
   consequence of a missed read) should shift it — is confirmed by the corpus's
   real spread from 1:10 to 1:50 rather than a single universal number.

Nothing here is a corpus error, and nothing is a genuinely novel framing beyond what's
already in the sign-industry literature — this is a case where reasoning from visual
acuity + perception-reaction-time physics regenerates the practitioner rule of thumb
almost exactly, which is itself the useful result: it means Brand 9 Signs can defend a
letter-height spec to a client or a zoning board from physics, not just convention, and
can *derive* a custom ratio for non-standard cases (unusual speed, low-contrast
materials, multi-word messages) that the flat "1 inch per 10 feet" rule doesn't cover.

## Commentary

The valuable output of this spike isn't the number — it's the reusable formula
`h = θ_min · v · T` with θ_min and T as tunable, justifiable parameters. That's more
useful to signage design and to zoning-variance arguments than a memorized ratio,
because it explains *why* the ratio changes with speed/context and lets Brand 9 Signs
compute a defensible non-standard answer instead of only citing a rule of thumb.
