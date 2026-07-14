# First-Principles Spike — 2026-07-14

## Question

Why does the sign industry price illuminated channel letters primarily by **letter height** (e.g., "$X per inch") rather than by the total square footage of the sign face, even though letters of the same height can differ a lot in width and complexity (a "W" vs. an "I")?

Backlog file was missing on this run (`first-principles-backlog.md` did not exist in the repo), so this question was self-generated as relevant to Brand 9 Signs operations, and a starter backlog was seeded for future spikes.

## First-Principles Answer (derived before any search)

Start from the physical build of a channel letter: an aluminum "can" (the back and the side wall, called the *return*), a plastic *trim cap* running the perimeter, an acrylic face, LED modules mounted inside, wiring, a power supply, and install labor to mount and hook up each letter.

Ask which of these scale with **height** and which scale with **area**, holding the font/design fixed:

1. **Return depth** (how deep the aluminum side wall is) is set almost entirely by illumination and rigidity needs, and in practice tracks letter height — a 12" letter typically gets a 3" return, a 36" letter needs 5"+ for even light diffusion and to resist flexing. So depth itself is a function of height, not a fixed constant.
2. **Perimeter** (stroke length that the trim cap and return-wall wrap around) scales with the letter's linear size. For a fixed font, width is roughly proportional to height (font aspect ratio is close to constant per glyph), so perimeter scales close to linearly with height.
3. **Return material area** = perimeter × depth. Since *both* factors move with height, the aluminum sheet consumed doesn't scale linearly with height — it scales faster, closer to height², the same way scaling a 2D shape uniformly by k multiplies its wall area by roughly k² once you account for depth also growing with k.
4. **Face material** (acrylic) scales with the letter's footprint area, i.e., also height²-ish for a fixed font — but acrylic sheet is a comparatively cheap, low-labor commodity, so it's a small share of total cost even though it scales the same way as returns.
5. **LED count** scales with area (you light a face, not just an edge), so it also moves faster than linear with height.
6. **Labor** (bending trim cap, welding return corners, wiring, mounting) is roughly proportional to perimeter and letter count, so closer to linear-with-height, but is a large fixed-ish cost per letter regardless of size (a letter is a letter to hang and wire).

So the *true* cost function is convex in height — somewhere between linear (labor, wiring) and quadratic (returns, face, LEDs) — not a clean single-variable linear function of either height or area alone.

Given that, why would an industry standardize on "$ per inch of height" instead of "$ per square foot of face," when area is arguably the more literal cost driver for the fastest-growing cost components (returns, acrylic, LEDs)?

Because **height, not area, is what the customer is actually buying**. A sign's value to a business is legibility at distance — the classic rule of thumb is roughly 1 inch of letter height per 10 feet of intended viewing distance. A customer thinking "I need this readable from the highway" reasons in inches of height, not square inches of face. Municipal sign codes reinforce this: zoning ordinances typically cap *letter height*, not sign area, because height-to-legibility is the safety/readability variable regulators care about. So height is simultaneously:

- the customer's mental model of what they're buying (visibility),
- the regulatory unit the permit is written in,
- and a reasonable (if imperfect and understated) proxy for the true convex cost curve, since nearly every cost driver — return depth, perimeter, area, LED count — increases monotonically with height for a fixed font.

Area-based pricing would be more cost-accurate per letter, but it requires a bespoke takeoff (measuring each glyph's actual footprint) for every quote, which adds sales friction and makes vendor-to-vendor quotes hard to compare. Height is a single number both sides already agree matters, cheap to state, and "good enough" as a cost proxy — so the market converges on it as a simplification, deliberately overcharging narrow letters ("I", "l") and undercharging wide/complex ones ("W", "M", "&") in exchange for a rate card that doesn't require CAD analysis to quote.

Prediction going in: because the fastest-growing cost terms (return material, face material, LEDs) scale faster than linearly with height, **actual price-per-inch should not be flat** — it should increase at the margin as letters get taller (a 36" letter should cost more than 3× a 12" letter, not exactly 3×), and pricing should show up as size *bands* or a convex curve rather than a strict linear rate.

## Corpus Answer

Search confirms the mechanism directly: taller letters need more aluminum for returns and backs, more acrylic for faces, more LED modules, and — critically — the sources state explicitly that **"the cost scaling is exponential, not linear"** and that a 36" letter "can easily cost double" an 18" letter, attributing this to both materials and added structural requirements (extra internal supports for very tall/deep returns). Return depth is confirmed to scale with height (standard 3–5" returns, deeper for taller/structural cases). Pricing in practice is presented in per-inch rate mentions ($12/inch cited as one benchmark) but real-world quotes cluster into non-linear size bands (small 12–18" at $75–$250/letter, medium 24–36" at $200–$600, large 48"+ at $400–$1,200+), which is a stepped/convex curve, not a flat linear rate — matching the "per inch" language is closer to sales heuristic and marketing simplification than a literal linear formula.

Sources:
- [Channel Letter Signs Cost Consideration | Signdealz](https://www.signdealz.com/blog/channel-letter-signs-cost-consideration)
- [How Much Does a Channel Letter Sign Cost? (2025) | Flexlume](https://www.flexlume.com/blog/how-much-does-a-channel-letter-sign-cost)
- [Cost Breakdown: What Goes Into Pricing Channel Letter Signs? – Mac1 Signs](https://mac1signs.com/cost-breakdown-pricing-channel-letter-signs/)
- [Channel Letter Sign Cost Guide 2026: What Affects the Price? – Blink Signs](https://blinksigns.com/channel-letter-sign-cost/)

## Delta Category: **rediscovered** (with one novel addition)

The core causal mechanism — that letter height acts as a proxy because return depth, perimeter, face area, and LED count all move with letter size — was derived independently and confirmed by the corpus, including the specific, non-obvious detail that scaling is convex/"exponential" rather than linear, which matched my prediction going in.

One piece of the reasoning was **not** found in any of the searched sources: the argument that height is used because it's the *customer's and regulator's* unit (legibility-at-distance, and municipal codes capping letter height rather than sign area), not just a cost proxy. The corpus material was entirely cost-side; the demand/regulatory-side justification for why height (rather than some other cost proxy, like perimeter directly) became the market's chosen unit is a framing the corpus didn't supply here. That piece is flagged as a genuine novel contribution, pending a dedicated search on sign-code conventions before it's trusted fully.

## Commentary

The valuable outcome wasn't just matching the corpus — it was correctly *predicting a specific quantitative shape* (convex, not linear, cost curve) before checking, from decomposing the physical build rather than recalling sign-industry trivia. That's the kind of check this gym is for: first-principles reasoning that yields a falsifiable, non-obvious prediction, which then either survives or doesn't against retrieval.
