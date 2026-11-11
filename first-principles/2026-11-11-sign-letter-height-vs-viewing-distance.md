# Spike 2026-11-11: How tall must sign letters be for a given viewing distance and traffic speed?

**Why this question:** The backlog file was missing, so this question was generated for the run. It is a basic primitive for Brand 9 Signs: it sets panel size, copy count and price on every builder, frontage and A-frame sign.

## First-principles answer (written before any retrieval)

**Primitives.** A letter is read when its smallest critical detail resolves on the retina, and the reader has the time to process the whole message before the sign leaves usable view.

**1. Acuity bound (static, ideal viewer).** 20/20 vision resolves detail about 1 arcminute across. A Snellen optotype is 5 arcmin tall with a stroke of 1/5 height. So the smallest *just-legible* letter subtends about 5'.
tan(5') ≈ 0.001454, so a 1-inch letter reaches that limit at 1/0.001454 ≈ 688 in ≈ **57 ft per inch of letter height**. That is a ceiling: threshold recognition of an isolated, maximum-contrast character by a young, perfectly corrected eye.

**2. Degradation multipliers (real viewer, real sign).** Each one takes away from the 57 ft/in:
- *Threshold vs. comfortable reading:* Reading words quickly needs about 2–3× threshold size (reading-reserve concept) → ÷2.
- *Age / uncorrected vision:* the population median driver is worse than 20/20; older drivers ~20/40 → another ÷1.2–2 at the tail.
- *Contrast & font:* thin, condensed, script, or low-contrast colour pairs drop it by a further 10–50%. Bold, open sans-serif with dark-on-light or light-on-dark stays close to the ideal.
- *Lighting / glare / motion blur:* night, sun behind the sign, vibration.
Stack the realistic central values (÷2 reading reserve, ÷1.3 population) and you get **≈ 20–30 ft per inch** for a good font at good contrast. For a poor font or colour pair it falls to ~15 ft/in.

So: **design letter height (in) ≈ viewing distance (ft) / ~25**, with 30 as optimistic and 15 as conservative.

**3. Time budget (moving viewer). This is the step people skip.** A driver doesn't read at one distance. They read during a window that closes as the sign leaves the cone of acceptable viewing angle (~10–15° off the line of travel, more for setback). Required read distance:
`D_read = v × (t_detect + t_read + t_decide/maneuver)`
- t_detect ≈ 0.5–1 s, t_read ≈ 0.3 s per word or ~1 s per familiar 3–4 word unit, t_maneuver (slow, change lane, turn) ≈ 3–5 s if action is required.
- At 45 mph (66 ft/s), a 6-word message plus a turn needs roughly (1 + 2 + 4) s × 66 ≈ **460 ft** of read distance. At 25 ft/in → about **18-inch** letters.
- And the sign must be legible from the *far end* of that window: letter height comes from the start of the window, not the average distance.

Corollary: for moving viewers, **word count costs inches**. Each extra word at 45 mph adds ~20–30 ft of required distance → about +1 in of letter height. Cutting copy is usually cheaper than enlarging the sign, because area grows with the square of letter height.

**4. Area corollary for sign sizing.** Copy should occupy ~40–60% of the face (negative space is a legibility input, not decoration). Letter height and character count fix the copy block, and the panel follows from there. That is why a 4×8 builder sign with 10 lines of copy fails: the copy count, not the panel, is the binding constraint.

**Answer:** Letter height (in) ≈ D(ft)/25 for good type and contrast (range /15–/30). For moving traffic, D = speed × (detect + read + maneuver time), and D is measured at the start of the viewing window. The "1 inch per 10 feet" folk rule is not a legibility rule. It is ~2.5× more conservative than the physics needs for a good font. If it is anything, it is an *impact/attention* heuristic.

## Corpus answer (retrieved after the derivation)

**USSC (United States Sign Council) on-premise guideline method:**
1. **Reaction time** = detection (~1 s in a complex environment) + message scan (~0.1 s per letter) + re-orientation (~0.04 s per letter) + maneuver (~5 s if action is needed). Worked example: 23 letters → ~9 s.
2. **Reaction distance** = reaction time × speed (ft/s). Example: 59 ft/s × 9 s ≈ 531 ft.
3. **Letter height** = distance ÷ **Legibility Index**. LI ≈ 30–35 ft/in for good fonts with good contrast (e.g. 31 for black Clarendon on white). All caps needs ~15% more height. Example result: ~17 in.
- **MUTCD** design guidance also uses **30 ft/in**. Older FHWA highway guides used 40 ft/in.
- The **"1 in per 10 ft"** rule is an industry heuristic, not a standard. Ratios vary across vendors (10, 30, 40 ft/in). A Penn State-linked index puts it near 10 ft/in for signs mounted **parallel** to the road (seen at a steep angle) and 30 ft/in for **perpendicular** signs.
- The design literature separates *legibility* (making out the letters) from *readability* (understanding the message).

Sources: [Signs of the Times, USSC best practices](https://signsofthetimes.com/the-usscs-best-practices-standards/) · [USSC Guideline Standards 2018](https://usscfoundation.org/wp-content/uploads/2018/03/USSC-Guideline-Standards-for-On-Premise-Signs-2018.pdf) · [Greenhouse Grower, roadside signs](https://www.greenhousegrower.com/?p=128295) · [IJSW review (shareok)](https://journals.shareok.org/ijsw/article/view/9) · [NAP tutorial (MUTCD 30 ft/in)](https://nap.nationalacademies.org/read/14396/chapter/38) · [Signs.com letter-height guide](https://www.signs.com/blog/?p=16381)

## Delta: **rediscovered**

| Element | First principles | Corpus (USSC/MUTCD) |
|---|---|---|
| Structure | D = v × (detect + read + maneuver); h = D / LI | Identical three-step chain |
| Legibility index | ~25 ft/in central (15–30) | 30–35 ft/in good fonts; MUTCD 30 |
| Read time | ~0.3 s/word | 0.1 s/letter (+0.04 re-orient) ≈ 0.5–0.7 s/word |
| Maneuver | 3–5 s | ~5 s |
| Worked example | 45 mph, 6 words + turn → ~460 ft → ~18 in | 40 mph, 23 letters → 531 ft → ~17 in |
| 1 in / 10 ft rule | "Not a legibility rule; ~2.5× conservative" | Partly explained by **parallel-mount viewing angle** |

## Commentary

- The derivation found the USSC method's exact shape: physical acuity bound, then degradation divisor, then time budget. Numbers landed within ~15%. LI came out slightly pessimistic (25 vs 30). Read time per word came out too optimistic, because USSC counts per *letter*, so long words cost more. The two errors partly cancel.
- **What reasoning alone missed:** I treated the 1-in-per-10-ft folk rule as an unjustified impact heuristic and nearly filed this as corpus-error. The corpus has a geometric explanation I skipped: a sign mounted flat to the road is seen at a sharp angle, so letters look narrower and the viewing window is short. That brings the effective LI down toward ~10. Viewing angle came up in my derivation (the viewing cone) but I never followed it through to letter height. The folk rule is still overused for perpendicular signs and A-frames, so that part of the suspicion holds.
- **What the corpus under-weights (operational, not a category change):** "word count costs inches" and "area grows with the square of letter height" are the most useful levers for B9 sales conversations. USSC has the inputs but presents them as a sizing calculator, not a copy-editing argument. Customer pitch: *cut three words before you pay for a bigger panel.*
- **B9 application:** For frontage signs at 45 mph, size letters as `h_in = speed_ftps × (1 + 0.1·letters + 5) / 30`. Add 15% for all caps. Use LI 10–15 for signs parallel to the road.
