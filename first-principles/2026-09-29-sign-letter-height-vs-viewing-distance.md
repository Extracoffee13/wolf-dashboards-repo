# First-Principles Spike — 2026-09-29

## Question
Why does readable sign distance scale linearly with letter height, and where does the "1 inch of letter height per 10 feet" rule come from?

## First-principles answer (derived before any lookup)
Primitives: a letter is a pattern the eye must resolve; the eye resolves angles, not sizes; a letter's apparent size is the angle it subtends.

1. Angle subtended by a letter of height h at distance d is θ = 2·atan(h/2d) ≈ h/d for small angles. So for a fixed required angle θ*, d = h/θ*. Linear in h by geometry alone; the constant is 1/θ*.
2. What is θ*? Legibility requires resolving the letter's internal detail (stroke width, gaps in an "e" vs "c"). Normal (20/20) acuity resolves about 1 arcminute. A letter needs roughly 5 strokes/gaps across its height, so the minimum letter height is ~5 arcmin (this is the Snellen optotype design).
3. 5 arcmin = 5 × 2.909e-4 rad = 1.454e-3 rad. So d_max = h / 1.454e-3 ≈ 688·h. One inch of height → ~57 ft at the bare threshold, for perfect contrast, unlimited viewing time, 20/20 eyes.
4. Real viewing is worse than threshold: contrast is imperfect, the viewer is moving (time-limited), older eyes are ~20/40 (2x), glare/clutter, reading a word not a single letter, and people need margin to decide and act. Multiply required angle by roughly 4-7x. 688/6 ≈ 115 → about 1 inch per 10 ft (120x).
5. So the "10 ft per inch" rule is not a legibility limit; it is a comfortable-reading figure, roughly one sixth of the threshold. Threshold-ish "just readable" would be ~1 inch per 50 ft; a fast-driver sign needs more margin (~1 inch per 3-5 ft).
6. Consequences: (a) the rule is linear only in the small-angle regime, fine for signs; (b) the constant is a policy (safety margin), not physics; (c) the constant should shrink with speed, age, low contrast, and lit-vs-unlit; (d) the ratio is about cap height, and stroke width/spacing matter because they set the resolvable detail.

## Corpus answer
Trade sources (Signazon, Signs.com, SGS, Excel KC, VisualPro, USSC-derived tables) all give 1 inch of capital letter height per 10 ft of viewing distance as the standard on-premise legibility index, attributed to United States Sign Council research. Several add 1 inch per 25-50 ft for maximum/threshold reading and about 1 inch per 4 ft for at-a-glance comfort. Some sources describe 10 ft/inch as the point where a letter is "just readable".

Sources: https://www.signs.com/blog/signage-101-letter-height-visibility/ , https://www.signazon.com/help-center/sign-letter-height-visibility-chart.aspx , https://excelkc.com/blog/calculate-sign-letter-size/

## Delta category
**rediscovered** — linear scaling, the acuity mechanism, and the ~10 ft/inch constant all match once a safety factor is applied.

## Commentary
- Derivation adds the why the corpus omits: the constant is a margin over the ~57 ft/inch acuity threshold, not the threshold itself.
- Mild corpus inconsistency: sources calling 10 ft/inch "just readable" contradict their own 25-50 ft/inch max figure. Physics supports 10 ft/inch as comfortable. Not strong enough to label corpus-error (definitions of "readable" vary).
- Practical use for B9: for a given install distance, the derivation lets us adjust letter height for speed/age/contrast instead of applying one fixed ratio (e.g., highway monuments deserve the 1:3-5 ft ratio).
