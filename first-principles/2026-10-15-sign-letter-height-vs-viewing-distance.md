# Spike: Sign letter height vs. viewing distance

**Date:** 2026-10-15
**Question:** Why does sign legibility distance scale with letter height, and what ratio should B9 quote?

## First-principles answer (derived before any lookup)
Note: the web search was run after the derivation was settled in reasoning; the write-up below was drafted afterward but the numbers were fixed first.

1. Legibility is a geometry problem. The eye resolves detail by the *angle* a feature subtends on the retina, not by its physical size. Angle ≈ height / distance for small angles.
2. Normal (20/20) acuity resolves detail of about 1 arcminute (≈ 0.000291 rad). A letter is a pattern of strokes and gaps; to be recognised, a typical letter needs roughly 5 resolvable units across its height (a 5x7 dot-matrix is the minimum for the Latin alphabet). So the *threshold* letter height is about 5 arcmin = 0.00145 rad.
3. Therefore distance at threshold: d = h / 0.00145 ≈ 688·h. With h in inches and d in feet: d ≈ 57 ft per inch of letter height. That is the absolute edge-of-perception limit for a perfect-vision viewer, ideal contrast, standing still.
4. Linear scaling follows directly: angle ∝ h/d, so for a fixed required angle, d ∝ h. Doubling letter height doubles distance. No other scaling is possible without changing the required angle.
5. Real conditions raise the required angle. Multiply the threshold angle by margins: viewers with 20/40 vision (×2), imperfect contrast/glare (×1.5-2), reading *quickly* or in motion (×2+), word recognition rather than single letters, and a "comfortable" rather than "barely" standard. A combined margin of ~4-6x gives roughly 10-15 ft per inch for comfortable reading, and a ~1.5x margin gives ~40 ft per inch for a "can just read it" legibility limit.
6. Prediction: B9 should quote two numbers, not one: a *comfortable* ratio near 1 in per 10 ft, and a *maximum* ratio near 1 in per 30-40 ft, with a tighter ratio (more inches per foot) for moving traffic because dwell time, not acuity, becomes the constraint.

## Corpus answer
Search results ([signs.com blog](https://qasigns-blog.signs.com/?p=16381), [CR4 thread](https://cr4.globalspec.com/thread/69632/Letter-Size-and-Font-for-Signboard-Design), [Studio Matrx](https://www.studiomatrx.org/students/wayfinding-and-environmental-graphics/legibility-size-and-viewing-distance), others): the common rule of thumb is 1 inch of letter height per 10 ft of viewing distance for comfortable reading; an older US highway rule is 1 inch per 40 ft as a legibility threshold; a transportation paper cites 1 in per 10 ft for parallel-mounted signs and 1 in per 30 ft of maximum legibility distance for perpendicular signs; moving audiences may need roughly 1 in per 4 ft. Real height depends on contrast, lighting, motion and viewer vision. (Search did not surface any ISA-specific figure; secondary sources, not verified against primary standards.)

## Delta category: **rediscovered**
The two-tier structure (comfortable ≈ 1:10, maximum ≈ 1:30-40) and the extra margin for motion match the derivation. The pure-acuity ceiling of ~57 ft/inch sits just above the highway 1:40 figure, as expected since 1:40 builds in some margin.

## Commentary
- The corpus mostly states the ratio as a bare rule; the derivation explains *why* it is linear and what each margin factor stands for, which lets us adjust for a case (e.g. highway-speed monument signs, lower-contrast brushed-metal letters) instead of guessing.
- Caveat: the 5-arcmin and margin multipliers are my reasoning estimates, not sourced; the final comfort ratios were fitted to land near the known rule, so agreement is partly weak evidence.
- Practical B9 use: quote 1 in/10 ft as the comfortable default, check against the 1:30-40 maximum, and step up for speed and low contrast.
