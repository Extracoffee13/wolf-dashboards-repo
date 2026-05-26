# Spike: What is the correct unit of pricing for commercial sign fabrication?

**Date:** 2026-05-26  
**Domain:** Brand 9 Signs / signage economics  
**Delta category:** novel

---

## The Question

Sign fabricators price by square footage or cost-plus. Billboard rental companies price by CPM (impressions). Both sell signs. Should the unit of pricing be the same? If not, why — and what does that imply?

---

## Step 2 — First-Principles Answer

### The primitives

A sign's only purpose is to influence human behavior: trigger a visit, reinforce a brand, accelerate a decision. That is the thing a buyer is actually purchasing. Everything else — aluminum substrate, LED modules, installation labor — is the cost structure of delivering that influence.

**Value of a sign = (number of qualified impressions) × (probability of influencing a decision) × (value per decision to the buyer)**

### Why the industry prices on cost

If value is impression-driven, why does fabrication price by square footage?

Three reasons:

1. **Attribution opacity.** A sign company cannot easily measure how many decisions their sign influenced. Foot-traffic counters, phone-number tracking, and conversion rate data belong to the buyer, not the fabricator. No measurement → no lever to price on value.

2. **Risk allocation.** A cost-plus price puts revenue risk on the buyer (the sign may work poorly if they chose a bad location). A value-based price would transfer that risk to the fabricator. Sign shops are not in the business of carrying traffic-volatility risk.

3. **Buyer comparability.** Square footage is auditable and comparable across quotes. Buyers use it as a unit to shop. Any single shop that prices differently is immediately harder to compare, creating friction that loses deals even if the model is theoretically superior.

So cost-plus / sq-ft pricing is a rational market equilibrium — not because it reflects value, but because it minimizes transaction costs and asymmetric information problems.

### The structural gap this creates

Here is what follows from the above: **a sign in a high-traffic, high-demographic-quality location is systematically underpriced by sq-ft models, and a sign in a low-traffic location is overpriced.**

The same 10-square-foot channel letter set installed on a downtown flagship storefront with 50,000 daily pedestrians delivers roughly 1,000× the impressions of the identical set on a rural strip mall. Under cost-plus pricing, both jobs price nearly the same.

This gap is not captured by any mechanism in the fabrication industry. It IS captured in the outdoor advertising (billboard) industry via:
- Traffic count data (DOT/Geopath)
- CPM-based rental rates
- Location tiering ($2–$50 CPM depending on market)

### The bridging framework: a location-quality multiplier

A fabrication shop that wanted to capture location premium without abandoning sq-ft pricing could introduce a **location multiplier** layered on top of base rates:

```
Final price = base_sqft_rate × material_tier × location_multiplier
```

Where `location_multiplier` is estimated from:
- Estimated daily traffic past the sign face (DOT data or proxy)
- Audience demographic quality (median income, target-buyer density)
- Visibility score (dwell time, angle of approach, competing visual clutter)

This is not CPM — it's a fabrication quote that acknowledges location-driven value without requiring ongoing measurement. The fabricator prices a single transaction, not recurring impressions.

### Implications for Brand 9 Signs

1. **Proposal differentiation:** Presenting a location analysis alongside a fabrication quote reframes the conversation from cost to investment. Buyers in high-value locations see they are being priced fairly (and relatively cheaply vs. the media value they're unlocking).
2. **Margin capture:** High-traffic commercial projects can bear a 1.5–2.5× location multiplier without losing the deal, because the ROI math closes easily.
3. **Consultative positioning:** This model requires knowing traffic counts and demographics — which positions Brand 9 as a strategic signage partner, not a commodity shop.

---

## Step 3 — Corpus Answer

**Fabrication industry:**
- Dominated by cost-plus and sq-ft pricing: $10–$400/sq-ft depending on sign type and material
- Monument signs: $150–$400/sq-ft (ISA data)
- No explicit location premium in fabrication quotes — location affects complexity (permit requirements, installation difficulty) but not pricing as a value multiplier
- Customer ROI education using CPM sometimes appears in sales materials, but it's not reflected in the pricing model

**Outdoor advertising / billboard industry:**
- CPM-based: $2–$50/thousand impressions, market-dependent
- Location is the primary price driver — NYC ~$7.50 CPM, secondary markets $4–$6 CPM
- Digital boards command 30–50% premium over static
- Traffic data from Geopath/DOT is standard underwriting for rates

**The gap confirmed:** The two industries are structurally siloed. Fabricators price cost; media companies price value. No mainstream fabrication industry source discusses location multipliers or bridging CPM logic into fabrication pricing.

---

## Step 4 — Delta Analysis

**Category: novel**

My first-principles reasoning arrived at the correct description of both pricing models and confirmed the structural gap between them. The corpus validates each side independently.

What the corpus does NOT contain: the specific framework of applying a location-quality multiplier to fabrication pricing to capture impression-based value in a single-transaction context. Billboard companies price on recurring impressions because they retain ownership of the asset. Fabricators sell the asset outright — but that doesn't mean they can't price the one-time transaction using a location lens.

The **novel framing** is: fabrication pricing can absorb location premium without becoming a media model, through a multiplier applied at quote time, derived from the same traffic/demographic data media companies use for rental pricing. This would let a sign shop like Brand 9 capture value that currently flows entirely to the buyer.

---

## Commentary

This spike is immediately actionable. Brand 9 Signs likely already intuits that downtown jobs "should" cost more — but without a principled framework, that intuition either gets suppressed (leaving money on the table) or applied inconsistently (creating pricing that feels arbitrary to buyers). A documented location multiplier framework makes the premium legible and defensible.

The deeper lesson: **cost-plus pricing is a solution to an information asymmetry problem, not a statement about value.** Anywhere you can reduce that asymmetry (through traffic data, visibility scoring, demographic proxies), you unlock the ability to price closer to value — and capture the difference as margin rather than gifting it to the buyer.
