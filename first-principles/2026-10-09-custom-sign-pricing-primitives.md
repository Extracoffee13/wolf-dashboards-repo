# First-Principles Spike — 2026-10-09

## Question
Why does a custom sign cost what it costs? What is the minimal primitive pricing model?

> Process note: the web search was dispatched in the same turn as the backlog write, before the derivation was written down. The derivation below was reasoned without consulting results, but it was recorded after the corpus result was visible, so treat "independent" with that caveat. Future spikes: write the derivation to disk before any search call.

## First-principles answer
A price must cover what the seller gives up and leave a reason to keep doing it. A sign is a manufactured, installed, one-off object, so the seller gives up:

1. **Matter** — material consumed, including what is cut away. A sign uses more stock than it shows: kerf, offcuts, and failed pieces mean cost = shown area / yield. Yield is a property of the shop and the job geometry, not the material.
2. **Time of skilled people** — design, prep, fabrication, finishing, install. Time is priced at what the person *costs the business* (wage + taxes + insurance + benefits), not the wage. Install adds travel and a two-person crew, and crew time is idle-sensitive.
3. **Time of machines and space** — a router, printer, paint booth and building are rented or depreciated whether or not they run. This is a fixed cost, so it only becomes a per-job cost by dividing across *sellable hours*. The divisor is the key variable: a shop that sells 50% of its hours must charge double the overhead per hour that a 100%-utilized shop would.
4. **Risk** — a custom item has no resale. If the client walks, the unit is scrap. Errors, remakes, weather on install day, and slow-paying clients are expected losses and must be priced in as a premium, in proportion to how custom and how large the job is.
5. **Money's time value** — materials are bought before the deposit clears; large jobs lock up capital.
6. **Profit** — the return that makes owning the shop better than being employed elsewhere. It is not a leftover; it is the payment for risk and capital.

So: price = (matter / yield) + (hours x loaded rate) + (overhead rate x machine/shop hours) + risk premium + capital cost + profit. Almost all of this scales with **hours and complexity, not area**. Area only matters as a proxy for matter and for hours. That predicts: (a) a small, intricate sign can cost more per square foot than a big plain one; (b) per-sq-ft price lists work only inside one product type and break across types; (c) setup cost (design, programming files, machine setup) is paid once per *job*, so quantity discounts are real and steep, and a one-off carries the whole setup; (d) install, permits and site conditions can rival or exceed fabrication because they are time, travel and risk, not matter; (e) the market ceiling is the customer's alternative (another shop, a cheaper product, no sign), so cost sets a floor and value sets a ceiling. The real price lives in between and is decided by competition and perceived value, which is why cost-plus is a floor-check, not a strategy.

Minimal primitive set: **{matter/yield, loaded labor hours, utilization-adjusted overhead, risk, profit}**, bounded above by customer alternatives.

## Corpus answer
Standard sign-industry guidance (SignShop, Graphics-Pro, bookkeeping/job-costing guides) is cost-plus: bill of materials + consumables allowance (~7%) + waste/scrap (5-10% on vinyl/ACM), labor at a *burdened* rate (e.g. $25 wage -> $30-35 loaded; shop rates roughly $60-70/hr), overhead = monthly overhead / available production hours, then a deliberate margin on top. Also: benchmark against wholesale quotes and track actual scrap and per-job costs.

## Delta category
**rediscovered** — Every corpus component maps to a derived primitive (waste = yield, burden = loaded cost, overhead/available hours = utilization divisor, margin = profit). Two nuances from the derivation are only weakly present in the corpus excerpts: an explicit **risk premium** scaled to customness, and the framing of cost-plus as a **floor** under a value-set ceiling. These are not strong enough to call novel.

## Commentary
- Confidence in the match is moderate: the corpus check was a single standard-mode search of vendor and trade blogs, which are weak, secondary sources.
- Action for Brand 9: the load-bearing variable is the overhead divisor (available vs. *sold* hours). If B9 quotes on available hours while real utilization is lower, every job underprices. Worth checking against actual booked hours.
- Useful test for estimates: if price/sq ft is the only input, the model is missing setup, complexity and install.

Sources:
- https://www.signshop.com/business-mgmt/sales-a-marketing/understanding-sign-pricing/
- https://graphics-pro.com/education/pricing-signs-and-graphics-profitably/
- https://beancount.io/blog/2026/08/25/custom-sign-shop-bookkeeping-material-markup-labor-burden-installation-pricing-guide
