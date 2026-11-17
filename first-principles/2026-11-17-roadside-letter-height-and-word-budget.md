# First-Principles Spike — 2026-11-17

**Question:** How tall must letters be on a roadside community sign (e.g. a Lennar 4x8 frontage sign) for a driver at speed V to read it — and how many words can a fixed 4x8 panel actually carry at 45 mph?

**Delta category:** rediscovered (with a novel operational extension)

---

## 1. First-principles answer (written before any search)

**Primitive 1 — the eye.** 20/20 acuity resolves about 1 arcminute of detail. A capital letter is roughly 5 stroke-widths tall, so at the legibility threshold a letter subtends ~5 arcmin.
h = D · tan(5′) = D · 0.001454 → **1 inch of letter height per ~57 ft** at threshold.

Threshold is not design. Real drivers are older (20/40 is common and still legal), the sign is glanced at not studied, contrast is imperfect, there is glare and motion, the font is not a Snellen optotype. A 2× safety margin is the minimum honest one → **design legibility ratio ≈ 25–30 ft per inch.**

**Primitive 2 — time.** The driver does not need to read the sign *at* some distance; they need to *finish* reading it while it is still readable and while there is still room to act. Total time needed:

t = t_detect + t_read + t_maneuver

- detect/orient: ~1 s
- read: people read glanced text at roughly 3 words/s at best → n/3 s for n words
- maneuver (decide, signal, slow, turn into the community): ~3 s

So t ≈ 4 + n/3 seconds. At V mph the car covers 1.47·V ft/s, so the required viewing distance is

**VRD = 1.47 · V · t**, and **h = VRD / LI** with LI ≈ 30 ft/in.

**Primitive 3 — geometry (setback).** A frontage sign is offset laterally from the driver's lane (say 40 ft). As the car closes in, the viewing angle grows; past ~20° off the line of travel the driver stops reading (it would mean turning the head away from the road). So reading must *end* at setback / tan(20°) ≈ 110 ft before the sign. That distance is dead — it adds directly to VRD.

**Primitive 4 — the panel is fixed (the closure).** Letter height depends on word count (through t_read), but word count is also bounded by panel area at that letter height. A character with spacing and leading occupies ~0.6h wide × 1.5h tall ≈ 0.9h². An average word ≈ 6 characters incl. space. Usable area of a 4x8 (48×96 in) after margins ≈ 80% → ~3,700 in².

Solving at 45 mph (66 ft/s), LI 30:

| words n | t (s) | VRD (ft) | cap height (in) | copy area (in²) | fits 4x8? |
|---|---|---|---|---|---|
| 3 | 5.0 | 330 | 11.0 | 1,960 | yes |
| 4 | 5.3 | 352 | 11.7 | 2,970 | yes |
| 5 | 5.7 | 374 | 12.5 | 4,200 | no |
| 6 | 6.0 | 396 | 13.2 | 5,650 | no |

Add the 110 ft setback penalty and n = 4 also breaks (h ≈ 15.4 in, ~5,100 in²); n = 3 barely fits.

**Conclusion (first principles):**
1. Design letter height ≈ 1 in per 25–30 ft of *required* viewing distance, and required distance comes from speed × time, not from where the sign happens to be.
2. A 4x8 frontage sign on a 45 mph road carries a **primary message of ~3–4 words at ~12–15 in caps**. Everything else (phone, URL, "from the $300s") is secondary copy for stopped or slow traffic and should be designed as such, not as part of the drive-by read.
3. Word count is the expensive variable: each extra word costs reading time *and* panel area, so cost of copy is super-linear in words.

---

## 2. Corpus answer (searched after)

- **USSC (United States Sign Council) on-premise legibility method:** reaction time = detect + read + maneuver; reaction distance = mph × 1.47 × seconds; letter height = distance ÷ legibility index. LI ≈ 30 ft/in is the commonly cited baseline (also the FHWA/MUTCD figure), adjusted by font, contrast and illumination; ~0.5 s per five-letter word reading allowance; all-caps needs ~15% more height than mixed case; high-complexity scenes multiply LI by ~0.67.
- **Sign-shop rule of thumb:** "1 inch per 10 feet for best impact," with max readable distance much farther; some highway references cite 1 in per 40 ft for non-Interstate signs.
- USSC also publishes sign-area guidance derived from letter height and copy/negative-space ratios (not verified against the primary PDF this run).

## 3. Delta

**Rediscovered.** Starting from acuity (5 arcmin), driver time budget and speed, the derivation lands on exactly the USSC structure: VRD = 1.47·V·t, h = VRD/LI, LI ≈ 30. The 57 ft/in threshold with a 2× margin reproduces the LI≈30 standard.

**Where the derivation adds something (novel framing, low confidence it's absent from the full USSC text):**
- **The word-budget closure.** The corpus treats copy as an input and solves for letter height (or sign area). Framing it the other way — *for a fixed stock panel (4x8) at a given road speed, what is the maximum word count?* — turns the formula into a sales/design rule Brand 9 can use directly: **4x8 @ 45 mph ≈ 3–4 primary words.**
- **Setback as dead distance.** Lateral offset converts into ~setback/tan(20°) ft of unusable approach that adds to required VRD. USSC may include an offset adjustment; secondary sources didn't surface it.

**Mild corpus critique:** the "1 in per 10 ft" shop rule is speed-blind and ~3× more conservative than LI 30. It's fine for storefronts and pedestrians, misleading for roadside frontage — it says nothing about how much copy fits.

## 4. Commentary

Reasoning got the structure and the constant right without retrieval; retrieval's value was confirming the constant (LI 30) and supplying adjustments (caps +15%, complexity ×0.67) that first principles would only estimate. The derivation's value was reframing the formula around the constraint the business actually faces (a fixed panel), which the orthodox write-ups don't lead with.

Actionable for B9 / Lennar decks: when a community frontage 4x8 faces a 45 mph road, push back on long copy — hero line ≤ 4 words at ≥ 12 in caps; demote everything else.

Sources (step 3): USSC Guideline Standards for On-Premise Signs (usscfoundation.org, 2018), Signs of the Times "USSC best practices," Signazon letter-height chart, signs.com rule-of-thumb post, NIST TN 1180 (letter size vs. viewing distance).
