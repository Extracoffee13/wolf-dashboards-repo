# Spike: What is the true unit of value in commercial signage?

**Date:** 2026-06-05
**Question slug:** signage-unit-of-value
**Delta category:** rediscovered

---

## The Question

What is the true unit of value in commercial signage — the physical artifact or the attention it generates?

This matters for Brand 9 Signs because pricing, positioning, and sales strategy all flow from what you believe you are actually selling.

---

## Step 2 — First-Principles Reasoning

### Start from primitives

**Value** = what a buyer willingly pays for because it makes them better off.

A sign has two components:
1. A physical object (substrate, materials, ink, structure, installation hardware)
2. A communication function (it says something to someone who passes by)

Why does a business buy a sign? Walk the causal chain:

> Buy sign → sign is seen by passersby → passerby becomes aware of business → subset visits → subset converts to customer → revenue

Now perform the inversion test: if the sign is fabricated perfectly but placed in a dark alley that nobody walks through, what is its value? **Zero.** The physical artifact is present; the value is absent. Value is therefore not in the artifact.

Now invert again: if a hand-painted cardboard sign in imperfect lettering sits on a corner where 40,000 cars pass per day, what is its value? **Substantial.** The artifact is cheap; the value is high.

**Conclusion: The unit of value is the attention event — a human moment of awareness triggered by the sign.**

### What makes an attention event valuable?

Three variables determine an attention event's worth:

1. **Volume:** How many people see the sign per unit time (daily impressions)
2. **Qualification:** Are those people prospects for this business? (targeted impressions)
3. **Effectiveness:** Does the viewer understand, remember, and respond? (conversion rate)

The sign's total delivered value is therefore:

> `V = daily_impressions × qualification_rate × conversion_rate × avg_customer_value × sign_lifespan_days`

Every factor except `sign_lifespan_days` is fixed by location, audience, and message design — not by material cost.

### The ownership vs. rental distinction

This is the structural fact that separates fabricated signage from advertising:

- **Rented attention (advertising):** You pay per impression. Stop paying → impressions stop. This is an **opex model** for attention.
- **Owned attention (signage):** You pay once. Impressions continue for the life of the asset. This is a **capex model** for attention.

In the capex model, once the sign is installed, the marginal cost per additional impression approaches zero. A sign lasting 10 years in a location with 10,000 daily impressions delivers ~36.5 million impressions for the price of one fabrication run. At a typical $4,000 install, that is $0.00011 per impression — a fraction of any other media channel.

### Pricing implication from first principles

If value = lifetime impression volume × quality, then correct pricing should be:
- **Location quality (traffic count):** high weight — multiplies all future impressions
- **Durability (lifespan):** high weight — extends the impression window
- **Material cost + labor:** moderate weight — contributes to durability and visibility, but is not the value itself

A cost-plus pricing model (material + labor + overhead + margin) captures none of this. It prices the wrong thing. The rational alternative: price on expected impression yield, or at minimum use impression value to justify a premium over commodity fabrication costs.

### The agent architecture implication

For a sign-sales agent (e.g., a Construct AI agent quoting customers), this means the value demonstration script should anchor on:

> "At your location's traffic count, this sign will be seen approximately X times per day. Over its 10-year lifespan that's Y total impressions. At $Z installed, you're paying [$Z/Y] per impression — compare that to $2–$6 CPM for digital display."

This reframes the sale from "how much sign do I get for my money" to "how much owned media am I acquiring."

---

## Step 3 — Corpus Answer

### OOH / Billboard industry

The Out-of-Home advertising industry has fully internalized impression-based value for **rented** signage (billboards):

- **DEC (Daily Effective Circulation):** traffic count × visibility adjustment × proportion in the audience segment — the standard currency for buying/selling billboard space
- **CPM:** $2–$7 for OOH, among the lowest of all media channels
- **Geopath:** the nonprofit that provides standardized audience measurement, combining DOT traffic counts, mobile location data, and visibility scoring
- **OAAA data:** billboards deliver an average 497% ROI ($6 return per $1 spent)
- Measurement hierarchy: DEC → OTC (Opportunity to Contact) → VAC (Visually Adjusted Contact)

### Fabricated sign industry

The fabricated sign trade prices almost entirely on cost-plus:
- Material + labor burden + overhead + margin
- Square footage, complexity, and substrate type as primary variables
- Sign industry trade press (Signs101, Sign Builder Illustrated) discusses pricing in terms of quoting accuracy, not impression yield

**However**, a minority voice in the corpus does articulate the impression framing for fabricated signs:
- Flexlume and similar vendors occasionally publish "cost per impression" comparisons for monument signs vs. other media
- The framing "owned attention infrastructure" appears in fragmented form across marketing content but is not a dominant industry model
- Vehicle wraps are more commonly priced with impression math because the comparison to digital CPM is stark

### The gap

The OOH industry knows impressions are the unit — for **rented** inventory. The fabricated sign industry hasn't systematically applied this to **owned** inventory. The pricing, sales, and customer-education gap is structural.

---

## Step 4 — Delta Comparison

**Category: rediscovered**

The core insight — impressions, not the artifact, are the unit of value — is not novel. The billboard industry has operated on this basis for decades via DEC and CPM metrics.

What is **underarticulated** in the corpus:
1. The **capex vs. opex framing** of owned vs. rented attention. The corpus talks about "one-time cost" but doesn't name the structural distinction cleanly.
2. The **agent sales script implication**: using impression math not just to justify signage vs. other media, but to justify premium fabrication vs. commodity, on the basis that durability multiplies lifetime impressions.
3. The **pricing correction**: most sign shops price on the wrong variable (cost) rather than the value variable (impressions). The corpus does not articulate a full alternative pricing model.

The first-principles chain independently arrived at the same conclusion as the OOH industry but extended it into a pricing model that the fabricated sign corpus doesn't have.

---

## Commentary

For Brand 9 Signs, the practical takeaway is operational:
- **Sales:** anchor on daily traffic count and sign lifespan before discussing materials
- **Quoting:** include a cost-per-impression comparison in every proposal above $2,000
- **Positioning:** "We build owned media, not just signs" — differentiates from commodity sign shops
- **Agent design:** a Construct quoting agent should pull traffic data for the client's address and compute lifetime impression estimate as part of the quote flow

The capex-model framing also has implications for financing conversations: if a sign is a media asset with a 10-year yield, it can be justified on an asset-purchase basis (depreciation, ROI payback period) rather than a discretionary spend basis.
