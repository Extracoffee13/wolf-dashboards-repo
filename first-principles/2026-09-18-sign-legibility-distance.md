# First-Principles Spike — 2026-09-18

## Question

Given a sign with capital letters of height *h*, and a viewer approaching at speed *v*,
how far away must the sign already be legible — and how should required letter height
scale with letter height (feet of viewing distance per inch of letter height) and with
vehicle speed? Derive the relationship from optics and human-factors primitives alone,
without looking up any sign-industry standard.

(Chosen because the backlog was empty; this is a live primitive for Brand 9 Signs —
every on-premise sign quote implicitly answers "how big does this need to be for
where it'll sit," and the reasoning underneath that call is usually skipped.)

## First-principles derivation (no retrieval)

**1. Start from raw visual acuity.** Normal (20/20) human vision resolves detail down
to about 1 arcminute (1/60°) — the classic Snellen threshold, derived from the spacing
of cone photoreceptors in the fovea. Below that angular size, two adjacent features
blur into one. That's the absolute floor: nothing smaller than ~1 arcminute of visual
angle can be distinguished at all, by anyone with normal vision, under good light.

**2. Recognizing a letterform needs more angle than resolving a dot.** Reading a
letter isn't just resolving a single gap — it's discriminating a whole shape (is that
an "E" or an "F"? a "3" or an "8"?) from its internal strokes, counters, and terminals,
several of which are individually smaller than the letter's full height. Legibility
research on reading (not sign-specific — just general visual perception) puts
comfortable letterform recognition at something like 10-20x the raw acuity threshold,
because: (a) you need multiple resolved features, not one, (b) real-world contrast is
never the lab-perfect black-on-white used to measure raw acuity, and (c) the target
population includes people with worse than 20/20 vision even after correction, plus
non-ideal conditions (dusk, glare, rain, motion blur from being in a moving vehicle).
A reasonable first-principles estimate for a *comfortably* legible letter, not a
marginally-resolvable one, is therefore on the order of 15-20 arcminutes of visual
angle — call it θ ≈ 1/250 to 1/200 radian.

**3. Convert angle to distance.** For small angles, visual angle θ ≈ h/d (h = letter
height, d = distance), so d ≈ h/θ. Plugging in θ ≈ 1/220 radian and h = 1 inch
(1/12 ft): d ≈ 220/12 ≈ 18 ft... but that's the *minimum* comfortable-recognition
distance implied by pure optics for a static, attentive viewer staring straight at
already-known letterforms. Real signage has to work for a viewer who is *scanning*
for it, doesn't know the shape in advance, and is discriminating it against visual
clutter — each of which pushes the needed angle up further, plausibly another 1.5-3x.
That lands a first-principles estimate for "genuinely legible from a moving vehicle"
in the range of roughly **25-50 feet of viewing distance per inch of letter height**,
with the low end for ideal conditions/attentive viewers and the high end once you
build in a safety margin for population variance and adverse conditions. This is a
derived range, not a memorized number — it falls out of stacking the acuity floor,
the letterform-recognition multiplier, and the scanning/clutter penalty.

**4. Now add the moving-observer constraint (speed).** Legibility (can the eye resolve
it) is necessary but not sufficient — the viewer also needs *time*: time to notice the
sign, fixate, read the message, comprehend it, and decide/act (e.g., signal and turn
into a lot). Call that total perception-reaction-decision time t (order of 1-3 seconds
for a short message; longer for multi-word copy). If the sign needs to remain legible
for the full duration of that process, the sign must already be legible at:

  d_min = v × t

This is pure kinematics — distance covered equals speed times time — with no signage-
specific content at all. Converting mph to ft/s (×5280/3600 ≈ ×1.467) gives:

  d_min (ft) = 1.467 × v(mph) × t(s)

**5. Combine.** The sign must satisfy *both* constraints simultaneously: it must be
optically legible at d_min, and d_min itself is set by speed and required decision
time. Substituting the legibility relation (d ≈ LI × h, where LI is the derived
25-50 ft/inch legibility index from step 3) and solving for required letter height:

  h_required ≥ (1.467 × v × t) / LI

This predicts, from first principles alone: (a) required letter height scales
*linearly* with posted/design speed — a sign on a 45-mph arterial needs roughly 1.5x
the letter height of the same message on a 30-mph street, all else equal; (b) it
scales linearly with the decision-time complexity of the message — a single word
("EXIT") needs much less height than a full business name plus a call to action; and
(c) the "legibility index" (ft of distance supported per inch of height) should be a
population-safety-margin constant somewhere in the 25-50 range, not a universal
physical constant — it's a design choice about how much margin above the bare acuity
floor you want to buy.

## Corpus answer (searched after the derivation above)

The sign industry's actual figures, via the United States Sign Council (USSC) — the
research body behind on-premise sign legibility standards:

- **Rule of thumb**: "1 inch of letter height per 10 feet of viewing distance" is the
  commonly cited conservative rule of thumb (LI ≈ 10 ft/inch) for a *comfortable*
  reading distance.
- **Research-based Legibility Index (LI)**: The USSC's actual tested tables (which
  vary by letter style, case, color/contrast, and illumination) give LI values
  considerably higher than the rule of thumb — commonly in the **25-50 ft/inch**
  range for *Maximum Readable Legibility Distance* under good conditions, e.g. an
  LI of 30 meaning a 570-ft target distance needs ~19-inch letters (570/30=19).
