# First-Principles Spike — 2026-11-18

**Question:** What letter height does a roadside sign (for example a Brand 9 community-entrance 4×8) need for a driver to read it? Derive it from vision and motion, not from sign-industry charts.

*(The backlog file did not exist, so it was created and this question was generated from current Brand 9 work: builder signs read from moving cars.)*

## First-principles answer (written before any retrieval)

**Primitives.** A sign is read when the eye can resolve the strokes of its letters, for long enough to take in the message, before the viewer has passed the point where the sign is still usable. So the variables are: (1) the eye's resolving angle, (2) how big a letter is compared with its finest detail, (3) the viewer's speed and how long reading takes, (4) the geometry of passing by.

**1. Acuity sets the threshold.** 20/20 vision resolves about 1 arcminute. A Snellen-style letter is about 5 stroke-widths tall, so a letter you can just make out takes up about 5 arcminutes. tan(5′) ≈ 0.00145, so the cap height at threshold is h ≈ D/690. That is **about 1 inch of letter for every 57 ft** for a young 20/20 eye under ideal contrast.

**2. Real viewers are worse than the threshold.** Many drivers are older, with 20/30 to 20/40 vision. That halves the threshold: about 1 in per 29 ft at 20/40. Threshold also means 50% recognition, and comfortable reading of words at a glance needs about 1.5–2× more angle. Weather, glare, low contrast and condensed or thin fonts take another ~1.5×. Multiply them together and the design value lands at **about 1 in per 15–30 ft**. Industry's "1 inch per 10 ft" would then be a conservative rule of thumb that carries roughly a 3–6× safety factor over the acuity threshold.

**3. For a moving viewer, the primitive is seconds, not feet.** The question is not "how far away can it be read" but "how far away *must* it be read". Required distance D = v × (t_detect + N_words × t_word + t_decide/maneuver). At 45 mph (66 ft/s), with 0.5 s to detect, 6 words at ~0.4 s each (2.4 s), and 2 s to decide and turn, t ≈ 5 s and D ≈ 330 ft. At ~30 ft/in that needs **about 11 in letters**. A 4×8 community-entrance sign with 4–5 in copy is unreadable to that driver, however "legible" the letters look.

**4. Offset geometry cuts the window.** A sign set back laterally L from the driver's line of travel can't be read once the viewing angle passes about 10–20° off axis (the driver won't turn their head that far, and letters foreshorten). Reading has to finish at x_min ≈ L / tan(10°) ≈ 5.7L before the sign. A sign 50 ft off the road loses its last ~285 ft, so the read has to *start* at 330 + 285 ≈ 615 ft. That nearly doubles the letter height again. Setback is the hidden multiplier, and it argues for perpendicular (V-shape or double-faced) placement over parallel placement.

**5. Message length scales letter height linearly.** Since D ∝ N_words, every extra word on a roadside builder sign raises the required letter height (and so the face area ∝ h² × characters). Cost grows roughly with the square of the word count at fixed speed. The economic primitive: **cut words before you buy square feet.**

**Prediction for corpus:** a rule of thumb of 1 in per 10 ft (or a "legibility index" of 25–40 ft per inch, depending on font, case and contrast), plus a reading-time formula for vehicular viewing. I expect the corpus to treat setback/viewing angle as a secondary note, not as a multiplier.

## Corpus answer (retrieved after the derivation above)

- **USSC method (United States Sign Council):** viewer reaction distance = speed (ft/s) × total viewer reaction time, then letter height = distance ÷ legibility index (LI). Their worked example: 40 mph in a complex environment gives a **9 s** reaction time, a 531 ft distance, and with LI 31 (black Clarendon on white) a **17 in** letter height.
- **Legibility index values:** about 30–40 ft per inch, depending on font, case, colour and lighting. The Access Board found ~35 ft/in suits average older and younger observers. A Sign Research Foundation paper uses 40 ft/in. A common shop rule is 30 ft/in, and the "1 in per 10 ft" rule of thumb also circulates.
- **Offset and orientation:** the USSC treats this as central, not secondary. Its cone of vision is ±10° (20° total). Parallel signs get their own legibility-index formula that includes the number of lanes and the lateral offset. Garvey (2006) sets the minimum observation angle at **30°** for parallel signs because of foreshortening, and a field study measured 27.75° while driving and 16.14° while walking. Perpendicular signs read better than parallel ones.

Sources: USSC Guideline Standards for On-Premise Signs (2018), usscfoundation.org; Signs of the Times, "The USSC's Best Practices Standards"; US Access Board VMS legibility research; Sign Research Foundation, *Arts and Science of Sign Design*; International Journal of Signage and Wayfinding (shareok.org).

## Delta category: **rediscovered**

The structure is the same as the USSC's: speed × reaction time → distance, then distance ÷ feet-per-inch → letter height, with offset geometry on top. The acuity derivation predicted a design LI of about 15–30 ft/in, against the corpus's 30–40. That is the same order, with mine somewhat conservative.

## Commentary

**What the reasoning got right**
- Seconds are the real primitive, and distance is derived from them. This is exactly the USSC's "viewer reaction time" framing.
- Lateral offset and orientation act as a multiplier, and perpendicular signs beat parallel ones. The USSC has a separate parallel-sign formula built on this.

**Where it missed**
- **Reaction time was too short.** I used 5 s; the USSC uses ~9 s for a complex 40 mph environment. Detection and deciding to act in traffic take far longer than reading the words. Armchair reasoning underestimates the human-factors overhead.
- **Angle limit:** my 10–20° readable-angle guess was really the *cone of vision* (detection). The corpus separates detection (±10°) from the foreshortening limit for parallel signs (~30° observation angle). Two distinct angles got merged into one.
- **The prediction about the corpus was wrong.** I expected offset to be a footnote, but it has its own formula. Don't assume the corpus is shallow where your own reasoning felt clever.

**What survives as useful framing**
Two points I did not see stated in the retrieved sources:
- Required letter height grows linearly with word count, and face area (and cost) grows roughly with its square.
- For B9 builder signs, **cut the word count before adding square footage**.

This is a sales lever, not new science. A 6-word 4×8 at a 45 mph frontage needs letters around 15–18 in on the USSC numbers, which no 4×8 holds. The honest pitch is either fewer words or a bigger face.
