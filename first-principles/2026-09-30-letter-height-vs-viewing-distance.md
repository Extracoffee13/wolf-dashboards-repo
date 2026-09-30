# Spike 2026-09-30: Why does letter height set legible distance, and what ratio should B9 size signs to?

## First-principles answer (derived before any lookup)

**Primitives.** A sign is information moving from a surface to a retina. The eye is a lens + sensor with a finite resolving angle. So the only thing that can matter geometrically is the *angle* a letter subtends, not its absolute size. Angle ≈ height / distance (small-angle), so legibility is a ratio: distance = height / angle. Scaling the letter scales the distance linearly. That already kills any "square-root" or "diminishing returns" idea: geometry is strictly linear.

**Threshold.** A healthy eye resolves detail of about 1 arcminute (1/60°). A letter needs several resolvable features (a stroke, a gap, a stroke, a gap, a stroke for an "E"), so the minimal legible letter is ~5 resolvable units tall: ~5 arcmin ≈ 0.00145 rad. Distance at threshold = h / 0.00145 ≈ 690 h. For 1 inch of letter: ~57 ft. That is the *cliff edge*: a perfect-contrast, stationary, well-lit, 20/20 viewer guessing letters.

**Why no one should size to the threshold.** Real viewing differs from the threshold in four multiplicative ways, each of which wants a bigger angle:
1. Reading needs recognition of words, not guessing single letters (~2x).
2. Contrast and lighting are worse than a test chart (dusk, glare, colored backgrounds) (~1.5-2x).
3. The viewer is a median viewer, not a 20/20 viewer; many drivers are 20/40 (2x).
4. Motion and time budget: a driver has about 2-3 seconds of glance to read, decide, and brake/turn. Time to read scales with how close to threshold you are, so you want to be far above it and let recognition be instant.
Product of those is roughly 4-10x on angle, so a *design* ratio lands around 7-15 arcmin... up to ~28 arcmin for "instant" reads. That gives distances from ~1 in per 25 ft (comfortable) down to ~1 in per 10 ft (read at a glance, in motion).

**Implication for sizing.** Work backward: (1) distance at which the viewer must have *decided*, not first seen (this is decision distance = speed x reaction/decision time, plus the sight line limits); (2) choose the regime (glance vs. pedestrian); (3) height = decision distance / ratio. Only then does the legibility distance equal the decision distance. Corollary: message length must shrink as speed grows, because word count multiplies read time. Another corollary: only the x-height/stroke of the *smallest meaningful element* matters, so tall letters with thin strokes or low contrast waste the angle.

**Confidence in the derivation:** high on the geometry and the linear law; medium on where the practical multipliers land (they are empirical).

## Corpus answer

Searched after deriving. Industry rule of thumb (International Sign Association and most sign shops): about **1 inch of letter height per 10 feet** of viewing distance for best impact/at-a-glance reads; practitioners also cite ~1 in per 25 ft as a maximum legible distance and ~1 in per 50 ft as the bare threshold. The underlying basis cited is the Snellen standard: 1 arcmin detail, 5 arcmin letter. The same sources frame the ratios as angular sizes: 1:50 ≈ 5.7', 1:25 ≈ 11.5', 1:10 ≈ 28.6'.
Sources: [Signazon letter-height chart](https://www.signazon.com/help-center/sign-letter-height-visibility-chart.aspx), [Digital Polo letter height by distance](https://www.digitalpolo.com/sign-letter-height-viewing-distance/), [Snellen chart (Wikipedia)](https://en.wikipedia.org/wiki/Snellen_chart), [Pannier Graphics](https://www.panniergraphics.com/blog/letter-height-visibility-chart-for-outdoor-sign-readability).

## Delta category: **rediscovered**

Same model (linear angle law, 5-arcmin Snellen threshold, practical ratios between threshold and "glance"), same numeric bands (my 690h ≈ 57 ft/in threshold matches the ~1:50 cited one; my glance regime matches 1:10). Not novel: the corpus already states the angular interpretation, though many shop pages present only the bare "1 in : 10 ft" rule without it.

## Commentary

- Value-add over the corpus rule is the *decision-distance* framing: the ratio is a regime choice, not a constant, and the real input is speed x decision time. Worth turning into a B9 sizing worksheet (speed, setback, sight line -> decision distance -> letter height by regime).
- Caveat: the multiplier stack (4-10x) was reasoned, not measured; the corpus bands corroborate it only loosely. Do not quote the multipliers to clients.
- Not checked: MUTCD/FHWA 1 in per 30-50 ft highway legend sizing, and ADA tactile rules. Those would be a good follow-up spike.
