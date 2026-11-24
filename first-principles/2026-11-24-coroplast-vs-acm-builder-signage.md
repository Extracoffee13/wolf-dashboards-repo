# First-Principles Spike — 2026-11-24

## Question

**When should a homebuilder's community sign be made on disposable coroplast versus durable aluminum composite (ACM)?**

Picked because the backlog was empty (created as a placeholder today). This question sits on Brand 9's core work (Lennar GC/JAX decks: 4x8s, 4x4s, model IDs, frontage), and the answer drives what we quote.

---

## First-principles answer (written before any search)

**Primitives.** A sign exists to carry a *message* at a *place* for a *time*. Its cost is not what the sheet costs. It is the cost of keeping the right message readable at that place for the whole time. Breaking that down:

1. **Material + print** per unit (C). Coroplast is cheap. ACM costs several times as much per sheet.
2. **Useful life** (L) before the sign stops doing its job. Coroplast in Gulf Coast sun and wind warps, fades and flexes at the fasteners within months. ACM stays flat for years. The *print* (UV ink or laminated vinyl) usually fails before the ACM does.
3. **Truck rolls** (T). Each install, swap or repair is a person, a vehicle, a drive and maybe an auger. For a 4x8 at a community entrance, one visit can easily cost about as much as the coroplast sheet. Whenever a sign dies early, you pay C *and* T again.
4. **Message lifetime** (M). How long until the words have to change anyway: "Now Selling" → "Final Phase" → "Closeout"; price points; incentives; a new model name. Builder messages are volatile. Directional and promo copy may change monthly. Community identity copy lasts the whole sell-out.
5. **Deployment horizon** (H). How long the place needs any sign at all. A master-planned community takes years to sell out. A grand-opening weekend lasts days.
6. **Failure cost** (F). A warped, faded or blown-over sign at a model park is not neutral. It tells the buyer this builder doesn't take care of things. That cost lands hardest on the signs buyers see first (entrance, model park) and is close to zero on a back-lot directional.

**Derivation.** Each sign position needs a replacement every min(L, M). The cause is either the substrate dying or the message going stale. Over a horizon H:

- Coroplast cost ≈ (H / min(L_coro, M)) × (C_coro + T)
- ACM cost ≈ C_acm + T + (H / M) × (reface cost + T), where a reface is a new vinyl face or a new print, and the panel and posts stay.

Three conclusions follow:

- **If M < L_coro** (the message changes before coroplast dies), durability buys nothing. The sign is replaced for content reasons anyway. **Coroplast wins**: pricing riders, event signs, incentive and promo signs, short-run directionals.
- **If H is short**, coroplast wins for the same reason. The extra years of ACM life fall outside the horizon.
- **If M and H are both long relative to L_coro**, coroplast forces repeated truck rolls only because the substrate died. Since T is often ≥ C_coro, the cost of coroplast is driven by **visits, not sheets**. ACM wins once the horizon covers about 2–3 coroplast lifespans, and sooner where F is high.

**The non-obvious move: separate the slow layer from the fast layer.** The real choice is not "coroplast or ACM" for a whole sign. A sign is a stack of layers that change at different speeds:

| Layer | Change rate | Right material |
|---|---|---|
| Posts / frame / footing | Lifetime of community | Treated wood, PVC, aluminum (installed once) |
| Panel / substrate | Years | ACM |
| Identity face (logo, community name) | Lifetime of community | Print on ACM, or a durable laminated vinyl |
| Message face (phase, price, incentive) | Weeks to months | Coroplast rider, magnetic, or replaceable vinyl overlay |

Match each layer to its own change rate. The durable layer is bought once. The volatile layer is made cheap enough to throw away and cheap enough to swap in one visit, ideally *without tools*, so a sales agent can do it and no truck roll is needed. That design move removes T from the volatile term, which was the dominant cost.

**Decision rule (derived):**
1. Ask "how long until the words change?" before "how long must it survive?"
2. M ≤ ~6 months or H ≤ ~6 months → coroplast.
3. M and H ≥ ~12 months, especially at high-visibility positions → ACM (or a durable substrate) with a replaceable message layer.
4. In between, decide on truck-roll cost and failure visibility, not on the price per sheet.
5. Always quote the structure once and the faces as a recurring line. That also matches how builders actually reorder.

Confidence before search: moderate. The numbers are illustrative. The structure (replace at min(L, M); truck rolls dominate; split layers by change rate) should hold.

---

## Corpus answer

Searched after the derivation was written. The sources are mostly sign-vendor guides (4over4, Traffic Safety Store, AlphaGraphics, eSigns, OptSigns) plus rider and frame product listings (Lowen, Staples).

- **Coroplast:** temporary, light and budget-friendly. Outdoor life is quoted at about 6–18 months, or 1–3 years with a UV coating. Sun and wind shorten it.
- **ACM / aluminum:** rigid, looks professional and lasts for years. Panel signs are commonly quoted at 10–15 years.
- **The usual rule:** use coroplast when the sign is temporary, light or budget-sensitive. Use aluminum/ACM for multi-year entries and identification. One guide notes that reprinting twice in coroplast costs more than printing once in aluminum.
- **Riders / inserts** are an established product category. Spring-clip frames take swappable message panels "without replacing the whole sign." Vendors say this saves money but give no measurements.
- An industry article says to weigh installation and long-term maintenance, not just the purchase price.
- No published total-cost-of-ownership benchmark was found for rider swaps or for truck-roll cost.

## Delta category: **rediscovered**

The core answer matches the corpus: coroplast for the short term, ACM for multi-year use, crossover at about two coroplast lifespans. Riders exist as a product, so the "split the layers" idea also has a working counterpart in the market.

## Commentary

- **Validated:** the substrate lifespans and the crossover at roughly 2–3 coroplast lives were reached without lookup. The reasoning held.
- **Framing the corpus is weaker on (not enough to call it novel):** the corpus sorts the decision by *durability*: how long must it survive? The derivation sorts it by **min(substrate life, message life)**: how long until the words change? It also names **truck rolls, not sheets** as the dominant cost. Neither is quantified anywhere I found. Riders are sold as a convenience, not as a way to cut truck rolls.
- **Actionable for B9:** quote the frame, posts and identity face once, and quote message faces as a recurring line item. Design message layers so a sales agent can swap them without tools. Ask the builder "how often does this copy change?" before "how long must it last?"
- **Caveat:** the corpus is vendor marketing, and the lifespan numbers are not independently measured. Gulf Coast UV likely pushes coroplast toward the low end of the range.

Sources: [4over4 Aluminum vs Coroplast vs PVC](https://www.4over4.com/guide/aluminum-signs-vs-coroplast-vs-pvc), [Traffic Safety Store rigid materials](https://www.trafficsafetystore.com/blog/rigid-sign-materials-compared-aluminum-vs-acm-vs-coroplast/), [eSigns yard sign material](https://www.esigns.com/yard-sign-material.html), [AlphaGraphics outdoor sign materials](https://www.alphagraphics.com/us-illinois-crystal-lake-us590/blog/blog/2026/06/best-outdoor-sign-materials), [Lowen rider-insert frames](https://www.lowensign.com/realestatesigns/rentalsigns/products/item/144z820w/blank,%20customizable%20angle%20iron%20rental%20sign%20unit%20with%202%20rider%20inserts,%20%2024h%20x%2024w,%20white.html), [Buildings.com — Signs of the Times](https://www.buildings.com/smart-buildings/article/10193347/signs-of-the-times-and-beyond)
