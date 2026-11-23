# First-Principles Spike: 2026-11-23

**Question:** When does an aluminium composite (ACM) builder sign beat coroplast on total cost of ownership?

Source: `first-principles-backlog.md`, the next open item after 2026-11-20. Recent spikes have mostly been letter-height and pricing-unit questions, so this one is a deliberate change of topic.

## First-principles answer (written before any retrieval)

**Primitives.** A builder sign is a message held in front of a road for some period. Its cost is everything spent to keep that message readable and presentable for that period. That breaks into four terms:

1. **Unit cost** `C`: substrate, print, and laminate if any.
2. **Trip cost** `T`: truck, crew time, and hardware for each install or swap. For a 4x8 on posts this is a real number, often close to the unit cost of a coroplast panel.
3. **Physical life** `L`: how long the panel stays presentable outdoors.
4. **Message life** `M`: how long the copy stays correct. Phase names, prices, "Now Selling" vs "Final Homes", a new rep's phone number. Builder content changes on a sales clock, not a weather clock.

The useful life of any panel is `min(L, M)`. You never get paid for physical life beyond the message.

**Failure physics.** Coroplast is extruded fluted polypropylene. Polypropylene is UV-sensitive: unstabilised PP chalks and embrittles, and the printed face fades. The flutes make it light and cheap but weak against bending across them. A 4x8 sheet on two posts acts like a sail. It flexes, cycles at the fastener holes, and tears or bows, especially in Florida sun and Gulf Coast wind. Expect a presentable life of months to about two years outdoors, with large post-mounted panels at the short end. ACM has two thin aluminium skins bonded to a polyethylene core. It is rigid, flat, and doesn't care about UV. Its life is limited by the ink and laminate (several years), not the substrate. It also takes a vinyl re-face or overlay, so the substrate can outlive several messages.

**TCO over a horizon `H`.** `H` is the community's sell-out window, often 18 to 36 months.

- Coroplast: `n_c = ceil(H / min(L_c, M))` panels, so `TCO_c = n_c (C_c + T)`.
- ACM, replaced at each message change: `n_a = ceil(H / min(L_a, M))`, so `TCO_a = n_a (C_a + T)`.
- ACM, re-faced in place: `TCO_a = C_a + T + (k-1)(V + T')`, where `k` is the number of messages, `V` is the vinyl re-face cost and `T'` is the re-face trip.

**Case 1: `M ≤ L_c`.** The message changes before the coroplast wears out. Then `n_c = n_a` and coroplast wins by `n(C_a − C_c)`. ACM's durability is stranded value. This covers most phase and price signs, and most short promos.

**Case 2: `M > L_c`.** The copy is stable (community ID sign, builder brand, model-home ID) and outlasts coroplast. Coroplast now needs `≈ M/L_c` replacements per message, and each one pays `T` again. ACM wins when

`(C_a + T) < ceil(M/L_c) · (C_c + T)`

Illustrative wholesale-ish numbers, flagged as priors, not data: 4x8 coroplast printed about $150, 4x8 ACM printed about $350, trip about $100. Then `C_a + T = 450` and `C_c + T = 250`, so ACM wins as soon as coroplast needs a **second** panel within the message life. With `L_c` around 12 months in Florida sun, the crossover is a stable message running past roughly 12 to 18 months. Because `T` sits on both sides, a higher trip cost pulls the crossover earlier. Trip cost is the hidden term that favours ACM.

**Second-order terms.**
- **Appearance cost.** A bowed, faded coroplast sign at a model park costs sales credibility before it physically fails. That shortens the effective `L_c`, so coroplast's real life is its *presentable* life, not its *intact* life.
- **Wind and risk.** Coroplast tears loose and becomes litter. ACM is heavier and needs proper posts, but it stays put. Storm-season replacements are extra trips.
- **Reuse.** ACM frames and blanks can be overlaid. Coroplast has no reuse value.
- **Cash and ownership.** If the builder pays for signs out of a marketing budget each period, the lower upfront cost wins politically even when TCO loses. That is an organisational term, not a physics one.

