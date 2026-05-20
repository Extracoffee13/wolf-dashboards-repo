# Spike: What is the primary unit of value in commercial signage for a small business?

**Date:** 2026-05-20  
**Slug:** primary-unit-of-value-in-commercial-signage  
**Delta category:** novel  
**Confidence:** 0.70

---

## Question

When a small business buys a sign from a fabricator like Brand 9 Signs, what are they actually paying for?
The candidate units of value are: **attention** (advertising impressions), **identity** (brand assertion),
**wayfinding** (helping people find the location), and **persistence** (always-on delivery). Which is primary?
Does the industry's answer match the first-principles answer?

---

## Step 2 — First-Principles Derivation

*(No retrieval. Reasoning from primitives only.)*

### Start with the object

A sign is a physical artifact that does three things simultaneously:
1. **Encodes information** (name, logo, category, arrow)
2. **Places that information at a fixed spatial coordinate** — it does not travel, it does not broadcast
3. **Persists without active transmission cost** — no one flips it on per viewer; it is always on

This triple structure distinguishes a sign from every other communication medium: broadcast (no fixed location),
digital display (active power cost, can be turned off/blocked), word-of-mouth (no spatial anchor).

### Strip it away: what breaks first?

Thought experiment — remove the sign from a small business with an otherwise unchanged location.

**What breaks immediately (day 1):**
- A person standing 30 feet from the entrance, uncertain which door is correct, cannot resolve that uncertainty.
  They may leave. This is **wayfinding failure at point of presence**.
- A new passerby sees a door but cannot tell what business is behind it. They don't enter.
  This is **existence declaration failure**.

**What breaks slowly (weeks/months):**
- Brand recall weakens for repeat visitors who relied on the sign as a visual anchor.
  This is **identity assertion failure**.
- New customers who might have been captured by the sign's presence are never acquired.
  This is **attention / top-of-funnel failure**.

### Which failures are hardest to substitute?

Test each against available substitutes:

| Value type | Digital substitute | Physical substitute | Substitutability |
|---|---|---|---|
| Attention / impressions | Social ads, Google Ads, Yelp | Flyers, sandwich board | High — many alternatives |
| Identity assertion | Website, uniforms, interior design | Window decal, branded awning | Medium — partial substitutes exist |
| Existence declaration | Google Maps listing, GPS | Handwritten note on door | Medium — works if customer already knows to look |
| **Wayfinding at point of presence** | GPS stops at street address | Nothing covers the last 20–50 feet | **Low — uniquely irreplaceable** |

The critical insight: **GPS addresses the "where on the map" problem. A sign addresses the "which door right now" problem.**
No digital tool fully replaces real-time, zero-friction, location-anchored disambiguation at the moment of physical arrival.
A person standing in front of a strip mall with six units cannot GPS their way to the correct door; they scan for signage.

### Persistence as a multiplier, not a value in itself

Persistence is the delivery mechanism that makes wayfinding available 24/7. It multiplies the wayfinding value by availability.
A sign that operated only 8 hours/day would still provide wayfinding — but less of it. Persistence is not a distinct value;
it is a coefficient on whichever value type is primary.

### Attention value scales with distance, not relevance

A highway billboard's audience is in transit; the business is not co-located with the sign.
There, attention dominates because wayfinding is irrelevant (you're not about to walk in).
A small business's building sign is co-located with the business; the audience has already
arrived in the vicinity. At that range, viewers are already in **wayfinding mode** —
they are asking "is this the place?" not "should I care about this business?"

This means the value function of signage is not monolithic. It is **distance-dependent**:

```
Distance > 1 mile    → attention / brand awareness dominates
Distance 100ft–1mi  → identity assertion / category recognition
Distance 0–100ft    → wayfinding precision dominates
```

For a small business's on-premises sign, nearly all viewers are in the 0–100ft zone.
Therefore, for this sign type, **wayfinding is primary**.

### Pricing implication

If wayfinding is primary, sign value should correlate with:
- **Foot traffic volume** at the location (more people → more wayfinding events resolved)
- **Location difficulty** (how hard is this address to find without a sign? second-floor office vs. corner-lot retailer)
- **Legibility at approach speed** (walking vs. driving affects how much wayfinding work the sign can do)

Pricing by material, size, or square footage is a proxy for these — but only a rough one.
A 2 sq ft sign on a hard-to-find office door may provide more wayfinding value than a 20 sq ft sign on a corner store
that everyone already knows how to find.

### First-principles answer

> The primary unit of value in commercial signage for a small business is **wayfinding precision at point of presence**.
> Identity and attention are secondary. Persistence is a multiplier. Pricing models that use impressions/CPM
> are importing an attention-model frame that fits billboards but misidentifies what small-business customers
> actually buy.

---

## Step 3 — Corpus Answer

The out-of-home (OOH) advertising industry uses **CPM (cost per thousand impressions)** as its standard
value metric. The Outdoor Advertising Association of America (OAAA) publishes impression data; media buyers
use it to compare OOH to digital and broadcast. The International Sign Association (ISA) publishes economic
impact studies correlating signage quality with revenue — but these studies measure correlation, not value decomposition.

Academic marketing literature frames small-business signage value through:
- **Mere exposure effect**: repeated visual contact builds familiarity and preference
- **Salience at moment of purchase** (somewhat aligned with wayfinding, but framed as advertising recall, not navigation)
- **Signage as a brand-quality signal** (identity frame)

Small business advisory literature (SCORE, SBA resources) advises on signage primarily as a branding/awareness tool.
No mainstream corpus source identifies wayfinding-at-point-of-presence as the distinct, irreducible primary value
for on-premises small business signs.

---

## Step 4 — Delta

**Category: novel**

The corpus defaults to the attention/impression model (CPM, brand awareness, mere exposure).
The first-principles derivation identifies wayfinding-at-point-of-presence as the distinct primary value —
a function no other medium substitutes, independent of the attention or identity functions.

The corpus has no "wayfinding-first" pricing model for commercial signage. The distance-dependent value function
(attention at distance, wayfinding at proximity) is not a framing the OOH/ISA literature applies to small business
on-premises signs.

### Implications for Brand 9 Signs

1. Sales conversations should lead with wayfinding outcomes, not impressions or brand aesthetics
2. Quoting could incorporate a "location difficulty" factor in addition to material/size
3. Hard-to-find locations (industrial parks, second floors, shared buildings) are an underserved segment —
   their willingness to pay is highest because the wayfinding gap is largest
4. The competitor frame of "we do great-looking signs" competes on identity; a wayfinding frame is differentiated

---

## Commentary

The attention-model bias in signage pricing is likely inherited from the billboard/OOH industry, which predates
small-business on-premises signage as an industry category. The metrics were designed for a different sign type
at a different distance regime and were never re-derived for proximity signage. This is a common pattern:
an industry inherits a measurement framework from an adjacent domain without checking whether the primitives transfer.
