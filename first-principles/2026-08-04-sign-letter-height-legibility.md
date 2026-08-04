# First-Principles Spike — 2026-08-04

## Question

From first principles (no lookup), how tall should letters on a road-facing
business sign be, as a function of traffic speed, for a driver to notice,
read, and act on it in time?

*(Chosen ad hoc — `first-principles-backlog.md` didn't exist yet in this
repo, so I seeded it as an empty queue and generated today's question
directly, picking one relevant to Brand 9 Signs' core business: signage
sizing.)*

## First-principles answer (derived before any search)

Two independent constraints multiply together: an **optical** constraint
(how large must letters appear, angularly, to be legible at all) and a
**kinematic/behavioral** constraint (how much distance — hence how early —
the sign needs to already be legible, given closing speed and how long
noticing + reading + deciding takes).

**Optical constraint.** Standard visual acuity (Snellen "20/20") is built
around resolving a ~1-arcminute gap under ideal, static, high-contrast,
fixated conditions. Reading a whole word while driving is harder in several
independent, multiplicative ways: (a) real-world driver acuity averages
worse than 20/20 (~2x), (b) whole-word gestalt recognition needs more
angular size per letter than single-gap detection (~1.5x), (c) the sign and
eye are both moving, smearing the retinal image during a short glance
(~1.5-2x). Stacking these gives roughly 5-6x degradation from the 1-arcmin
ideal, so I adopted ~20 arcminutes (1/3°) as the effective per-letter
threshold. Converting: distance(ft) ≈ 14.3 × height(in) — i.e., a 1-inch
letter becomes legible around 14 feet away, by this construction.

**Kinematic constraint.** The driver needs total time T for: noticing the
sign, reading a short name (~1 sec/word under divided attention), deciding
relevance (~1 sec), and beginning a physical reaction to an *unexpected*
stimulus (longer than the ~1.5s reflex figure used for expected hazards). I
used T ≈ 5 seconds. Required sight distance = speed × T.

**Combine.** height(in) = (speed(ft/s) × 5) / 14.3, which collapses (since
everything is linear in speed with the same constants) to:

    height(in) ≈ 0.5 × speed(mph)

E.g., a business on a 35-mph road needs ~17-18" letters to be reliably read
and acted on in time. Full derivation and intermediate numbers in the
session transcript.

## Corpus answer

The United States Sign Council (USSC) — the industry body whose research
underlies most sign-code legibility standards — publishes exactly this kind
of speed-indexed table, framed with the same "seconds of readability"
concept I used independently:

- At 30 mph: 8" letters for 5 seconds of readability (4" for 3 seconds)
- At 60 mph: 16" letters for 5 seconds of readability (8" for 3 seconds)
- At 55 mph, a sign must be legible from ~440 ft to be detectable and readable

This is also linear in speed for a fixed time budget: height(in) ≈
0.267 × speed(mph), i.e. roughly 1 inch of letter height per 3.75 mph.

Separately, a more commonly cited "rule of thumb" (also USSC-derived, but
for general on-premise retail signage rather than the speed/time-budget
framing) is **1 inch of letter height per 10 feet of viewing distance**,
and highway/wayfinding signage uses a looser Legibility Index of roughly
1 inch per 40-50 feet.

Sources:
- [USSC Sign Legibility Rules of Thumb (PDF)](https://files.secure.website/wscfus/7691102/uploads/USSC_Sign_Legibility_Rules_of_Thumb.pdf)
- [Signazon: Sign Letter Height Visibility Chart](https://www.signazon.com/help-center/sign-letter-height-visibility-chart.aspx)
- [Sign Knights: Sign Visibility & Viewing Distance Guidelines](https://www.signknights.com/sign-visibility-and-viewing-distance-guidelines/)

## Delta

**Category: rediscovered** (with a quantified miss on the constant)

I independently arrived at the same *mechanism* and *functional form* the
industry uses: split legibility into an optical (angle-based) term and a
kinematic (speed × time-budget) term, and the result is linear in speed for
a fixed reading-time target — exactly the shape of USSC's own 30mph/60mph
table. That's a real validation of the reasoning chain, not a coincidence:
both derivations are forced into the same shape by the same physics
(constant angular threshold × constant time budget ⇒ linear in speed).

Where I missed: my required letter heights ran ~1.9x larger than USSC's at
matched speed and matched 5-second time budget (e.g. 15" vs 8" at 30mph).
Backing out USSC's implied optical constant, their effective legibility
distance is ~27.5 ft per inch of letter height, against my assumed 14.3
ft/inch — meaning their effective angular threshold is close to ~10-11
arcminutes, not the ~20 arcminutes I stacked up from first principles. I
over-penalized the "moving glance + divided attention" degradation factors
by roughly 2x. The error is precisely localized: not the model structure,
one specific empirical constant (the effective driving-legibility angular
threshold) that no amount of reasoning from optics primitives alone gets
you — it needs actual behavioral measurement.

**Commentary:** this is a clean illustration of where reasoning-from-primitives
earns its keep and where it doesn't. It cheaply and correctly recovers the
*shape* of a physical law (linear in speed, product of an optical and a
kinematic term) — the part that's "just physics + geometry" and that a
literature search would have handed over without any insight into *why*
it's true. What it can't recover without data is the *calibration
constant* — here, the empirically-measured effective angular threshold for
glance-reading under driving conditions, which folds in real human
perception/attention data that no amount of armchair optics stacking
reliably reproduces (my stacked-guess was off by ~2x, in the conservative
direction). The practical rule: use first-principles reasoning to derive
the correct functional form and to sanity-check or explain a retrieved
number, but don't trust a from-scratch numeric constant for anything that
ultimately traces back to measured human factors — go get the number.
