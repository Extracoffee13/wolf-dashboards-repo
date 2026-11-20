# First-Principles Spike: 2026-11-20

**Question:** How tall must sign letters be to be read at a given distance, and what should a builder model-park sign (4×8 on a 45 mph frontage) use?

**Why this question:** `first-principles-backlog.md` didn't exist, so I created it and generated this question. Letter-height sizing is a basic sizing rule behind every Brand 9 frontage, 4×8 and A-frame quote.

## First-principles answer (written before any retrieval)

**Primitives.** A reader can read a letter when its features are resolvable by the eye, they have time to read the whole message, and contrast is high enough that the features don't wash out.

**1. The acuity limit.** Normal (20/20) vision resolves detail about 1 arcminute wide. A letter is built from strokes and gaps; a capital E is five strokes/gaps tall, so the smallest readable letter is about 5 arcmin tall (that's what an eye chart is designed around). 5 arcmin = 5/60 degree = 0.001454 rad. For small angles, letter height h ≈ d × 0.001454, so d ≈ 688 h. **One inch of letter height is just barely readable at ~57 ft**, under ideal conditions, by a person with 20/20 vision, who is standing still and staring at it.

**2. Threshold is not legibility.** "Barely readable" means a reader can pick out the letters if they try hard. Signs are glanced at, not studied. Three things eat into the threshold:
- *Visual acuity of the population.* Many drivers are worse than 20/20 (older drivers, uncorrected vision); design for about 20/40, which halves the distance → ~29 ft/in.
- *Font and case.* Thin strokes, condensed or script faces, and all-caps strings with no word shapes all raise the angle needed. The ~5 arcmin figure assumes a clean, medium-weight sans with stroke ≈ 1/5 of height. Bold condensed or decorative faces lose maybe 20–40%.
- *Contrast and lighting.* Low contrast (e.g. tan on white, or a backlit sign at dusk) costs more. High contrast (dark on light, or white on a saturated dark) keeps you near the limit.

So a realistic legibility figure is roughly **25–30 ft per inch of capital height** for a good sans-serif in high contrast — and closer to 15–20 ft/in for poor fonts or contrast.

**3. Time to read, for a moving viewer.** A driver doesn't read a sign at a single distance; they read it during a window. Reading time ≈ fixed detect/decide time (~1–2 s) + reading time per word (~0.25–0.4 s a word for short strings, and more for unfamiliar words). Reading has to *finish* before the sign leaves a comfortable viewing angle (roughly 10–20° off the line of travel), and before the driver must act on it (slow down, turn). So the required read distance is:

  D_required = speed × (t_detect + n_words × t_word + t_maneuver) + lateral offset effects

At 45 mph (66 ft/s) with 6 words: 66 × (1.5 + 6×0.35 + 2) ≈ 66 × 5.6 ≈ 370 ft. Divide by 30 ft/in → **~12-inch letters**. At 25 mph inside a community: 37 × 5.6 ≈ 205 ft → ~7-inch letters.

**4. Copy is the real lever.** Required height scales linearly with word count (through reading time) and with speed. Halving the copy from 8 words to 4 drops the time term by ~1.4 s, which can be worth 25–30% of letter height at road speeds. On a fixed 4×8 panel, this is the binding constraint: the panel's area is fixed, so every extra word shrinks every letter *and* adds reading time — a double penalty. That predicts a rule: **on a fixed panel, copy length hurts legibility roughly quadratically, not linearly.**

**5. Setback/angle.** A sign set far off the road is seen at a steeper angle late in the approach. Readers stop reading at maybe 20° off-axis, so the read window closes earlier, which raises the required distance (and therefore letter height) for signs with big setbacks.

**Derived rules of thumb**
- Hard ceiling (ideal eye, stationary): ~55–60 ft per inch.
- Design value for good conditions: ~25–30 ft per inch of capital height.
- Conservative "make it pop": ~10–15 ft per inch.
- For moving traffic, size from the read-time window, not the distance to the sign: D = v × t_total, then h = D / 30.
- Model-park 4×8 at a 45 mph frontage: the community name needs ~12" caps; secondary lines are only worth it if they are ≤ 3–4 words.

## Corpus answer (retrieved after the derivation)

- **Industry rule of thumb:** 1 inch of letter height per **10 ft** gives the "best impact". The maximum readable distance is about **30–40 ft per inch**. Signazon and the Albany NY chart, for example, give 3" letters as best at 30 ft and readable to 100 ft. Readable distance varies by about 10% with color.
- **MUTCD (road signs):** a legibility index of **30 ft per inch** of letter height. FHWA research suggests about **40 ft/in** for drivers with about 20/20 vision.
- **USSC On-Premise Sign Guideline Standards (2003):** letter height = Viewer Reaction Distance ÷ Legibility Index. VRD = speed × Viewer Reaction Time, and the LI varies by font, case and color (roughly in the high-20s to mid-30s for good combinations). The worked example is 59 ft/s × **9 s VRT** = 531 ft, and 531 ÷ LI 31 = 17" letters. VRT covers detection, reading and maneuver, and it grows with copy length and road complexity.

## Delta

**Category: rediscovered**

| Item | First principles | Corpus | Verdict |
|---|---|---|---|
| Hard ceiling | ~57 ft/in (5 arcmin, 20/20) | ~40 ft/in for 20/20 (FHWA) | Same order; the theory is optimistic by about 30% because real glyphs and real contrast fall short of an eye chart |
| Design legibility | 25–30 ft/in | MUTCD 30 ft/in; USSC LI ~30 | **Match** |
| "Pop"/impact | 10–15 ft/in | 10 ft/in | **Match** |
| Moving-viewer method | D = v × t_total, h = D / LI | VRD = v × VRT, h = VRD / LI | **Same structure, found independently** |
| Reaction-time magnitude | ~5.6 s for 6 words | ~8–11 s typical USSC VRT | **Underestimated.** The derivation leaves out search/scan time in visual clutter and the safety margin for a maneuver |
| Copy length on a fixed panel | Quadratic penalty (shorter time window × smaller letters) | Word count sits inside VRT; the fixed-panel coupling isn't stated explicitly | Small **novel** framing, a useful sales argument but not a new law |

## Commentary

The derivation landed on the same structure as the USSC: reaction distance divided by a legibility index, with an LI near 30. That validates reasoning from acuity and time windows. The miss was the size of the time budget. Reasoning from the visual task alone leaves out the *search* phase (finding the sign among the clutter on the frontage) and the decision margin, and those roughly double the reading time. For the model-park case this changes the answer. At 45 mph (66 ft/s) with a 9 s VRT the reaction distance is about 594 ft, so caps should be **about 20"**, not 12". A 4×8 can only fit that for a 1–2 word community name, which supports the fixed-panel "copy is the real lever" point. Practical rule for B9 frontage quotes: size the hero line from USSC VRT (not from the distance to the sign), and cut secondary copy to ≤ 4 words.

**Confidence:** 0.75. Corpus values for USSC VRT/LI were retrieved secondhand, not from the 2003 PDF itself.

**Sources:** [Signs of the Times: USSC best practices](https://signsofthetimes.com/the-usscs-best-practices-standards/) · [FHWA 15-027](https://www.fhwa.dot.gov/publications/research/safety/15027/004.cfm) · [Signazon letter height chart](https://signazon.com/help-center/sign-letter-height-visibility-chart.aspx) · [Albany NY sign size chart](https://selfservice.albanyny.gov/sites/default/files/AV0095%20-%20APP%20-%20Sign%20Size%20Recommendation%20Chart.pdf) · [National Academies](https://nap.nationalacademies.org/read/14396/chapter/38)