**Decision rule.**
- Message life shorter than coroplast's presentable life: coroplast.
- Message life longer than about 1.2 to 1.5 times coroplast's presentable life, or the sign is large (4x8 or bigger), post-mounted and wind-exposed: ACM.
- Changing content on a long-lived frontage: ACM blank with vinyl overlays.

The binding variable is **message half-life**, not material life.

## Corpus answer (retrieved after the derivation)

Sources are mostly sign printers and sellers, who have a stake in what they sell. Their figures disagree with each other.

- **Coroplast** lasts "a season or two" outdoors. Estimates run 6–12 months typical (4over4), up to 6 months (FedEx Office), and 6–18 months in 4over4's comparison guide. 4over4 says **fading, not structural failure, usually ends it**, because the board outlasts the print. Lamination extends its life.
- **ACM** lasts 3–7 years depending on UV intensity and orientation, with south-facing signs dying first. It is about 20% cheaper than solid aluminium (vendor claim).
- **The rule the sources give:** coroplast for temporary, campaign and event signs; ACM for semi-permanent signs meant to last a few years; aluminium for permanent ones. Total cost of ownership comes up only to argue for aluminium on permanent storefronts. "Factor in reprint/replacement cost" is mentioned but never modelled.

Sources:
- https://www.trafficsafetystore.com/blog/rigid-sign-materials-compared-aluminum-vs-acm-vs-coroplast/
- https://www.4over4.com/guide/aluminum-signs-vs-coroplast-vs-pvc
- https://www.4over4.com/faqs/signs/how-long-do-corrugated-plastic-yard-signs-last-outdoors
- https://www.office.fedex.com/default/corrugate-sign.html
- https://www.victorystore.com/blogs/news/how-long-do-yard-signs-last-outside
- https://www.safetysign.com/aluminum-composite-sign-material

## Delta

**Category: novel**, with a partial correction to my own reasoning.

- **Where the two agree (rediscovered):** the material lifespans. Coroplast lasts about 6–18 months and ACM several years, and UV, sun and orientation govern both. My prior of about 12 months for coroplast sits in the corpus range.
- **What the corpus lacks (novel):**
  - It sorts signs by how long the *material* lasts ("temporary vs years"). It never treats the *message* as having a lifespan, or the useful life as `min(physical life, message life)`.
  - It never treats trip cost `T` as a term paid on every replacement, which is what pulls the crossover earlier.
  - It never uses ACM-plus-vinyl-overlay as a third option.

  For builders, the copy changes on a sales clock, so the corpus rule ("temporary means coroplast") is right for the wrong reason. A phase sign is temporary because its *message* is short-lived. A community ID sign at a 30-month frontage is "temporary" in the builder's mind but has a long-lived message, and the corpus rule would misassign it to coroplast.
- **Where the corpus corrected me:** I put structural failure (flute fatigue, torn fasteners) first. Vendors say fading usually ends a coroplast sign first. That evidence is mostly about small yard signs. For 4x8 panels on posts in Gulf Coast wind, structural failure is still plausible but unconfirmed. Either way, laminate on coroplast lengthens its life and moves the crossover later.

## Commentary / actionable

- When quoting a builder package, tag each sign with an expected **message life**. That sorts the materials:
  - phase, price and "Now Selling" signs: coroplast
  - community ID and model ID signs: ACM
  - long frontage with changing copy: ACM blank plus vinyl overlays
- Crossover rule of thumb with prior-level numbers (ACM 4x8 about $350, coroplast about $150, trip about $100): ACM wins once a stable message would need a second coroplast panel. In Florida sun that is roughly 12–18 months of unchanged copy.
- **Not verified:** B9's actual unit costs, trip cost and observed Florida coroplast life. Replace the priors with B9's real numbers before using this in a sales pitch.
