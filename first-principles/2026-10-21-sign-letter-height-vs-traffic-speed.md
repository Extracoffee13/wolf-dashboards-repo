# Spike 2026-10-21: Why does required sign letter height scale with traffic speed?

## Question
Why does required letter height scale with traffic speed, and by how much?

## First-principles answer (derived before any lookup)
1. Reading needs angular size. The eye resolves about 1 arcmin; a letter needs about 5 stroke-widths, so the bare minimum is about 5 arcmin. A comfortable glance needs about 20-30 arcmin.
2. Legibility distance d = h/theta, which is linear in height. At about 25 arcmin that gives roughly 11 ft of distance per inch of letter height.
3. The driver needs a time budget T: about 0.3 s per word, about 1.5 s perception and reaction, plus time to act (brake, change lane, turn).
4. Required distance D = v*T. At 30 mph (44 ft/s) and T = 5 s, D = 220 ft; at 60 mph, D = 440 ft. So h scales linearly with v and with message length.
5. T grows with speed, because braking distance goes as v^2, so the requirement is slightly worse than linear.
6. Lateral offset L caps the useful range. A sign leaves the roughly +/-10 degree useful cone at about 5.7*L, so size cannot buy distance that offset removes.
7. Motion degrades dynamic acuity, so theta should rise with speed, which steepens the requirement.

Prediction: h ~ v * T(message length) / theta.

## Corpus answer
- The MUTCD legibility index for static road signs is 30 ft per inch of letter height. FHWA calls it conservative (20/40 vision). Letter height is legibility distance divided by that index, with legibility distance set by operating speed and sign placement.
- The common consumer rule of thumb is 1 inch per 10 ft. It is looser, and treated as a starting estimate.
- The USSC Foundation on-premise guideline builds the same chain: viewer speed, reaction/maneuver time (about 4-6 s by roadway type), observation angle, and a letter-height lookup. It also covers glance frequency and a copy-area guideline of about 40% of the panel.
- Projecting signs are readable from farther away at a smaller size than parallel wall signs.

Sources: FHWA 16037/15027 research pages; USSC Foundation Guideline Standards for On Premise Signs 2018; Studio Matrx legibility note.

## Delta: rediscovered
The structure matches: h = (v * T) / index, with a reaction-time budget and an observation-angle cap. My index (about 11 ft/in) matches the consumer rule, not the MUTCD (30 ft/in). Mine is the comfortable-glance threshold; the MUTCD is the worst-case-vision threshold. I did not derive the copy-area and glance-frequency effects, or the parallel versus perpendicular mounting difference. The latter follows from the observation-angle point in step 6 but I did not apply it.

## Commentary
- Confidence in the structural answer is high. The numeric index depends on whose vision is assumed.
- Practical use for Brand 9: quote letter height from D = v*T for the actual road speed and message word count, and flag the 10 vs 30 ft/in range to customers as comfortable versus worst-case.
- Search results were snippets only, and I did not read the USSC tables, so the lookup values are unverified.
