# Spike: What letter height does a sign need for a given viewing distance?

Date: 2026-10-28

## First-principles answer (derived before any lookup)
1. The eye resolves angle, not size: θ ≈ h/d for small angles.
2. 20/20 acuity resolves ~1 arcmin; a letter needs ~5x5 such units (stroke-gap-stroke-gap-stroke), so the bare threshold is 5' = 0.00145 rad, h ≈ d/690 (~1 in per 57 ft).
3. Threshold is not legibility. Contrast, glare, motion, aging eyes (20/40 doubles the angle) and limited read time demand a 3-6x margin.
4. A 6x margin gives 30' = 0.0087 rad, h ≈ d/115, ~1 in per 10 ft. Scaling is linear in distance; the margin is set by use case.
5. Contrast and stroke weight are multipliers; caps beat lowercase at equal height.
6. Distance is measured from the decision point: required distance = decision distance + speed x (read time + reaction time). A 45 mph driver covers 66 ft/s.

Answer: h ≈ d x tan(5') x margin (margin 5-6 general use) => ~1 in per 10 ft, floor ~1 in per 57 ft; add distance for speed, scale up for low contrast.

## Corpus answer
- Sign-industry heuristic: 1 in of letter height per 10 ft (starting point, not a formal standard).
- Signage Foundation "Sign Legibility: Rules of Thumb" (Bertucci 2006): legibility index ~30 ft per inch; 2015 follow-up repeats it, +15% height for all-caps; 35 ft/in for harder conditions (secondary sources, original not read).
- FHWA MUTCD: 1 in per 40 ft for highway signs.
- Academic on-premise work (citing Garvey 2006): 1:10 for parallel-mounted, 1:30 for perpendicular signs.
- Returns diminish above ~8 in letters.
Sources: signsny.com/resources/distance-visibility, journals.shareok.org/ijsw/article/view/9, mutcd-dr.fhwa.dot.gov/SHSe/Design.pdf

## Delta: rediscovered
Linear scaling, the 1 in/10 ft rule, the caps penalty direction and the contrast/conditions multipliers all match. The corpus's research figures (30-40 ft/in) sit at roughly 1.5-2x threshold, tighter than my 6x "comfortable" margin; the 1:10 rule is the conservative end of the same spectrum. My gap: I did not separate parallel vs perpendicular mounting (viewing angle shrinks effective legibility), nor the all-caps penalty quantitatively.

## Commentary
Quote B9 customers a range tied to use: 1 in/10 ft (comfortable, pedestrian/storefront), ~1 in/30 ft (vehicle, research index), with perpendicular/projecting signs on the looser ratio. State the decision-distance assumption explicitly. Corpus citations are secondary; verify the Foundation figures before publishing as a claim.
