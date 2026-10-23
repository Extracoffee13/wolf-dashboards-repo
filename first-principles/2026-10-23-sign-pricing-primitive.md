# Spike: What is the irreducible pricing primitive for a custom sign?

Date: 2026-10-23

## First-principles answer (derived before any lookup)

Price must cover what the seller gives up to produce the thing, plus a margin for risk and for the capital in the business. A sign is a made-to-order physical object, so the seller gives up four things:

1. **Materials.** These scale with face area (substrate, vinyl, paint, LEDs) and with perimeter and depth for dimensional work (returns, trim cap, routed edges). Area is the dominant driver for flat signs.
2. **Machine time.** The CNC router, the printer and the vinyl cutter are capital assets with a fixed hourly cost. Time scales with area for printing and with path length and complexity for routing. A tiny intricate piece can cost more per square foot than a big plain one.
3. **Human labour.** Design, prepress, finishing, painting, assembly, install. Part of it is fixed per job (artwork, setup, file prep, quoting), and part scales with size. Install is its own regime: crew time, travel, lift or crane, permits, and the risk of working at height.
4. **Fixed overhead per job.** Quoting, project management, shipping or delivery, and the cost of getting it wrong (a reprint).

So price = fixed per-job cost + variable cost × size + install + margin. The variable part has no natural unit except area (or linear length for channel letters, edge-lit work and similar). Shops therefore quote **per square foot** because area is the one measurable quantity that tracks both material and machine time for most products. The fixed part explains why a single small sign has a minimum price. The price per square foot falls as size grows, because the fixed cost is spread over more area, and rises for complexity, because machine and labour time grow faster than area.

Prediction: the quote is not a pure area × rate. It is a tiered rate card (per-sq-ft by product class) with a minimum charge, a setup/design line, and install priced separately by crew-hours. Volume discounts should appear where setup is amortised (repeat sign types across a community or a franchise). Margin should differ by product class, higher on custom/one-off and lower on commodity items such as coroplast yard signs.

Implication for Brand 9: the quote engine's primitive should be product class × area × complexity tier, plus fixed setup, plus install by crew-hours, and it should track fixed and variable cost separately so the repeat-order discount is a derived number, not a guess.

Confidence in the structure: high. Confidence in the specific numbers: none, because I derived no figures.

## Corpus answer

Standard practice, from sign-shop forums and cost guides ([signs101 minimum charges](https://signs101.com/threads/minimum-charges.60212), [signs101 small-work pricing](https://www.signs101.com/threads/pricing-for-small-work-like-store-hours-signs.167540), [HomeAdvisor](https://cost-guide-ssr.homeadvisor.com/cost/safety-and-security/make-and-install-signs/)):

- Price per square foot by material or product class, plus a base fee that varies by product (one shop: $10 base + $1.44/sq ft) or a minimum charge.
- Installation billed separately, and usually not included in the per-sq-ft figures.
- Size is the biggest driver; lighting/electronics, thickness, finish, quantity and mounting are separate lines.
- Rough ranges are $15-35/sq ft for plastic, aluminum and steel, $10-100 for basic, and $150-300 for high-end including install. These are mixed-quality sources and I treat the figures as rough.

## Delta: **rediscovered**

The structure matches: area as the main variable, a fixed per-job floor (base fee or minimum), install priced separately, and rates varying by product class. I did not find a source for the volume-discount-from-amortised-setup prediction or the complexity-over-area point. Both are plausible and untested, so I am not claiming them as novel.

## Commentary

- Reasoning from cost sources reached the orthodox answer without retrieval, which supports using first principles to sanity-check the B9 quote engine.
- Open gaps: the numbers (I derived none) and the complexity premium. The search was one standard query on thin sources; a B9 job-cost history would settle both better than the web.
- Confidence in the delta call: 0.6.
