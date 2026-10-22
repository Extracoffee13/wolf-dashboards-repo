# Spike: Sign letter height vs. viewing distance

Date: 2026-10-22

## Question
Why does letter height scale linearly with viewing distance, and what height-per-distance ratio should Brand 9 Signs use?

## First-principles answer (derived before any lookup)
1. Reading is angle-limited. The eye resolves angles, not sizes. A letter of height h at distance d subtends theta ~ h/d (small angle). So the constraint is h/d >= theta_min, which gives d_max = h/theta_min. Linear in h by geometry alone; no other form is possible.
2. Threshold for 20/20 vision: a letter is recognized when it subtends ~5 arcmin (stroke ~1 arcmin). 5 arcmin = 1.45e-3 rad, so d = 688 x h: 1 inch letters at ~57 ft. This is the absolute threshold: perfect contrast, stationary, young eyes.
3. The relevant population is not 20/20. Drivers are licensed at ~20/40 (twice the angle): 10 arcmin -> 344 x h -> 1 inch per ~29 ft.
4. Real signs are not at threshold. Reading a word fluently in a glance needs acuity reserve (roughly 2-3x above threshold), and contrast, glare, dusk, motion and clutter all eat acuity. So a design ratio should be some multiple of the threshold: ~1 inch per 10-15 ft for comfortable reading.
5. Geometry adds a penalty: a sign seen at an oblique angle (storefront blade or flat sign seen from along the street) is foreshortened by cos(angle). At 30 degrees off axis that is a modest loss, at 60 it is a halving. Parallel-mounted signs need more height than perpendicular ones.
6. Time budget: at 45 mph (66 ft/s) a driver needs ~3 s to read and decide, so the sign must be legible ~200+ ft before the decision point. That sets h = distance / ratio, which is where the ratio choice becomes money (bigger letters = more material, labor, and sometimes permit trouble).
Prediction: two ratios should exist: a ~1:30 "threshold for the standard observer" figure and a ~1:10 "comfortable/commercial" figure, with the gap being a ~3x reserve and/or foreshortening.

## Corpus answer
- MUTCD legibility index is 30 ft per inch of letter height, assuming 20/40 acuity ([FHWA](https://www.fhwa.dot.gov/publications/research/safety/15027/004.cfm); [NAP](https://nap.nationalacademies.org/read/14396/chapter/38)).
- A wayfinding method (Garvey 2006) uses 1 inch per 10 ft for parallel-mounted signs, tied to a 30 degree viewing angle, and 1:30 for perpendicular signs ([source](https://journals.shareok.org/ijsw/article/download/48/51)).
- Vendor charts quote ~1 inch per 10 ft; treat as marketing estimates. Real needs depend on contrast, lighting, speed and viewer vision.
- Not found in search: a 5 arcmin derivation or ISA guidance (not verified).

## Delta category: rediscovered
The 20/40 threshold derivation (~29 ft/inch) lands on the MUTCD 30 ft/inch figure. The 1:10 versus 1:30 split was predicted, though the corpus attributes it to mounting angle (parallel vs perpendicular) rather than my primary explanation of a comfort reserve; both are plausible and likely compound.

## Commentary
Practical B9 rule: quote 1:30 as the hard ceiling (highway/perpendicular, 20/40 viewer) and 1:10 as the design default for flat/parallel storefront and community signage; state which in proposals. The 1:10 vendor figure is a convention, not a measured limit. Confidence is moderate: the corpus search was one standard query and vendor sources are weak.
