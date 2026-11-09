# First-Principles Spike — 2026-11-09

**Question:** How tall must sign letters be for a given viewing distance (and what rule of thumb falls out)?

## First-principles answer (derived before any lookup)
- Legibility is an angular problem: the eye resolves angle, not size. Angle ≈ h/d (radians) for letter height h at distance d.
- A reader with 20/20 acuity resolves detail of 1 arcminute. A letter is built on a 5x5 grid, so strokes are 1/5 of letter height: the letter must subtend ~5 arcmin (0.00145 rad) to be read at all.
- Threshold distance d = h / 0.00145 ≈ 688·h → about **57 ft per inch** of letter height. That is a cliff-edge limit, not a design number.
- Derate: (1) the population is not 20/20; 20/40 (the common driving-vision floor) halves it to ~29 ft/in. (2) Real signs have imperfect contrast, glare, weather, stroke/spacing variation: another factor of ~1.2-2. (3) Motion and dwell: at 60 mph (88 ft/s) a driver needs several seconds to read and decide, so the sign must be legible well before the threshold distance.
- Result: a design number between ~30 ft/in (population-safe, traffic) and ~10 ft/in (comfortable, glance-and-decide pedestrian/storefront). Always divide required distance by the index to get letter height. Complexity (more words) pushes toward the smaller index.

## Corpus answer
- MUTCD legibility index: 30 ft per inch of letter height for traffic signs; FHWA research finds ~40 ft/in for good vision (90th-100th percentile).
- Sign-trade rule of thumb: ~10 ft per inch for comfortable reading; digital rule ~ height = distance/25 (ft).
- Complexity multipliers ~0.83 (moderate) and ~0.67 (high). Sources: FHWA (fhwa.dot.gov/publications/research/safety/15027), NAP human factors guidance, Univ. of Kentucky safe design guide, Stouse "Letter Height for Signs".

## Delta category: **rediscovered**
The derivation's 57 ft/in at 20/20 and ~29 ft/in at 20/40 independently lands on MUTCD's 30 and the 40-45 FHWA range; the 10 ft/in trade rule matches the "comfort/dwell" derating.

## Commentary
Reasoning got the structure (angle, 5-arcmin letter, acuity derating, dwell time) right; the corpus just supplies calibrated constants. Useful B9 framing: pick the *population acuity* and *dwell time* first, and the ft/in index is an output, not an input. Confidence moderate: derating factors were estimated, not sourced.
