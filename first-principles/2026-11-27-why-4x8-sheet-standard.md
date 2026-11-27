# First-Principles Spike — 2026-11-27

## Question

Why is 4x8 ft (48" x 96") the standard sheet size for sign substrates (coroplast, PVC, ACM, plywood, HDU), and which common sign sizes does it actually favor? What does that mean for how Brand 9 should price and size signs?

*Backlog was missing, so this question was generated for the run. It ties to signage-industry basics and to Brand 9's partner-sheet economics (whole 4x8 sheets vs custom pieces).*

---

## First-principles answer (reasoned before any lookup)

**Primitives.** A sheet good is made in a mill, shipped, carried by people, cut on a machine and used in a product. Each step limits the size, and the standard is whatever fits all of them, picked once and then locked in.

1. **The human body.** A sheet must be carried by one or two people with no lifting gear. A person can hold a panel by its edges with arms about 4 ft apart. The length is limited by balance and by wind: an 8 ft panel stands about as tall as a doorway or a ceiling, so one person can tip it upright and walk it. A 5x10 sheet needs two people, and a 10 ft length won't turn through most doors or stairwells. So the width is set near 4 ft by arm span, and the length near 8 ft by height and doorways.

2. **The building.** Sheet goods started in construction, not signage. Wall framing is spaced 16" or 24" on center, and ceilings are about 8 ft high. A sheet whose sides are multiples of 16 and 24 (48 = 3x16 = 2x24, 96 = 6x16 = 4x24) lands its edges on framing members with no cutting. Then 4x8 covers one floor-to-ceiling wall bay with no waste. The building module and the body limit point to the same number, which is why it stuck.

3. **Transport.** A legal US trailer is 102" wide. Two 48" sheets sit side by side with room for straps. A pickup bed is about 48–50" between the wheel wells, so a 4x8 lies flat. Pallets and forklift forks are sized around the same footprint. Each of these was then built around the sheet, which reinforces it.

4. **Lock-in.** Once mills, trucks, racks, saws and CNC beds are built for 48x96, any new material (coroplast, PVC foam board, ACM) is made at 4x8 so it fits existing shop equipment. So sign substrates use 4x8 because of carpentry, not because of signs.

**Corollary: the causality runs from the sheet to the sign.** If the sheet came first, common sign sizes should be the ones that divide 48x96 cleanly. Predictions:
- 24x24 → 8 per sheet, 100% yield. ✔ divides cleanly
- 18x24 → 24 on the 48 side (2), 18 on the 96 side (5, 6" left) → 10 per sheet, 93.75%. ✔ near clean
- 12x18 → 4 x 5 = 20 per sheet, 93.75%. ✔
- 4x4 and 4x8 → exact. ✔
- **24x36 → 2 x 2 = 4 per sheet, 72" of 96" used → 75% yield.** ✘ This breaks the prediction. A 24" x 24" strip is left on every sheet.

So the hypothesis is only partly right. Most yard-sign sizes tile the sheet, but 24x36 (one of the two best sellers) wastes a quarter of the sheet. It can't be a sheet-derived size. It must come from elsewhere: poster and architectural paper sizes (24x36 is the US Arch D sheet and a standard poster size), meaning the print and frame world, not the carpentry world. The customer's sense of a "normal" sign size comes from posters, and the shop's costs come from plywood. Those two standards collide at 24x36.

**Pricing implication.** The real cost driver for a cut-sheet sign is the fraction of a sheet it uses up, not its square footage. Pricing per square foot undercharges 24x36 (it takes 1/4 of a sheet but covers only 1/5.33 of the area) and overcharges sizes that tile cleanly. Ways to handle it:
- price per sheet fraction (1/10, 1/8, 1/4, 1/2, 1),
- fill the waste strip: a 24x36 order of 4 leaves a 24x24 strip, which is exactly one 24x24 sign or two 12x24 riders, so offer it as a matched add-on,
- or nudge buyers to 24x32 (6 per sheet, 100%) when the exact size isn't fixed.

This is a guess from geometry. It assumes no bleed, kerf or trim margin, which push real yields down.

---

## Corpus answer (looked up after)

- Standard 4x8 plywood sheets entered the US market in **1928** (Wikipedia, *Plywood*). No authoritative source gives the *reason* for the size.
- The common explanations are (a) it's about the largest panel one worker can handle and install alone, and (b) **an 8 ft sheet spans 16" on-center studs cleanly** (engineerfix, Bob Vila, Hunker). These are stated as practical facts, not documented history.
- Older or other sizes existed (5x5 Baltic birch, which is metric; 5x9 anecdotally). There's an unverified claim that Portland Manufacturing showed 4x8 panels at the 1905 Lewis & Clark fair.
- Sign vendors (4OVER4, SinaLite) list standard coroplast sizes as 12x18, 18x24, 24x24 and 24x36. 18x24 and 24x36 are the most popular. **No vendor source discusses sheet yield**, and none says that 24x36 wastes 25% of a 4x8.

Sources: [Wikipedia — Plywood](https://en.wikipedia.com/wiki/Plywood) · [engineerfix — full sheet size](https://engineerfix.com/how-big-is-a-full-sheet-of-plywood/) · [Bob Vila — plywood sizes](https://www.bobvila.com/articles/plywood-sizes-and-types.md) · [Hunker — standard plywood sizes](https://www.hunker.com/12464023/what-are-standard-sizes-of-plywood) · [EcoModder post (unverified 1905 claim)](https://ecomodder.com/forum/511429-post17.html) · [4OVER4 — coroplast sizes](https://www.4over4.com/help/signs/what-sizes-are-available-for-cheap-coroplast-signs) · [SinaLite sell guide](https://sinalite.com/media/images/pdf/Sell-Guide-CP.pdf)

---

## Delta

**Category: rediscovered** (with one novel sub-finding)

- The origin of 4x8 matched the corpus: one person can handle it, and it lands on the 16"/24" framing module. Reasoning alone found it, and the corpus doesn't do better. The corpus has the date (1928) but no recorded rationale, so on *why* it is folk explanation just like the derivation.
- **Novel sub-finding:** the corpus treats "standard sign sizes" as one family. The derivation splits them into sheet-derived sizes (12x18, 18x24, 24x24, 4x4, 4x8, all ≥93% yield) and a poster-derived one (24x36, 75% yield). No source found prices or sizes signs on that basis.

## Commentary

The derivation was most useful where it *failed*. The "sizes follow the sheet" hypothesis made a prediction that could be checked, and 24x36 broke it. The question "where else could this size come from?" then turned up the two-standards collision. A lookup would have returned the list of sizes without the anomaly, because the list carries no yield data.

**Action for B9 (not done, flagged only):** check how the shop prices 24x36 cut-sheet jobs and whether orders reuse the 24x24 leftover strip. This ties to the `b9-partner-sheet-economics` rules (whole sheets vs custom pieces). Note that partner prices may already include waste, and this run didn't check that.

Confidence: 0.6. The geometry is certain. The historical cause is inferred, and the corpus couldn't confirm it either.
