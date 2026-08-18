# First-Principles Spike — 2026-08-18

## Question
Why do commercial sign codes (monument/pylon signs) scale the *allowed* sign height and area with road speed and/or setback distance, instead of applying one flat citywide size cap? What is the underlying causal relationship between sign size, road speed, and legibility?

*(Self-generated — the backlog was empty. Chosen as directly relevant to Brand 9 Signs' operating domain: on-premise commercial signage.)*

## First-Principles Answer (derived before any search)

**1. What a roadside sign is for.** It transmits a small packet of information (business name, sometimes a short offer) to a *moving* observer with enough lead time to notice, read, decide, and act (turn, change lanes) before the decision point. This is a communication-under-a-deadline problem.

**2. The deadline is set by speed.** Time available = distance-of-first-legibility ÷ speed. If legibility distance were fixed by a flat size cap, the *reading time budget* shrinks in direct proportion to speed — a flat rule silently punishes fast roads.

**3. Legibility distance is linear in letter height.** From small-angle optics, θ ≈ letter_height / distance. Reading (not mere detection) requires θ to stay above some roughly constant threshold θ_min set by human perception and divided attention while driving. So distance_legible = letter_height / θ_min — a straight-line relationship with a perceptual constant, not a policy choice.

**4. Combine 2 + 3.** For a constant reading-time budget T, required distance D = speed × T, and required letter_height = θ_min × D = θ_min × T × speed. **Required letter/sign height scales roughly linearly with design speed.**

**5. Area is a weaker, secondary constraint.** If proportions hold, area grows ~height² — but regulators cap area more conservatively than the physics alone implies, because area is also bounded by an independent externality (visual clutter) that doesn't care about road speed. Expect codes to regulate *height* on physics grounds and *area* more conservatively on aesthetic/clutter grounds.

**6. Setback is a proxy, not the cause.** Setback affects sightline geometry directly (taller sign needed to clear medians/traffic at greater lateral offset) but its bigger role is administrative: setback correlates with road class/speed in typical zoning (arterials get bigger setbacks), so codes use the easy-to-measure, on-the-plat variable (setback) as a stand-in for the real, hard-to-adjudicate variable (available reaction distance / sightline).

**7. Economic reinforcement.** Slow local streets give ambient exposure — a big sign there buys little marginal benefit against a real clutter externality. Fast arterials give almost none — a business must be seen and decided upon in seconds, so a larger sign earns its externality. Speed/setback-scaled caps approximate this efficient trade.

**Predicted shape of the rule:** height allowances keyed roughly linearly to speed/road-class tier or to setback as its proxy; area capped more conservatively and independently for clutter reasons.

## Corpus Answer (found after reasoning, via search)

- **United States Sign Council (USSC) / Pennsylvania Transportation Institute research** is the actual industry standard behind on-premise sign legibility: legibility distance is governed by a **Legibility Index (LI)**, expressed in feet of viewing distance per inch of letter height. The commonly cited rule of thumb is **~10 feet of readable distance per inch of capital letter height** (e.g. a 24" letter ≈ readable at ~240 ft) — i.e. **legibility distance is a linear function of letter height**, exactly the Primitive-3 relationship, with an empirically fixed constant rather than a derived one.
- Real municipal codes tie sign **height directly to setback**, not to letter-height physics explicitly — e.g. Phoenix: height may increase 1 ft per 12 ft of additional setback from a signal, up to a district max; Citrus Heights, CA: height may increase 1 ft per 1 ft of additional setback, capped at 12 ft. This matches Primitive 6: setback is used as the administrable lever, not speed itself.
- Some jurisdictions tie **area directly to speed/road classification** — e.g. one code doubled allowable sign square footage on arterial roads posted ≥35 mph. Others (Cumming, IA) scale area allowance with setback in stepped tiers (1 sq ft/linear ft of building frontage under 250 ft setback, 1.5 above that, 2 beyond 500 ft) — a stepped, roughly-linear proxy formula rather than a clean physics-derived curve.

## Delta

**Category: rediscovered**

The reasoning chain independently arrived at the two load-bearing facts the corpus encodes: (a) legibility distance is a *linear* function of letter height with a roughly fixed perceptual constant (matches USSC's ft-per-inch legibility index almost exactly in form, though the specific constant — 10 ft/in — wasn't and couldn't be derived from optics alone without an empirical measurement of θ_min), and (b) setback functions as an administrable *proxy* for the real causal variable (available reaction/sightline distance) rather than being causal itself, which is exactly how real zoning ordinances use it (height-per-setback-increment formulas, not height-per-speed formulas). The predicted asymmetry — height regulated closer to the physics, area capped more conservatively for independent clutter reasons — also shows up as observed practice (stepped/tiered area formulas rather than quadratic ones).

## Commentary

The value of first-principles reasoning here wasn't inventing a new fact — the USSC's number is empirical and not something optics alone gives you — it was **predicting the right functional form and the right role for each regulatory variable before seeing any code**. Getting "distance is linear in letter height" and "setback is a proxy, not a cause" right in advance means the reasoning chain, not just the memorized fact, is trustworthy — which is the actual asset for future signage-code work (e.g. reasoning about a jurisdiction Brand 9 hasn't seen yet, or sanity-checking a proposed sign against a code that's silent on some edge case). The one place reasoning alone was insufficient: the specific numeric constant (10 ft/in) is an empirical fact about human perception under real driving conditions, not something derivable from clean-room optics — a reminder that first-principles reasoning nails structure/relationships but still needs a measurement to pin down constants.
