# Spike 2026-10-08: Letter height vs viewing distance

**Question:** What letter height is needed for a sign to be read at distance d?

## First-principles answer (derived before any lookup)

1. Legibility is an angular problem, not a linear one. The eye resolves angle, so only the ratio height/distance matters. Scaling letter and distance together leaves legibility unchanged.
2. Anchor on human acuity. 20/20 vision resolves detail of 1 arcminute. A recognizable letter needs a 5x5 grid of such details (strokes plus gaps), so a letter at threshold subtends 5 arcmin (Snellen).
3. Small-angle conversion: 5 arcmin = 0.001454 rad. Threshold height h = 0.001454 * d. A 1 in letter is therefore at threshold at ~688 in = **57 ft**. Threshold ratio is about **1 in per 57 ft**.
4. Threshold is not a design target. Real readers need an acuity reserve for:
   - below-20/20 vision (many viewers are worse, and old eyes lose contrast sensitivity)
   - poor contrast, glare, dusk, dirty faces
   - ornate or narrow fonts (lower effective stroke width)
   - time: a driver gets a glance of ~1-2 s, and reading must finish with margin to act
   So multiply the angle by a reserve factor k of roughly 1.5 to 6 depending on context.
5. Resulting ratio is 1 in per (57/k) ft:
   - k ~ 1.5 (good contrast, static, bold font): ~1:40
   - k ~ 2: ~1:30
   - k ~ 6 (fast, cluttered, must be read quickly): ~1:10
6. Prediction: any rule of thumb is a point on a one-parameter family set by k. The disagreement between rules is a disagreement about reserve, not about physics. Rules above ~1:57 should be impossible, and should fail even for perfect vision.

## Corpus answer

Search (standard mode, secondary sources only; FHWA document itself not opened):
- 1 in per 40 ft, quoted as an FHWA rule of thumb for non-Interstate signs (via a forum post; unverified).
- 1 in per 30 ft, common sign-industry chart value (indoor or smaller copy).
- 1 in per 10 ft, trade-forum "fast read / vehicle" conservative rule.
- Michigan code adds 1 in per 35 ft above 5 in letters.
- Calculators bucket as 10 (vehicle fast read), 25 (pedestrian), 40 (less critical).
- Caveat everywhere: contrast, lighting, speed, font, and viewer vision modify the ratio.

Sources: https://www.stouse.com/?p=1020, https://www.signs101.com/threads/viewing-distance.63700, https://state-rules.com/michigan/mac/408.42230/, https://uksignboards.com/forums-2/discussion/does-anyone-know-of-a-guide-for-distance-legibility/

## Delta: **rediscovered**

The derived structure matches: ratio-only dependence, a threshold near 1:57, and a spread of 1:10 to 1:40 explained by a context-dependent reserve factor. The corpus gives the numbers without the 1:57 ceiling or the reserve-factor framing.

## Commentary

- Useful B9 framing: 1:40 is ~1.4x threshold, 1:30 ~1.9x, 1:10 ~5.7x. When a client asks "how big?", ask first "how fast and how cluttered?", which picks k, then compute.
- The 1:40 FHWA figure is unverified secondhand; verify against MUTCD/FHWA before quoting it to a client.
- Not tested: whether 5 arcmin is the right per-letter threshold for stroke-width-limited modern fonts (Clearview vs Highway Gothic).
