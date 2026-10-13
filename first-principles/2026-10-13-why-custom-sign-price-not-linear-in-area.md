# First-Principles Spike — 2026-10-13

**Question:** Why does a custom sign's price not scale linearly with area, and what is the real unit of pricing?
(Backlog was missing/empty; question self-generated from Brand 9 Signs operations.)

## First-principles answer (derived before any lookup)
Decompose a job's cost into components and ask how each scales with a sign's linear size L:
- **Fixed per job** (design/proofing, permit paperwork, setup, truck roll, minimum crew trip): scales as L^0. Dominates small signs, so price per sq ft falls as size rises.
- **Material** (face panels, sheet stock): scales with area, L^2.
- **Edge work** (routing, returns, trim cap, LED modules, wiring on channel letters): scales with perimeter or letter count, L^1. For letter-based signs this, not area, is the dominant variable cost.
- **Install**: scales with access, not size. It is a step function: ladder, then lift, then crane, then engineered footing. Each threshold adds a discrete jump.
- **Margin**: roughly proportional to the sum.

So total cost is an affine curve at small sizes (fixed term), steps at access/shipping/engineering thresholds, then roughly L^1 to L^2 growth, depending on the product. No single unit fits every product. The honest unit is the dominant variable driver: sq ft for flat faces, perimeter or letter height for channel letters, hours and trips for install. Sq ft survives as a quoting unit because it is easy to communicate, but it is a proxy that hides the fixed and step terms.

## Corpus answer
Shops price per the same drivers. Channel letters are quoted per vertical inch (one forum shop: about $19 remote, $21 raceway, $22 reverse channel) or flat per letter below a size threshold. Flat panels and vinyl are quoted per sq ft. Font complexity adds surcharges. Permit, electrical, delivery and install are added separately, and shops set minimums. Sources are anecdotal and conflicting (signs101 threads, consumer cost guides).
- https://www.signs101.com/threads/vertical-inch-channel-letter-pricing.180201/
- https://www.signs101.com/threads/channel-letters-and-upright-inches.121240/

## Delta: **rediscovered**
Independent derivation matches: a per-job fixed term, a unit tied to the dominant driver (height or perimeter for letters, sq ft for flats), and install and permits as separate items. One small gap in the corpus: it does not frame install as a step function (access thresholds). That is mild and unverified, so it is not scored novel.

## Commentary
Practical use for B9 quotes: keep fixed, unit, and install as separate lines, and flag access thresholds (lift/crane) as explicit price steps. The web sources are weak (forum anecdotes), so the match validates the structure, not any specific number.
