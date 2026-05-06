# First-Principles Spike — 2026-05-06

## Question

**What determines the economic value of a commercial sign location, independent of the sign itself?**

Domain: signage industry primitives, real estate fundamentals, Hartley Capital strategy

---

## Step 2 — First-Principles Derivation

*(No retrieval. Reasoning from primitives only.)*

### Starting primitives

1. A sign exists to transfer information to observers.
2. Value requires a receiver — without eyes, a sign has zero communicative value.
3. Commercial signs are placed to influence purchasing decisions — the ultimate measure is conversion, not impressions.
4. Location is fixed; the sign is replaceable. Therefore location value is the durable variable.

### Derivation

**Location value = (Audience Size) × (Audience Relevance) × (Attention Probability) × (Conversion Proximity)**

**Audience Size — a network flow problem.**
Traffic volume through a location is determined by the surrounding road infrastructure and land-use zoning. Locations on high-betweenness nodes in the road network (intersections, on/off-ramps, arterial merges) see more vehicles per unit time. This is not a sign property — it is a topology property. Higher betweenness → higher baseline value, independent of what sign occupies the location.

**Audience Relevance — a matching problem.**
Raw traffic is not uniform. A location's value is a product of whether the passing demographic matches the advertisers willing to pay for exposure there. A sign location in a high-income commuter corridor commands a premium multiplier because the pool of advertisers targeting that demographic is large and price-competitive. Relevance is determined by land use patterns around the location (office parks, retail strips, residential density and income level) — again, not the sign.

**Attention Probability — a cognitive load problem.**
A driver at 60 mph on a familiar straight highway is operating on autopilot; cortical attention is suppressed. A driver approaching a fork, an off-ramp decision, or a traffic signal is visually scanning the environment actively. **Sign locations at road-network decision points capture disproportionately higher attention** because the driver is already in a heads-up visual-scan state. This is the "decision-point topology" multiplier: locations at nodes where drivers must choose receive more attentive eyes per vehicle than mid-run locations with the same ADT. Visibility (unobstructed sightlines, lighting, dwell time) is the conventional framing, but the deeper driver is cognitive state, not just geometry.

**Conversion Proximity — a temporal gap problem.**
The causal chain from sign exposure to purchase action degrades with time. A sign 500 feet before a fast-food exit converts at higher rates than an identical sign 5 miles prior, because the decision-action gap is compressed. Therefore locations near points of sale — retail entrances, exit ramps leading to commercial strips — carry a structural conversion premium that is baked into the location's value, not the sign's creative.

### Scarcity overlay
Permit scarcity is not a first-principles primitive — it is a regulatory artifact that caps supply and inflates values above what the four factors would produce in a free market. It is real and material, but it is a market distortion layer sitting on top of the fundamental value, not a component of it.

### Summary formula
```
Location Value ≈ ADT × Demographics_Multiplier × Decision-Point_Attention_Multiplier × Conversion_Proximity_Factor
```

The location with the highest value has: maximum throughput traffic, matching affluent demographics, sits at a road-network decision node, and is adjacent to points of sale.

---

## Step 3 — Corpus Answer

**Primary source: outdoor advertising industry (OAAA, Geopath, SignValue, appraisal literature)**

The industry converges on these determinants:

1. **ADT (Average Daily Traffic)** — the dominant metric. Rule of thumb: every 10,000 ADT adds ~$1,000–$2,000/month to billboard value. Highways with 50,000 ADT command 5× rates vs. 10,000 ADT roads.

2. **Demographics multiplier** — household income >$75k applies a 1.5–2× multiplier; business decision-makers during commute hours apply a 2–3× multiplier. A billboard reaching 30,000 affluent commuters often outprices one reaching 50,000 rural vehicles.

3. **Visibility factors** — angle to roadway, dwell time (how long a driver can see the sign), obstructions (trees, buildings, competing signs), lighting. Measured via Geopath's "Eyes On Impressions" (EOI) methodology, which adjusts raw traffic for these factors.

4. **Market size** — larger metros command base-rate premiums due to advertiser competition.

5. **Advertiser demand** — secondary market dynamic: high-demand categories (retail, auto, fast food) cluster in certain corridors, bidding up location rates.

6. **Permit scarcity (explicitly identified in appraisal literature)** — regulatory moratoria and caps on new permits mean existing permitted locations carry a use-permit premium. Appraisal guidance explicitly separates the value attributable to the permit from the value of the physical improvement.

---

## Step 4 — Delta Analysis

| My derivation | Corpus | Match? |
|---|---|---|
| Audience size (traffic volume / ADT) | ADT primary metric | ✓ exact |
| Audience relevance (demographic match) | Demographics multiplier | ✓ exact |
| Attention probability (visibility + cognitive load) | Visibility / dwell time / EOI adjustment | ✓ partial — corpus captures geometry, not cognitive state |
| Decision-point topology as attention multiplier | Not explicitly named; subsumed in dwell time | ⚡ novel framing |
| Conversion proximity (temporal gap to purchase) | Not named as a distinct factor | ⚡ novel framing |
| Permit scarcity as regulatory overlay (not a primitive) | Explicitly foregrounded in appraisal literature | Corpus adds; I anticipated but didn't elevate |

### Category: **rediscovered**

The core framework (traffic × demographics × visibility = location value) aligns precisely with the corpus — derived independently, validates the reasoning chain. Two sub-elements are more specific than the corpus:

- **Decision-point topology** (cognitive scanning state at road-network nodes) is subsumed under "dwell time" in industry measurement but the mechanistic explanation is different. The corpus measures *how long* a driver sees the sign; the derivation surfaces *why attention is higher at intersections and off-ramps*.
- **Conversion proximity** (temporal gap between stimulus and action) is implicit in location-based targeting practices but not named as a distinct location-value factor in standard OOH literature.

Permit scarcity: correctly identified as a regulatory overlay rather than a primitive, which the appraisal literature confirms ("value attributed to the use permits, not to the improvements").

---

## Commentary

For Brand 9 Signs and Hartley Capital, the actionable insight from this spike is that **location selection should score against all four primitives, not just ADT**. An operator who optimizes only on traffic count will overpay for mid-run highway locations and underprice decision-point locations (off-ramp faces, intersection corners) that punch above their ADT in attention and conversion. The decision-point topology multiplier is the market inefficiency most likely to be underpriced in standard rate cards.

For Hartley Capital strategy: permitted locations in moratorium markets carry a scarcity premium that compounds separately from the four operating fundamentals — and that premium is an illiquid, regulatory-dependent asset, not an operating asset. Distinguish the two when underwriting sign-adjacent real estate.
