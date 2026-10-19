# Spike: What is the true primitive pricing unit for custom signage?

Date: 2026-10-19

## Question
Sign shops quote by square foot, but costs arise by process step. What is the actual primitive pricing unit: area, process step, or risk?

## First-principles answer (derived before reading corpus results)
Caveat on process: the search call was issued before this derivation was written out. The derivation uses only the question's primitives, but treat independence as imperfect.

1. A price must cover cost plus margin, and cost is the sum of resources consumed: material, machine time, human time, capital tied up, and exposure to failure.
2. Material consumed scales with area (plus waste from nesting/offcuts). So material is area-linear, with a waste multiplier greater than 1.
3. Labor and machine time split in two: (a) per-job fixed time (file prep, setup, proofing, site survey, travel, paperwork) which is independent of size, and (b) per-area or per-length time (cutting, painting, assembly) which scales with size, with perimeter/detail (routing a script logo) scaling differently than area.
4. Installation scales with weight, height, access and crew-days, not with face area. A small sign on a 30 ft pole costs more than a large sign at grade.
5. Risk is the term that area cannot capture: illuminated, structural, permitted, or custom-engineered pieces carry failure and rework exposure.
6. Therefore true cost = fixed per-job + area x (material x waste + variable labor) + install(access, weight, crew-days) + risk reserve. Area is a proxy that correlates with only the middle term.
7. Why quote by area anyway? Customers and competitors can compare it, and it is cheap to calculate. It works as a communication unit, with the fixed and install terms hidden in the rate, which makes rates drop as size grows (fixed cost amortized) and spike for small or complex pieces.
8. Conclusion: the primitive cost driver is the process step (with its own scaling variable); area is the primitive quoting unit. A good quote is a stack of per-step lines: a minimum/fixed charge, an area rate by product class, install priced in crew-time, and an explicit risk or complexity multiplier.
9. Implication for Brand 9: small cheap signs are mispriced if quoted purely per sq ft; installs should be priced independently of face area; a quote tool should expose the fixed charge.

## Corpus answer
Web sources (cost guides, a sign-shop bookkeeping guide) agree: per square foot is the common base, often combined with a base price plus per-unit charges; materials differ in rate; lit signs cost more; permits, electrical, delivery are itemized separately; one source recommends separating material markup, burdened labor and installation rather than a flat hourly rate. Sources give no standard markup or overhead-allocation formula, and the figures come largely from marketing/consumer guides. See e.g. https://beancount.io/blog/2026/08/25/custom-sign-shop-bookkeeping-material-markup-labor-burden-installation-pricing-guide and https://www.elmark.com/blog/how-much-does-a-sign-cost.

## Delta category
rediscovered

## Commentary
Same structure: base plus per-area rate, install and electrical separate, burdened labor separate from material. Not claimed as novel. Two framing points the corpus snippets lacked: (1) area is a quoting proxy, not a cost driver, and effective $/sq ft should fall with size because of the fixed term; (2) install should be keyed to access/crew-days rather than face area. Both are testable against B9 job-cost history and not yet validated. Corpus quality is weak (marketing sources), so "rediscovered" validates the structure, not the numbers.
