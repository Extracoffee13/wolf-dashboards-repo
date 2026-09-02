# First-Principles Spike — 2026-09-02

## Question

Why does sign letter height scale with legibility distance the way it does — i.e., is
there a first-principles reason behind rules like "1 inch of letter height per 10 feet
of viewing distance," or is it an arbitrary industry convention?

(Self-generated: no seeded backlog existed. Chosen for direct relevance to Brand 9
Signs operations — letter-height/viewing-distance sizing is a daily estimating and
proposal decision.)

## First-principles derivation (no retrieval)

Start from the geometry of vision, not from any remembered sign-industry number.

**1. The eye resolves angles, not absolute sizes.** A letter of height *h* viewed from
distance *d* subtends an angle θ ≈ h/d radians (small-angle approximation, valid for any
d that's large relative to h, which is always true for signage). This means legibility
is fundamentally a ratio (h/d), not either quantity alone — a "10-inch letter" and a
"1-inch letter" are equally legible if viewed from proportionally scaled distances. This
already explains, from geometry alone, why every legibility rule in the industry must
take the form "X feet per inch of height" rather than an absolute size.

**2. The eye has a fixed angular resolution floor.** Human foveal vision is limited by
photoreceptor spacing and optical diffraction to roughly 1 arcminute of two-point
resolution in a normal (20/20-defined) eye. Letter *recognition* (not mere dot
detection) requires resolving multiple internal features of a glyph — strokes, gaps,
curves — not just detecting that something is there. The classical optometric
definition of 20/20 acuity (the Snellen construction) sets the *whole letter* to
subtend about 5 arcminutes at the threshold distance, with the finest stroke/gap detail
at the underlying ~1 arcminute limit. So 5 arcminutes is a reasonable first-principles
floor for "an optotype is just barely identifiable by an ideal 20/20 eye, under ideal
high-contrast lab conditions, with unlimited fixation time."

**3. Real-world reading is not the lab case — it needs a safety margin.** A person
glancing at a sign while driving, walking, or scanning a shopping plaza differs from the
Snellen test in every way that matters: (a) fixation time is a fraction of a second, not
unlimited; (b) the target is a whole word in context, not an isolated forced-choice
optotype; (c) contrast, glare, and lighting are rarely lab-ideal; (d) population visual
acuity is worse than 20/20 on average (uncorrected refractive error, aging); (e) there's
vibration/motion if the viewer is moving. Each of these degrades effective resolution
independently, so a multiplicative safety factor is the right model, not an additive
one. A factor of roughly 2–6× over the 5-arcminute detection floor is a defensible
range: 2× for "static, well-lit, corrected-vision reading with a couple seconds to
look" up to 6× for "in-motion, split-second, mixed population, imperfect contrast."

**4. Converting angle back to a ratio.** θ (rad) = h/d ⇒ d/h = 1/θ.
- At 5 arcmin (0.001454 rad, pure threshold): d/h ≈ 688 → **≈57 ft per inch** — an
  upper bound, essentially unattainable in practice since it assumes lab conditions.
- At ~11–12 arcmin (≈2.3× margin): d/h ≈ 287 → **≈24–25 ft per inch** — a "technically
  identifiable, if you concentrate" distance.
- At ~29 arcmin (≈5.7× margin): d/h ≈ 120 → **≈10 ft per inch** — a "comfortable,
  no-strain, quick-glance" distance.

So first principles alone predict a *family* of valid ratios spanning roughly 10–25+
feet per inch of letter height, not a single number — with the specific ratio
determined entirely by how much margin you build in for real-world viewing conditions
versus laboratory acuity. The industry doesn't need one rule; it needs to specify which
point on this curve it's quoting (max theoretical distance vs. comfortable/attention-
getting distance), because both are "true" depending on the question being asked.

## Corpus answer (post-derivation search)

Sign industry sources (Signazon, Signs.com, US Sign Council-derived guidance) converge
on: **"1 inch of letter height ≈ 10 feet of readability"** as the standard rule of
thumb for effective, comfortable readability — attributed to US Sign Council research
and used industry-wide for decades. The same sources separately note that a 20/20 eye
can *technically* read a 6-inch letter up to 150 ft away (25 ft/inch), while the same
letter is considered "easily/comfortably readable" from only 60 ft (10 ft/inch) — i.e.
the corpus itself carries two different numbers for two different definitions of
"legible," without deriving either from acuity physics.

## Delta: rediscovered

The derived range (≈10 ft/inch at the "comfortable/quick-glance" margin, ≈24–25 ft/inch
at the "technical maximum" margin) lands almost exactly on both published numbers
(10 ft/inch and 25 ft/inch), despite being produced with zero lookup — just Snellen
geometry plus a reasoned safety-margin multiplier. That's a clean rediscovery of the
known industry constants from visual-acuity first principles.

The one thing the derivation adds that the corpus doesn't state outright: *why* two
different "correct" ratios (10 ft/inch vs. 25 ft/inch) coexist in sign-industry
literature without contradiction — they're the same acuity floor scaled by different,
implicit safety margins (viewing-condition assumptions), not competing claims. The
corpus presents both numbers as empirical facts side by side; the derivation explains
them as the same underlying model evaluated at two different margin settings, which
also predicts *when* to use which number (comfortable/impact sizing vs. worst-case
minimum sizing) rather than just citing both.

## Practical takeaway for Brand 9 Signs

For proposal sizing, default to the 10 ft/inch comfortable-reading ratio (matches
"impact" sizing) but note to clients requesting minimum-viable sizing (e.g. tight
setback, budget-constrained monument signs) that 20–25 ft/inch is defensible as a
technical floor — with the explicit caveat that it assumes good contrast, static
viewing, and corrected 20/20 vision, none of which hold for a driver at 35 mph in low
light. The acuity-margin framing gives a principled way to push back when a client asks
"can we go smaller" — the answer is a quantified tradeoff, not a shrug.
