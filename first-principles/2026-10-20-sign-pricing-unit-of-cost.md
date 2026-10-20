# First-Principles Spike — 2026-10-20

## Question
Why is custom signage priced per square foot, and what is the real unit of cost in a sign job?
(Backlog file was missing/empty; question generated from Brand 9 Signs operations.)

## First-principles answer (derived before any search)
1. A sign has four cost layers: materials, fabrication labor, install, overhead + margin.
2. Materials are bought by area (sheets/rolls), so material cost scales with area. $/sqft is a good proxy for it.
3. Fabrication labor scales with area (print, laminate), perimeter/path length (CNC, cutting), complexity (pieces, letters, layers) and fixed setup (file prep, proofing).
4. Install labor does not scale with area. It scales with height, access, site conditions, travel and crew-hours. Permits and engineering are separate.
5. Per-job fixed costs (design, proofing, PM, quoting) are the same for a small sign and a large one.
6. True cost is approximately: fixed setup + k1*area + k2*perimeter + k3*complexity + install hours * crew rate + risk.
7. $/sqft survives because it is easy for buyers to compare, area dominates variable cost for flat print/panel products, and a rate card is cheap to quote from.
8. It breaks at the extremes: small signs are dominated by fixed cost, large simple signs by install, dimensional/illuminated signs by labor and electronics.
9. Predictions: $/sqft per product class, a minimum charge, install priced separately, and per-letter or per-inch pricing for dimensional letters.
10. Implication for B9: quote as setup + area-based materials + a product-specific labor driver + install hours, not one blended rate.

## Corpus answer
Web search (forums and consumer cost guides, mostly anecdotal and some low-quality SEO content):
- Shops split material, labor and install rather than one flat rate; one guide warns a single rate undercharges complex illuminated work.
- Vinyl is often priced per sqft; cut lettering per letter with volume breaks.
- A shop minimum covers paperwork time (reported range roughly $25 to $87.50).
- Install is priced separately (flat for windows/vehicles, hourly otherwise, with offsite minimums and travel).
- No single standard formula; the common outline is material + burdened labor + permits/install, then markup, subject to the minimum.

Sources:
- https://beancount.io/blog/2026/08/25/custom-sign-shop-bookkeeping-material-markup-labor-burden-installation-pricing-guide
- https://signs101.com/threads/whats-your-shop-minimum.86967/page-2
- https://sawmillcreek.org/threads/vinyl-letter-pricing.67050/

## Delta category
**rediscovered**: every structural prediction (per-class $/sqft, minimum charge, separate install, per-letter for dimensional work, single-rate failure at the extremes) matches the corpus.

## Commentary
The corpus is thin and anecdotal, so this is validation of the structure, not of any numbers. The one thing the corpus did not state explicitly is the perimeter/path-length driver for CNC work and the fixed-setup-vs-area decomposition as a cost model. That is a candidate for B9's quoting engine, but it is untested against real job data.
