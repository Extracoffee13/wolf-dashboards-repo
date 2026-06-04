# First-Principles Spike: What Is the Unit of Value in Commercial Signage?

**Date:** 2026-06-04
**Question:** What is the actual unit of value in commercial signage — square footage of sign face, impressions, or conversion events?
**Delta Category:** novel

---

## First-Principles Answer

### Start from the definition of value

Value is the delta between a world with the sign and a world without it. A sign exists to cause a person to take an action that benefits the business — visit, call, purchase, remember. The atomic unit of value must therefore be anchored to *caused actions*, not to the physical attributes of the sign.

### Test each candidate unit

**Square footage of sign face**
This is a production input, not an output. A 200 sq ft sign in a cornfield delivers near-zero value. Square footage prices the cost of manufacturing, not the outcome delivered to the client. It's a billing convenience, not an economic primitive.

**Impressions (exposures)**
Closer. Impressions measure how many people perceive the sign. But impression is necessary, not sufficient for value. A sign in a language no one in the area reads generates impressions and zero comprehension events. Impressions must be weighted by:
- (a) **Audience relevance** — does this person have latent demand for what's advertised?
- (b) **Legibility probability** — can they parse the message at speed and distance?
- (c) **Decision timing** — are they in a window where this information can cause action?

Unweighted impressions are a flawed proxy. They're a better proxy than square footage, but still miss the causation mechanism.

**Conversion events**
Cleanest economically. Someone saw the sign and acted. This is the right answer structurally — but it's nearly unmeasurable operationally for physical signage. No pixel, no cookie, no receipt link. Attribution requires expensive panel studies or location data inference.

### What is the true primitive?

The true primitive is: **decision-influence probability × LTV of the influenced decision**, divided by the cost of the sign. This is an expected value formula.

Operationally, that probability decomposes into four multiplied factors:

| Factor | What it captures |
|---|---|
| **Audience quality** | Relevant prospects who pass and can act |
| **Message clarity** | Probability a viewer correctly interprets the message in the available time |
| **Call strength** | Urgency or desire triggered by the message |
| **Recurrence / frequency** | How often the same prospect sees it — memory encoding and trust accumulate |

So the true unit of value in commercial signage is **quality-weighted relevant attention**: the product of all four factors above, measured in attention-seconds from people with relevant buying intent.

### Business implication for Brand 9 Signs

Most sign shops price on cost-plus-square-footage. This creates a structural gap: the price paid is anchored to input cost, while the value delivered scales with location quality, audience fit, and message design. A shop that can quantify and sell on quality-weighted impressions — particularly by advising clients on placement, visibility geometry, and message clarity — can command 30–60% price premiums on high-value installs, and position itself as a strategic marketing partner rather than a commodity fabricator.

---

## Corpus Answer

The Out-of-Home (OOH) advertising industry has a layered hierarchy of impression metrics:

- **Gross Impressions**: Raw count of people who pass the OOH asset (baseline)
- **Opportunity to See (OTS)**: Filters for physical visibility — not obstructed, illuminated, in line of sight
- **Likelihood to See (LTS)**: Applies probability models for dwell time, viewing angle, traffic speed, and environmental context
- **GRP (Gross Rating Points)**: Percentage of a target market reached
- **CPM**: Cost per thousand impressions ($2–$10 for static billboards; $5–$50 for programmatic DOOH)

Attribution uses mobile location data (Geopath), geo-holdouts, and media mix modeling (MMM). The MRC published final OOH measurement standards (December 2025). Geopath/OAAA are launching a next-gen audience measurement platform in H2 2026.

Critically: most traditional sign shops still price on material + labor + square footage + permit complexity. The impression/CPM framework is used by large OOH media companies (Clear Channel, Lamar, etc.), not by custom sign shops like Brand 9 Signs.

---

## Delta Analysis

**Category: novel**

The corpus and first-principles reasoning converge on the direction: away from square footage, toward quality-weighted impressions (the OTS → LTS evolution confirms this). I rediscovered that impressions beat square footage as the unit of value.

What the corpus does not contain:
1. The explicit framing of *decision-influence probability × LTV* as the foundational economic primitive
2. The four-factor decomposition (audience quality × message clarity × call strength × recurrence) as the operational form of that primitive
3. The observation that the gap between how sign shops *price* (cost-plus sq footage) and how they *create value* (quality-weighted impressions) is a specific margin opportunity for shops like Brand 9 Signs
4. The prescriptive implication: a custom sign shop that advises on placement, visibility geometry, and message design is selling a fundamentally different product than one that just fabricates to spec

The corpus describes how large OOH media buyers measure inventory they already own. It does not describe how a custom sign fabricator should frame its value proposition. That gap is where the novel framing lives.

---

## Commentary

The signage industry's measurement evolution (sq footage → impressions → quality-weighted impressions) mirrors a general pattern in media: any medium initially prices on production cost, then shifts to audience proxies (impressions), then toward outcome proxies (qualified impressions, attribution). Custom sign shops are 10–15 years behind billboards on this curve. The first-principles approach reaches the frontier faster than the corpus because it starts from economic first principles rather than industry conventions.

**Confidence: 0.72**

---

*Sources consulted:*
- Clear Channel Outdoor: OOH Metrics Explained
- MRC OOH Measurement Standards (December 2025)
- BlueAlpha: How to Measure OOH Advertising (geo holdouts, MMM)
- Geopath/OAAA measurement platform announcement
- The Drum: OOH buying guide (costs, models, metrics)
- Flexlume: How to Calculate the Value of Outdoor Signage
