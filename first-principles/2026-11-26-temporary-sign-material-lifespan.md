# First-Principles Spike — 2026-11-26

**Question:** What should set how long-lived a material a temporary builder or community sign is made from (coroplast vs PVC vs ACM/aluminum)?

*Source: `first-principles-backlog.md` was missing. I created it and generated this question from Brand 9's builder-signage work (Lennar GC/JAX decks).*

---

## 1. First-principles answer (written before any search)

**Primitive: a sign is a container for information, placed in front of a stream of passers-by.** It is worth something only while three things are all true:

1. it is physically present and legible,
2. what it says is still true, and
3. someone still needs to say it there.

So a sign's effective life is the **minimum** of three clocks:

    L_eff = min(L_phys, L_info, L_deploy)

- **L_phys**: how long until it *looks* bad, which comes well before it falls apart. A faded or warped builder sign tells buyers the community is stalled. Its value drops before it physically fails. In Florida, UV and hurricane wind cut this clock sharply. Wind failure is all-or-nothing: the sign is either up or in a ditch.
- **L_info**: the half-life of the message. Prices, incentives, "Now Selling" changing to "Final Opportunity", phase or plan names, model hours, and builder rebrands each expire the face, whatever its condition.
- **L_deploy**: how long the community needs a sign at that spot at all (sell-out, model-park closure, entry monument handover to the HOA).

**Cost per useful day** = (material + print + **install/removal labor**) ÷ L_eff.

Two things follow.

**(a) Durability beyond min(L_info, L_deploy) is wasted money.** An aluminum face carrying a price that changes next quarter buys years of life that will never be used.

**(b) Durability *below* that minimum is very expensive, because the real cost of a failure is the truck roll, not the substrate.** For a 4×8 or 4×4 the board is often cheaper than the crew, vehicle and time it takes to reinstall it. Each early failure also means a reprint and a period with no sign up. So the target is L_phys ≥ min(L_info, L_deploy), with margin for the local climate, and no more.

**(c) The three clocks run at different speeds on different *parts* of one sign, so the parts should be split.** The structure (posts, frame, monument) should be built to L_deploy, which runs in years. The face should be built to L_info, which runs in months. The fastest-changing content (price, incentive, "Sold") belongs on riders, magnets or slide-in inserts built to the shortest clock. A sign that welds a 3-month message to a 3-year structure means that every time the message changes, someone either throws away the structure or leaves a wrong message up.

**Predicted rules:**
- Event, open-house or incentive messaging (L_info of weeks to months): coroplast, or a rider on a durable sign.
- Phase or community-name faces (L_info ≈ L_deploy, about 1–3 years): PVC or ACM faces in a reusable post-and-frame system.
- Entry monument (L_deploy of many years): aluminum or HDU. Information changes here are rare, but when they happen they are expensive.
- Shorten every L_phys estimate for full sun and wind exposure, and spec wind load as pass/fail, not as an average.
- The question to ask a client is not "how long should it last?" It is "**how long will what it says stay true, and how long will you need a sign at this spot?**"

## 2. Corpus answer (after search)

The orthodox guidance, mostly from sign-printer guides, picks material by **how long the sign is needed outdoors**:
- Coroplast: about 6–18 months, for weeks to a season. Sun is its weak point.
- Expanded PVC: about 2–5 years (1–2 years exposed on a fence).
- Aluminum: 5+ years. Shops report 10–15 years for panels and 20+ years for monuments.
- Aluminum is "often more economical over its lifespan" for permanent installs. Shade extends the life of every material, and sun and wind shorten coroplast fastest.
- Separately, architectural specs (NY OGS, VA) describe **modular frames with removable or replaceable inserts and face panels**, but for wayfinding and repair, not for marketing information going out of date.
- The corpus has **no** cost-per-phase model, no install-labor term, and no concept of message half-life.

## 3. Delta: **novel**, with part of it rediscovered

- **Rediscovered:** the mapping from duration to material (coroplast for short, PVC for medium, aluminum for long) and the climate penalty. The corpus confirms modular frames with replaceable faces exist.
- **Novel:** the corpus uses one undefined clock, "how long you need it." The first-principles answer splits that into three clocks and makes the *information* half-life the usual binding constraint for builder marketing signs. It adds the truck roll as the main cost of failing early. It also uses differing clock speeds as the reason to separate structure, face and rider. In the corpus, modular faces are a maintenance feature. Here they follow from the economics.

## 4. Commentary

Retrieval gave reliable numbers (the material lifespans) that I could only have guessed at. Reasoning gave the *decision structure*, which the corpus doesn't have. The corpus answers "how long does PVC last?" The useful question for a builder is "how long does this *message* last?" The two methods do different jobs: use retrieval to set the parameters and reasoning to build the model they plug into.

**Operational implication for Brand 9:** quote builder programs as reusable frames plus faces on a refresh schedule, with riders for incentive and price content. In the quote, ask about the message's lifespan before the material. This also creates repeat face orders from the same installed frames.

Sources: [4over4 — Aluminum vs Coroplast vs PVC](https://www.4over4.com/guide/aluminum-signs-vs-coroplast-vs-pvc), [4over4 — outdoor sign board by climate](https://v2.4over4.com/guide/how-to-choose-outdoor-sign-board-material), [AlphaGraphics — best outdoor sign materials](https://www.alphagraphics.com/us-illinois-crystal-lake-us590/blog/blog/2026/06/best-outdoor-sign-materials), [Signs.com — PVC vs aluminum](https://www.signs.com/whats-the-difference-between-pvc-signs-and-aluminum-signs/), [NY OGS spec 101429 Modular Signage](https://online2.ogs.ny.gov/dnc/masterspec24/docs/Division10Specialties/101429.0ModularSignage.docx), [VA spec 101400](https://www.wbdg.org/FFC/VA/VANCAS/VANCA101400.pdf).
