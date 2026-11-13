# First-Principles Spike — 2026-11-13

## Question
Is price-per-square-foot the right pricing primitive for flat printed signs (coroplast, aluminum composite, PVC — Brand 9's core product)?

## First-principles answer (written before any retrieval)

**Start with what a sign costs to make.** Strip the job to its physical and human inputs:

1. **Fixed per-job cost (F).** File intake, prep, proofing, customer back-and-forth, order entry, machine setup, packing, invoicing. None of this changes with size. A 12x18 yard sign and a 4x8 banner take about the same proof cycle.
2. **Area cost (a·A).** Ink and laminate scale with printed area. Printer time on a flatbed scales roughly with area too.
3. **Perimeter / shape cost (p·P).** Cutting and routing scale with cut length, not area. A die-cut shape with a complex outline costs much more to cut than a rectangle of the same area. Grommets and edge finishing scale with perimeter.
4. **Substrate cost, quantized by the sheet.** You don't buy substrate by the square foot; you buy 4x8 sheets (32 sq ft). What a piece really costs is *sheet cost ÷ pieces per sheet*, not *area × rate*. That makes it a step function of dimensions:
   - 18x24 (3 sq ft): 10 per sheet (24" across the 48" side → 2; 18" along the 96" → 5) = 30 of 32 sq ft used, **6% waste**.
   - 24x36 (6 sq ft): 4 per sheet either way = 24 of 32 sq ft, **25% waste**.
   - 4x4 (16 sq ft): 2 per sheet, 0% waste. 3x5: 1 per sheet plus offcut, **~53% waste** unless the offcut is resold.
   So two signs with the same area can differ a lot in true substrate cost depending on how they nest.
5. **Per-unit hardware and logistics.** Stakes, posts, frames and install trips are counted per sign. Shipping moves on dimensional-weight and oversize thresholds (e.g. above about 48" on a side), again steps, not a smooth curve.

So **true cost ≈ F + a·A + p·P + S(dims)/yield + h·N + shipping step**. Price-per-sq-ft captures only the a·A term.

**What follows from that:**
- **Small signs are undercharged** by a flat sq-ft rate, because F dominates. A shop pricing at $X/sq ft *must* add a minimum order or a setup fee, or it loses money on one-off small signs.
- **Large signs are overcharged** relative to cost, because F is spread thin. Competitors who see that will undercut on big pieces, so sq-ft rates should fall with size (tiering).
- **Quantity discounts aren't generosity.** They are F amortizing across N, so price per unit should follow roughly F/N + marginal cost: a hyperbola that flattens out, not straight percentage tiers.
- **Odd sizes should cost more per sq ft** when they nest badly. A 24x36 deserves a higher sq-ft rate than an 18x24 on sheet substrate. Rolled media (banner, vinyl) instead quantizes on *roll width*, the same logic in one dimension.

**Then why does sq-ft pricing exist at all?** Because cost isn't the only primitive. The price also has to be *legible to the buyer and fast to quote*. Square feet is a single number the buyer can compute and compare across shops. It turns "how much is a sign" into multiplication, which makes quoting quick, and in a business where quote speed wins jobs (builders, real estate) that matters. Sq-ft pricing is a **communication protocol** that sits on top of the cost structure, not a model of it.

**And the value side:** the customer isn't buying square feet. A builder's model-park sign is worth whatever it does for lot sales; a real-estate yard sign is worth the leads it drives. Value is set by *the function* (wayfinding, compliance, lead capture, brand), which barely depends on area. So the sq-ft rate is a floor-setting tool at best. Margin is in value-tier packaging (e.g. "community launch kit") where area is invisible.

**Prediction for what the corpus will say:** the industry quotes per sq ft, plus minimums/setup fees, plus size and quantity tiers. Pricing advice will push "know your costs + charge for value." I expect the **sheet-yield step function** to be under-discussed in sign-pricing literature (though known as "imposition/nesting" in print production).

**Answer:** No, not as the *cost* primitive. The cost primitive is **(fixed job cost, sheet yield, cut length, unit count)**. Sq ft is the right *quoting interface* only when wrapped with (a) a per-job minimum, (b) a tiered rate that falls with size, and (c) a yield surcharge or standard-size catalog that steers buyers to sizes that nest well. The best version: sell **standard sizes chosen for yield** at fixed prices, and quote custom sizes per sq ft with a minimum.

## Corpus answer (retrieved after the derivation above)

Practitioner sources (Signs101 forum threads, Sign Warehouse's pricing guide, 4over4 vendor guides) agree on:
- **Base + area.** A per-sq-ft material rate plus a base or setup charge for fixed labor. Typical figures: about $5–15/sq ft and a $25–$87.50 shop minimum, with some shops setting the minimum at one hour of labor.
- **Sq ft misprices small or detailed work.** Forum posters note that "one sq ft of 3" Helvetica is not one sq ft of 3/4" Times Roman," and some shops price cut vinyl per linear inch or per item. That is the perimeter/cut-length term, found independently.
- **Quantity breaks are setup amortization.** 4over4 says outright that setup is a fixed charge spread across the run, with the steepest per-sign saving on the first jump in quantity. That matches the F/N hyperbola.
- **Sheet pricing exists in practice.** One order form offers price per sq ft *or* per 48x96 sheet and pushes whole-sheet orders. A forum post notes that 16"-tall yard signs give 12 per sheet instead of 10. So practitioners know about yield. It is just rarely written up as a *pricing* principle; it lives in shop know-how and imposition/nesting software.

Sources: [Signs101 – minimum charges](https://signs101.com/threads/minimum-charges.60212/post-649566), [Signs101 – minimum charge on small jobs](https://www.signs101.com/threads/minimum-charge-on-small-jobs.76355), [Signs101 – how to price efficiently](https://signs101.com/threads/how-to-price-efficiently.60503/), [Sign Warehouse – basic guide to pricing signs](https://signwarehouse.com/blogs/content/a-basic-guide-to-pricing-signs-banners-and-signs), [4over4 – coroplast costs, stakes and quantity breaks](https://v2.4over4.com/guide/coroplast-yard-sign-costs-stakes-and-quantity-breaks), [Signs101 – coro sheet cost / yield](https://www.signs101.com/threads/poly-coated-cardboard.58546/latest).

## Delta category: **rediscovered** (with a small novel sliver)

## Commentary
The derivation reached the orthodox answer independently: sq ft + minimum + quantity tiers, and that area alone misprices detailed or small work. All of these appear in the corpus. The parts that are *not* stated clearly anywhere in what I found:
1. **Sq ft is a communication protocol, not a cost model.** It exists for buyer legibility and quote speed, and that is why it survives despite being wrong about cost.
2. **Choose the standard-size catalog for sheet yield.** 18x24 nests at 94%; 24x36 at 75%. Practitioners know that 16" yard signs give 12 per sheet, but I didn't see anyone turn that into "price per sq ft should vary by nesting efficiency" or "pick catalog sizes by yield."

Actionable for Brand 9: check the shop's standard sizes against 4x8 yield and either (a) add a small surcharge per sq ft on poor-yield sizes or (b) steer buyers toward high-yield sizes. This lines up with the existing `b9-partner-sheet-economics` practice (whole sheets vs custom pieces on Signs365).

Confidence: 0.7. The corpus check rests on forum and vendor sources, not a systematic survey.
