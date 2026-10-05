# First-Principles Spike — 2026-10-05

**Question:** Why should sign letter height scale linearly with viewing distance, and what is the constant?
_(Backlog was empty; question self-generated from signage industry primitives.)_

## First-principles answer (derived before any lookup)


1. Primitive: the eye resolves angles, not sizes. A letter of height h at distance d subtends theta = 2*atan(h/2d) ~ h/d for small angles. Legibility is therefore a function of theta only (holding contrast/lighting fixed). Same theta => same legibility => h = k*d. Linear scaling is geometry, not convention.
2. Constant k from acuity: 20/20 vision resolves detail of 1 arcminute. A letter is designed on a ~5x5 grid of strokes, so the letter must subtend ~5 arcmin to be just identifiable. tan(5') = 0.001454 => h = d/688. At 100 ft: 1.75 in. That is the absolute floor: perfect eyes, high contrast, unlimited reading time.
3. Real viewers aren't threshold viewers. Divide acuity: 20/40 (common, DMV pass) => x2. Low contrast, glare, dusk => x1.5-3. Motion: a driver at 45 mph (66 ft/s) has a bounded read window; a sign must be readable for ~ 2-4 s and a reader needs headroom to read quickly not just resolve => x2-3. Combined safety factor ~ 5-10 over threshold => h ~ d/130 to d/70.
4. So I predict the rule of thumb: roughly 1 inch of letter height per 10 ft (d/120) as the "max legibility distance" for a good-contrast sign, and a comfortable-reading distance several times shorter (~ 1 in per 3-5 ft... ) because comfortable reading needs more than threshold. Roughly rule: max distance ~ 100x height (in feet per inch ~ 10).
5. Implications for B9: (a) the constant depends on speed — highway signs need larger k than pedestrian wayfinding; effective k should scale with speed (reading time t: d_read = v*t, so h = v*t/120 ). At 30 mph (44 ft/s), 3 s of read time => 132 ft => 13 in minimum letters. (b) Contrast and stroke weight change k. Thin script faces have effective acuity demand of a smaller stroke => lose distance. (c) Letter height means cap height, not font size; x-height-heavy fonts read larger.
Confidence: linear scaling certain; constant within factor ~2 of 1in/10ft.

## Corpus answer (searched after derivation)
- Standard rule (USSC / ISA, repeated by sign vendors): **1 inch of letter height per 10 ft of maximum readable distance** (d/120) — a ceiling for a still viewer with normal vision in good light.
- Comfortable at-a-glance reading: about **1 inch per 4 ft**.
- Sources: signs.com Signage 101 letter-height visibility; panniergraphics.com letter-height chart; signknights.com viewing-distance guidelines; optsigns.com road-sign readability.
- Not confirmed by this search (from background knowledge only, so unverified here): highway practice (MUTCD) uses a legibility index of ~30 ft/in (Clearview ~40 ft/in), which is consistent with the speed/read-time argument above.

## Delta: **rediscovered**
Linear scaling and the 1 in / 10 ft constant (d/120, ~5.7x over the 5-arcmin acuity floor of d/688) were reached independently. The derivation also explains *why* the constant is a ceiling and why comfortable reading needs ~2.5x more height, and predicts the speed dependence (h = v*t/k), which the vendor corpus mostly omits. That extra framing is a nice-to-have, not strictly novel.

## Commentary
Use for B9 quoting: treat 1 in/10 ft as max distance, 1 in/4 ft as design target; for roadside/monument signs size from speed x read-time, not from a flat ratio. Confidence in the linear model: high; in constants: medium (vendor sources are secondary).
