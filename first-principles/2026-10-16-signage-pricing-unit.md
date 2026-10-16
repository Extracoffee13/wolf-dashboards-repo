# Spike: 2026-10-16 — Signage pricing unit

**Question:** What is the first-principles pricing unit for custom signage, why does the industry quote by square foot, and when does that break?

## First-principles answer (derived before any lookup)
A sign is a bundle of costs. Decompose price = materials + labor + overhead + margin, then ask which driver scales with what.

1. Materials scale with area (face substrate, vinyl, paint, LEDs per lit area) and with perimeter (returns, trim cap, edge finishing). For a fixed construction, both grow with the sign's linear dimensions, so area is a decent first-order proxy for material cost.
2. Labor splits into two parts. Setup labor (artwork, file prep, programming CNC, mounting hardware, permit paperwork) is fixed per job, independent of size. Run labor (cutting, painting, assembling, wiring) scales roughly with area for a given construction.
3. Install labor is driven by weight, height, access (lift, crane, trenching/footing), travel and crew-hours. It barely correlates with face area. A 4 ft monument and a 4 ft wall sign cost very different amounts to install.
4. Complexity (letter count, curves, multi-layer, lighting type) multiplies run labor without changing area.
5. Therefore the true cost function is: fixed setup + area x construction-rate + install(site) + complexity multiplier. Single-unit pricing can't capture it.

Why would the industry still pick one unit? Quoting needs speed and comparability. Customers compare by a rate they can understand; area is the one variable both sides can measure from a drawing. So price per square foot is a lookup key into a table of construction types (flat cut vinyl, routed PVC, channel letters, cabinets), each with its own rate, plus a minimum charge to cover fixed setup. That gives the prediction: rate per sq ft FALLS as size rises (fixed costs amortize), differs sharply by construction type, and install is quoted separately.

Where it breaks: small signs (setup dominates, so minimums rule), channel letters (priced per letter or per inch of letter height because perimeter and letter count drive labor, not face area), illuminated work (LED count and power supplies), and anything with difficult install. Prediction: for letters the unit is height-inches or per-letter, for flat stock it is sq ft, for installs it is crew-hours/day-rate.

Implication for Brand 9 operations: an estimating engine should carry a triple (setup, area/perimeter/letter rate by construction, install by site class) rather than a single $/sqft, and should log actuals per component so rates can be fitted instead of guessed.

## Corpus answer
Trade sources (Signs101 threads, fabricator guides) show: flat graphics, wraps and large prints are priced per sq ft; channel letters per upright (vertical) inch (~$15-22/in, forum-reported) or flat per letter up to a size cap; wide/script fonts adjust the price; installation, permits and electrical are separate line items. Consumer-marketing pages give wide ranges ($150-1,000/letter) and are low quality.
Sources: https://www.signs101.com/threads/vertical-inch-channel-letter-pricing.180201/ , https://www.signs101.com/threads/channel-letters-and-upright-inches.121240/ , https://blinksigns.com/channel-letter-sign-cost/

## Delta: rediscovered
Same structure: unit varies by construction type, install separate, per-letter/height unit for letters, area for flat work. Not in the corpus snippets (unverified as novel, only the framing): explicit fixed-setup term and a minimum-charge rationale, plus "log actuals per component to fit rates." Missed: corpus favors upright inch over my perimeter-based unit for letters (practical proxy, easier to measure).

## Commentary
Reasoning from cost drivers predicted the orthodox practice well. Weak point: I did not predict the specific shop-level unit (upright inch) - a convenience proxy, not a cost law. Confidence 0.7.
