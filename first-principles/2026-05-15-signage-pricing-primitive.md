# First-Principles Spike: What Is the Correct Pricing Primitive for Commercial Signage?

**Date:** 2026-05-15
**Question:** What is the correct pricing primitive for commercial signage — cost-plus, value-based, or attention-based?
**Delta category:** novel

---

## Step 1 — The Question

Sign shops price their work. The question is whether the pricing primitive they use (cost of materials and labor) is the *correct* one, or whether a better primitive exists and is being systematically ignored.

---

## Step 2 — First-Principles Reasoning

### What does a sign actually do?

A commercial sign is a physical artifact placed in fixed space to communicate information (identity, location, offer, wayfinding) to observers who move through that space. Unlike digital media, it is:
- **Durable** — measured in years, not seconds
- **Location-fixed** — it cannot be retargeted
- **Impression-passive** — audiences encounter it by moving through space, not by being served an ad

### What generates value for the buyer?

The buyer (a business) pays for a sign because they expect a return. Their value equation, worked from primitives, is:

```
V = (incremental visitors per day) 
  × (avg transaction value) 
  × (repeat rate multiplier) 
  × (sign lifetime in days)
  + (brand recognition lift × long-term LTV effect)
```

This is a cash-flow model. The sign is an investment, and its NPV should exceed its cost for the purchase to be rational.

### What does a cost-plus model actually measure?

Cost-plus measures the fabricator's *inputs*:

```
Price = (materials + labor + overhead) × (1 + margin%)
```

This ensures cost recovery and a fixed profit margin. It is **independent of the sign's economic value to the buyer**. A sign in a high-traffic downtown corridor and a sign in a low-traffic industrial park cost the same to fabricate — and thus get priced identically — despite delivering radically different economic value.

**Structural distortion:** Cost-plus systematically underprices signs in high-value locations and may overprice them in low-value ones, but since most buyers comparison-shop fabrication rather than value, the industry never gets corrective signal.

### Can value-based pricing work here?

Value-based pricing would set price as a fraction of the buyer's expected economic return. Theoretically correct, but practically broken for sign shops because:
1. The fabricator does not know the buyer's revenue or conversion rate
2. The buyer has no incentive to disclose it honestly
3. Multiple shops fabricate equivalent signs — no lock-in creates downward pricing pressure
4. Verification is impossible — you can't A/B test a sign at a fixed location

### The attention-based alternative

Signs are physically similar to static outdoor advertising (billboards). The outdoor ad industry already has a pricing primitive: **CPM — cost per thousand impressions**.

Inputs that are *measurable and largely public*:
- **Traffic count** at location (DOT/municipality data, often free)
- **Sign visibility window** (seconds of exposure per pass — function of approach speed and sight line)
- **Sign lifetime** (material and installation quality)

Example calculation:
- Location: 8,000 vehicles/day intersection
- Sign lifetime: 10 years → 3,650 days
- Total impressions: 8,000 × 3,650 = **29.2 million impressions**
- Static billboard CPM in US markets: ~$3–$8
- At $5 CPM → implied media value: **$146,000**

A sign fabricated for $4,000 at cost-plus is priced at **2.7% of its attention value**. The fabricator is leaving 97.3% on the table — captured by the building landlord (via rent), the municipality (via location approval), and ultimately the sign buyer.

### The correct primitive from first principles

The sign delivers value through **impressions × message quality × duration**. The fabricator controls message quality (design, legibility, material) and duration (build quality). Location (traffic × visibility) is the customer's variable — but it is *knowable* by the fabricator if they ask.

**Optimal pricing structure (derived):**
```
Price = fabrication cost floor
      + design quality premium (complexity, legibility engineering)
      + location multiplier (f(daily traffic × visibility factor × lifetime))
```

This is a hybrid: cost floor ensures no fabrication losses; location premium captures value upside.

**Why doesn't the industry do this?**
1. Fabricators lack the mental model of "sign as media" — they think "sign as product"
2. Traffic data exists but isn't part of the sign sales process
3. Buyers resist paying a location premium — "I'm paying for the sign, not my own corner"
4. Sales reps aren't trained to have the location-value conversation
5. The Sign Pricing Guide and industry tools formalize cost-plus, creating path dependency

**Strategic implication for Brand 9 Signs:**
Any shop that can (a) pull traffic data for a customer's address, (b) translate it into impression value, and (c) use it to justify and capture a location premium is operating at a fundamentally higher pricing tier than cost-plus competitors. The buyer gets a compelling ROI story; the shop gets margin expansion on its highest-value jobs.

---

## Step 3 — Corpus / Orthodox Answer

Industry standard (ISA, Sign Pricing Guide, Signs101, shopVOX, SignCraft) is **cost-plus with material multipliers**:

- Common formula: `materials × 2 + labor hours × shop rate`
- Simplified alternative: `materials × 5` (for routine work)
- Square-footage pricing: $10–$300/sq ft by sign type
- Industry tools (Sign Pricing Guide since 2005) survey successful shops and produce cost-based rate tables
- ISA and trade press frame pricing as "how do I recover costs and hit margin targets" — not "how much value am I delivering"

The corpus makes **zero mention** of:
- Attention-based pricing
- Location quality as a pricing input
- Impression value or lifetime media value
- Buyer ROI as a pricing justification
- Traffic data as a sign pricing variable

Value-based pricing is discussed in general SMB pricing literature but is absent from sign industry trade resources.

---

## Step 4 — Delta Analysis

**Category: novel**

The first-principles derivation arrives at a hybrid cost-floor + attention-based model that the industry corpus does not contain. This is not a case of the corpus being wrong — cost-plus is a rational response to a commoditized fabrication market with no information asymmetry on buyer value. But it is incomplete.

The novel framing: **a sign is a media asset, not just a fabricated product, and the media value is calculable from public traffic data.** Sign shops that adopt this framing can capture a location premium on their highest-value jobs, justify it with data, and differentiate from pure cost-plus competitors.

The delta is not "the corpus got the math wrong" — it's "the corpus is using the wrong variable as the pricing primitive."

---

## Commentary

The cost-plus habit in sign shops is structurally similar to early software pricing by lines of code, or law firm billing by hours rather than outcomes. It solves the seller's cost-recovery problem without touching the buyer's value problem. The transition to attention-based thinking would require:
1. A data workflow (pull traffic counts at quote time)
2. A pricing model (location multiplier table)
3. A sales narrative ("here's the media value of your sign location")
4. Enough market differentiation that the buyer can't immediately comparison-shop the premium away

Brand 9 Signs operating in commercial real estate corridors (Hartley Capital assets, high-traffic retail) is positioned in exactly the segment where this premium is largest and most defensible.

---

*Spike authored by AP agent, 2026-05-15*
