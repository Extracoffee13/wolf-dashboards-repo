# First-Principles Spike 2026-10-30

## Question
What determines the price of a custom sign, and why do sign shops quote by square foot?

## First-principles answer (derived before any lookup)

**Primitives.** A sign is (1) material consumed, (2) machine time, (3) human time, (4) fixed per-job overhead, (5) delivery/install, (6) risk and margin.

**Chain.**
1. Material scales with area. Substrate (aluminum, PVC, acrylic), vinyl and ink are bought per sheet or roll, so cost per job ~ area x unit price, plus waste. Nesting efficiency and offcuts make waste a multiplier (roughly 1.1-1.4x) that depends on shape and quantity.
2. Machine time scales with area for printing (head sweeps cover area) and with perimeter/path length for cutting and routing. So a flat-print sign is area-driven, a die-cut or routed letter sign is perimeter/complexity-driven.
3. Human time has a large fixed part (art prep, proofing, setup, file fixes, client communication) that does NOT scale with area. A 1 sq ft sign costs nearly as much to set up as a 10 sq ft one. So per-sq-ft price must fall as size rises, and small jobs need a minimum charge.
4. Quantity amortizes setup: unit price = variable + fixed/N. Repeat jobs with reusable art are cheaper.
5. Install is a separate service: labor hours, travel, equipment (lift, truck), site risk. It scales with height, count of locations and access, not with sign area.
6. Illuminated/dimensional signs add components (LEDs, power supplies, fabrication labor) that scale with letter count and depth, not area.
7. Margin must cover idle capacity, rework, warranty and the overhead of quoting itself, so price = cost x markup, with markup higher where the customer cannot easily compare.

**Why quote per square foot?** Area is the one number the customer and the shop can both measure from a mock-up. It proxies material and print time, which are the dominant variable costs for flat signs. It is a communication convenience, not a true cost law: it hides the fixed part (hence minimums and tiered rates) and breaks for dimensional, lit and installed work, where the real drivers are labor hours and components.

**Prediction.** Real shops use per-sq-ft rate cards by material for flat goods, with size tiers and minimums, and custom estimates (cost-plus, labor-hours based) for dimensional, illuminated and installed signage. Install priced separately.

Confidence in structure: high. Unsure on actual numbers and markup norms.

## Corpus answer (searched after deriving)
- Shops build a price per category, then express it per letter, per sq ft or per sign. Flat vinyl/graphics are priced per sq ft or per letter; install is billed separately with a minimum.
- Minimum charge = greater of (time x hourly rate) and a set floor; small jobs still carry travel, setup, layout, cleanup.
- Markup is applied per material category (cited: ~1.5x cost common; vinyl far higher, ~10x; metals lower). A single flat markup distorts pricing.
- Install labor cited at $40-90/hr, 6-20 hours for mid-size storefront signs; no-electrical signs can be cheap.
- Illuminated/LED/neon quoted at much higher $/sq ft ranges; dimensional work is job-costed.
- Caveat: many sources are lead-gen cost sites, not shop data; method is reliable, numbers are not.

Sources: [Sign Warehouse pricing guide](https://signwarehouse.com/blogs/content/a-basic-guide-to-pricing-signs-banners-and-signs), [SignShop: understanding sign pricing](https://www.signshop.com/business-mgmt/sales-a-marketing/understanding-sign-pricing/), [Signs101 small-work pricing thread](https://www.signs101.com/threads/pricing-for-small-work-like-store-hours-signs.167540), [Angi install cost](https://www.angi.com/articles/commercial-sign-installation-cost.htm), [beancount job-costing guide](https://beancount.io/blog/2026/08/25/custom-sign-shop-bookkeeping-material-markup-labor-burden-installation-pricing-guide).

## Delta: rediscovered
Structure matched: area as shared measurement proxy, fixed-cost-driven minimums, separate install, job-costing for lit/dimensional work.
Corpus added what reasoning could not supply: real numbers, and that markup varies by material category (vinyl vs metal), which I had treated as one blended markup.
Gap in my derivation: I assumed markup tracks buyer comparability; the corpus implies it also tracks how much value the material adds relative to its cost.

## Commentary
For Brand 9: quote flat goods from a per-material rate card with size tiers and a floor; keep install and dimensional/lit work on labor-hour job costing. Do not apply one blended markup. Confidence in the numbers is low (web sources are weak); confidence in the structure is high.
