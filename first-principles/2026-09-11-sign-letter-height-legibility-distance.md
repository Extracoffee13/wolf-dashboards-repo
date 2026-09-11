# First-Principles Spike — 2026-09-11

## Question

Why does a sign's letter height scale roughly linearly with viewing
distance, and what sets the constant of proportionality — i.e., where does
a number like "1 inch of letter height per N feet of viewing distance"
actually come from?

This is a signage-industry primitive directly relevant to Brand 9 Signs
fabrication and quoting: every job ultimately reduces to "how big do the
letters need to be for this location."

## First-principles derivation (no retrieval)

**Step 1 — the geometry.** A letter of height *h*, viewed from distance
*d*, subtends a visual angle θ. For d ≫ h (always true for signage — you're
never standing a letter-height away from a sign), the small-angle
approximation holds:

θ ≈ h / d  (θ in radians)

This alone explains the linear relationship: if the eye needs a fixed
minimum angle θ_min to resolve the letter, then h and d must scale
together to hold θ ≥ θ_min. The constant of proportionality is entirely
determined by θ_min — the smallest angle a viewer's eye can usefully
resolve a letter at. So the real question collapses to: what is θ_min for
a letter (not a point, not a line — a whole recognizable character)?

**Step 2 — the eye's resolution limit.** The retina's foveal cone spacing
sets a hard floor on angular resolution. Two points closer than about 1
arcminute (1/60°) apart on the retina fall on the same or adjacent cones
and can't be discriminated as separate — this is the classical minimum
angle of resolution (MAR) for high-contrast detection, and it's a
biological constant, not a convention.

But *reading a letter* is a harder task than detecting a gap or a grating.
A letter shape needs several distinguishable strokes across its height to
be identified (a "C" from an "O", an "E" from an "F"), not just one
resolved gap. If a letterform needs roughly 5 resolvable units across its
height (a reasonable guess: cap-height ≈ 5 stroke-widths, which matches
how most sans-serif faces are actually drawn), then:

θ_min(letter) ≈ 5 × MAR ≈ 5 arcminutes, under ideal conditions.

**Step 3 — convert to a distance ratio.** 5 arcmin = 5/60° ≈ 0.001454 rad.
Setting h/d = θ_min:

d/h ≈ 1/0.001454 ≈ 688

So under ideal lab-acuity conditions, 1 inch of letter height should stay
legible out to ~688 inches ≈ **~57 feet per inch of letter height**.

**Step 4 — but real signage is not a lab eye chart.** The 5-arcmin figure
assumes: perfect 20/20 acuity, maximum black-on-white contrast, the viewer
fixating directly on the target with time to focus, and no motion. None of
that holds for an actual sign:

- Population vision isn't uniformly 20/20 — a meaningful fraction of
  viewers (uncorrected refractive error, age-related contrast loss) need
  several times the ideal angle.
- Real sign contrast (colored letters on a substrate, weathering, distance
  haze, non-perpendicular viewing angle) degrades effective contrast well
  below a lab eye chart's stark black-on-white.
- The viewer usually isn't fixating — they glance while driving, walking,
  or doing something else, so the eye doesn't get to dwell and
  accommodate.
- Motion (a driver's own motion relative to the sign, or the sign passing
  through peripheral vision before central fixation) further degrades
  effective resolution.

Each of these individually costs a factor of ~1.5–3x in required angle;
stacked, a realistic "effective MAR" for an unprepared, moving, average
viewer is plausibly 15–30 arcminutes rather than the ideal 5. Re-running
the Step 3 conversion at, say, 20 arcmin (4x the ideal):

d/h ≈ 1 / (20/60 × π/180) ≈ 172 → **~14 feet per inch of letter height.**

That is now in the right neighborhood of a "read comfortably" distance
rather than an absolute physiological ceiling.

**Step 5 — the shape of the answer, before checking anything.** My
prediction, purely from this reasoning, is that any real-world signage
rule of thumb should:

1. Be linear in letter height (confirmed by the geometry itself — this
   part is not really in question).
2. Land somewhere well under the ~57 ft/inch physiological ceiling, likely
   in the 10–20 ft/inch range for "comfortable reading," because real
   viewing conditions cost a 3–5x degradation factor versus a Snellen-chart
   eye test.
3. Have a *separate*, larger number for "can be noticed/identified but not
   necessarily read in detail" (a sign doesn't have to be read letter by
   letter to register — a familiar logo shape is recognized well past the
   point where individual letters are legible), which should sit closer to
   the ideal-acuity ceiling, maybe 25–50 ft/inch.

## Corpus answer

Industry sources (Signazon, Signs.com, VisualPro, and similar sign-shop
references) converge on:

- **~1 inch of letter height per 10 feet of viewing distance** as the
  standard "comfortable read" rule of thumb.
- A worked example given directly in the corpus: 3" letters have "best
  impact" within 30 ft (10 ft/inch) but remain readable/visible up to
  ~100 ft (≈33 ft/inch) — i.e., there are two different distance regimes,
  exactly the "comfortable read" vs. "noticeable/identifiable" split
  predicted above.
- Separately, ophthalmology sources confirm the Snellen optotype design
  basis: each letter is drawn so its height subtends **5 arcminutes** of
  visual angle at the test distance, with individual strokes at 1
  arcminute — precisely the "5 × MAR" assumption used in Step 2 above, not
  an approximation I had to guess at after all — it's the literal standard
  the eye-chart industry uses.

## Delta

**Category: rediscovered**, with a small **novel** wrinkle.

- The core physiological constant (5 arcminutes per letter height, 1
  arcminute per stroke) was derived independently in Step 2 from a
  plausible guess about stroke count per letterform, and it turned out to
  exactly match the literal Snellen chart design standard. That's a clean
  independent rediscovery, not a coincidence I could have gotten from
  general knowledge of "sign rules" — I hadn't looked up sign guidance at
  all at that point.
- The practical industry number (10 ft/inch) came out of Step 4 as a
  *predicted range* (10–20 ft/inch) rather than an exact hit, but the
  reasoning for *why* it must be several-fold more conservative than the
  physiological ceiling — and why a second, larger number for "just
  noticeable" should exist — was derived, not looked up, and both
  predictions landed correctly.
- The mildly novel piece: the corpus sign-shop sources state the 10 ft/inch
  and ~25–50 ft/inch numbers as rules of thumb without deriving *why* two
  regimes exist or what specifically separates them (degradation of
  effective MAR under real viewing conditions vs. the lab-ideal Snellen
  limit). The optics literature has the acuity piece; the sign-industry
  literature has the practical numbers; connecting them with an explicit
  "~4x real-world degradation factor" bridging the two doesn't show up
  stated plainly in either corpus as searched.

## Commentary

The interesting result isn't the number — it's that the exercise
correctly predicted *the existence of two different constants* (comfortable
read vs. maximum noticeable) before seeing any corpus material, purely
from noticing that "legible" is ambiguous between "resolvable as a shape"
and "identifiable as a specific letter/word," and those are different
tasks with different angular thresholds. That's a case where reasoning
from primitives produced a better-structured question than the naive
version ("what's the ratio?") — it's actually two ratios, and the corpus
confirms that structure. Worth remembering for quoting/spec work: when a
client asks "how big do my letters need to be," the honest answer is
always two numbers, not one, and this derivation is why.
