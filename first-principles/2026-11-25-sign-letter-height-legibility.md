# First-Principles Spike — 2026-11-25

## Question
How tall must the letters on a sign be so that the intended viewer can read it, at a given distance or a given speed?

(The backlog file did not exist, so this question was generated. It is the most basic sizing primitive in the signage trade: it decides panel size, which decides material, cost and permit class.)

## First-principles answer (written before any retrieval)

**1. What the eye can resolve.** Normal 20/20 vision resolves about 1 arcminute. The Snellen standard treats a letter as a 5×5 grid of strokes, so the smallest readable letter at 20/20 subtends about 5 arcminutes.
5 arcmin = 5/60 × π/180 ≈ 0.00145 rad. Height = distance × 0.00145, so 1 inch of letter for every 1/0.00145 ≈ 690 inches ≈ **57 ft** of distance. That is the *threshold*: the distance where a perfect eye reading a high-contrast chart can just make out an isolated letter.

**2. Threshold is not legibility.** A sign is not an eye chart.
- Many viewers are not 20/20. Drivers can be licensed at 20/40, and older eyes lose contrast sensitivity. 20/40 halves the distance to about 28 ft/in.
- Real signs have lower contrast, glare, dirt, night lighting and display fonts.
- People read words, not letters, and they do it with a glance, not by staring. Fluent word recognition needs letters well above threshold, roughly 1.5 to 2×.
Taking 57 ft/in and applying a safety factor of about 2 gives **~25–30 ft of distance per inch of letter height** as the practical legibility ratio for a good font with good contrast. Bad conditions (script font, low contrast, thin strokes) push it down toward 15–20.

**3. Moving viewers: the distance is set by time, not by the eye.** For a driver the question changes. "How far away can they read it" stops mattering; what matters is how far away they must *start* reading so they finish in time. The chain:
- Detect the sign and decide to look: about 1–2 s, more in visual clutter.
- Read: about 0.3 s per word, plus about 1 s to take in a logo or symbol.
- Act (brake, change lanes, turn) before passing the sign: about 2–4 s, and the sign leaves the cone of vision before you reach it, since you cannot read at a steep angle.
For a 6-word message at 45 mph (66 ft/s): 1.5 s detect + 1.8 s read + 3 s act ≈ 6.3 s ≈ **415 ft** of required read distance. At 28 ft/in that means letters about **15 in** tall. At 25 mph (37 ft/s) the same message needs about 230 ft, or about 8 in letters.

So the general formula is:
**Letter height (in) = speed (ft/s) × total time (s) ÷ legibility ratio (ft/in)**
where total time grows with word count and clutter, and the ratio shrinks with poor contrast, poor fonts and older viewers.

**4. Corollaries a sign shop can use.**
- Word count is a sizing variable. Halving the copy can shrink the letters as much as halving the speed does. Cutting copy is often cheaper than buying a bigger panel.
- Setback and angle add distance: the sign is read along a diagonal, and the last ~10° before passing is lost.
- Upper and lower case reads faster than all caps at the same cap height, because word shapes help; it also uses less width.
- Contrast and stroke weight multiply the ratio. A thin script on a busy photo can lose half its distance.
- For a pedestrian or a parked shopper (a yard sign, a model-home A-frame) time hardly matters, and the static ratio of 25–30 ft/in decides the size.

**Confidence before retrieval:** high on the threshold arithmetic and on the overall shape (time × speed ÷ ratio). Medium on the exact ratio (25–30) and the timing constants.

## Corpus answer (retrieved after the derivation)

The industry standard is the **United States Sign Council (USSC) on-premise sign guidelines**:
- **Letter height (in) = Viewer Reaction Distance (ft) ÷ Legibility Index (ft/in).** VRD = speed (mph × 1.47 = ft/s) × viewer reaction time (s).
- **Legibility Index ≈ 30 ft/in** is the recommended general value ("will yield correct results in virtually all situations"). The LI varies by font and color pair; one worked example uses LI 31 for Black Clarendon on white: 531 ft ÷ 31 ≈ 17 in.
- **Reaction time** depends on the setting (about 5 s for a town commercial district under 35 mph, more in complex settings). Reading time is about **0.1 s per letter or symbol**.
- **All caps** needs letters about **15% taller** than upper and lower case.
- On highways the MUTCD uses about 30 ft/in. Older FHWA work used 40 ft/in for 20/20 drivers, and the ratio was lowered to cover older drivers.

Sources: [USSC Guideline Standards for On-Premise Signs 2018](https://usscfoundation.org/wp-content/uploads/2018/03/USSC-Guideline-Standards-for-On-Premise-Signs-2018.pdf), [Signs of the Times: USSC best practices](https://signsofthetimes.com/the-usscs-best-practices-standards/), [FHWA research](https://www.fhwa.dot.gov/publications/research/safety/15027/004.cfm), [IJSW: parallel-mounted letter height](https://journals.shareok.org/ijsw/article/view/48)

## Delta — **rediscovered**

The derivation reached the same formula structure as USSC: height = speed × time ÷ legibility ratio. Its ratio (25–30 ft/in, from 57 ft/in at threshold with a safety factor of about 2) brackets the USSC value of 30. It also predicted the all-caps penalty in direction (the corpus puts it at 15%).

Smaller differences:
- **Reading speed:** the derivation used 0.3 s per word, which is faster than USSC's 0.1 s per letter (about 0.5 s for a 5-letter word). It underestimated read time by about 40%, so it would undersize letters for long messages.
- **Threshold anchor:** the corpus's 40 → 30 ft/in history (FHWA for 20/20, lowered for older drivers) matches the derivation's step from 57 (threshold) to 28 (20/40) to about 30 (practical) closely. The acuity arithmetic is the real foundation of the standard.
- **Framing the corpus underweights (not new enough to call novel):** copy length is a sizing lever with the same force as speed. The USSC formula contains it (through letter count in reaction time), but sign buyers are rarely told "cut 4 words and you can drop a panel size." That makes it a sales and design talking point for B9, not a correction to the standard.

## Commentary
The derivation was right where it relied on physics (visual angle) and weakest where it relied on behavioral constants (reading speed, reaction time). Those constants are empirical. They cannot be derived, only measured, and that is exactly where retrieval is worth it. For B9 quoting, use USSC LI 30 and 0.1 s per letter, and pitch copy reduction as a cost lever.