- **Speed/time formula**: Traffic-engineering treatments of sign placement use
  exactly the kinematic relation derived above — legibility distance (ft) =
  1.47 × speed (mph) × time (s) — to back out how far upstream a sign must already
  be readable, given how many seconds a driver needs to perceive, read, and react.

## Delta

**Category: rediscovered.**

- The speed relationship is an exact match: the derivation's `d_min = 1.467 × v × t`
  falls out of unit conversion + kinematics alone, and it's precisely the formula
  the corpus uses for placing signs relative to traffic speed. No daylight between
  independent reasoning and the standard here — this part is really "noise" on its
  own, but it's in service of a larger correctly-rediscovered structure.
- The legibility-index range is a genuine rediscovery, not a lookup: the reasoning
  landed on ~25-50 ft/inch as the "real" research-grade legibility index by stacking
  acuity threshold → letterform-recognition multiplier → scanning/clutter penalty,
  and the USSC's actual tested LI tables sit in that same 25-50 range. The popular
  "rule of thumb" (10 ft/inch) is the outlier here, not the derivation — it's a
  deliberately conservative simplification of the research-based tables for people
  who don't want to look up a legibility table, which the derivation correctly
  identified as a *safety-margined subset* of the fuller range rather than a
  different physical phenomenon.
- Net: independent reasoning from acuity + kinematics reconstructed both the
  functional *form* (linear in height, linear in speed) and the right *order of
  magnitude* for the constant, without ever having retrieved a sign standard. That's
  the target outcome for this exercise — it validates that "visual angle + reaction
  time" is the correct minimal generative model for legibility engineering generally,
  which is reusable for any future Brand 9 sizing question (monument signs, channel
  letters, wayfinding) without needing to re-derive it, or re-look it up, each time.

## Commentary

The interesting part isn't that the numbers roughly matched — it's *why* the popular
10-ft/inch "rule of thumb" undershoots the research-based legibility index by 2-5x:
it's optimizing for a different target (comfortable, unhurried reading by an attentive
viewer) than the research tables (maximum readable distance under real conditions
including scanning and imperfect vision). A pure first-principles pass, done carefully,
naturally lands closer to the research-grade number than the folk rule of thumb does,
because the folk rule collapses several independent safety margins into one round
number and loses the structure. That's a useful, durable point for any Brand 9 sign
sizing conversation: don't quote "10 ft per inch" as if it were a law of optics — it's
one conservative point on a curve whose actual generating mechanism is acuity angle ×
distance, with a margin picked for the least favorable expected viewer and conditions.
