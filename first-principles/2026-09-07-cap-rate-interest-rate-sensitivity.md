# First-Principles Spike — 2026-09-07

## Question

When interest rates fall, why — and by how much — should real estate cap
rates fall? Is the relationship 1:1, more than 1:1, or less than 1:1?

Picked because it sits at the center of Hartley Capital's underwriting
(every deal's exit value assumption rides on this) and it has a clean
enough structure to actually derive instead of just quoting.

## First-principles answer (derived cold, no retrieval)

**Step 1 — define the object.** Cap rate is a current yield: `cap rate =
NOI / Price`, the real-estate analogue of an earnings yield (E/P) on a
stock.

**Step 2 — get a pricing identity from a growth perpetuity.** For a
stabilized asset whose NOI grows at a constant rate `g` forever, the
present value of that cash-flow stream is `P = NOI₁ / (r − g)`, where `r`
is the investor's required rate of return. Rearranging: `NOI/P = r − g`,
i.e. **cap rate = r − g**. This is just the Gordon growth model applied to
a building instead of a stock.

**Step 3 — decompose the discount rate.** `r = rf + rp`: a risk-free rate
(proxy: the 10-year Treasury) plus a risk premium compensating for
illiquidity, releasing/capex risk, and the opportunity cost of not holding
the risk-free asset instead. So:

`cap rate = rf + rp − g`

**Step 4 — the naive prediction.** Holding `rp` and `g` fixed, a fall in
`rf` of size Δ should move the cap rate by exactly −Δ. 1:1, full stop.
This is the version of the claim that gets repeated casually, and it's the
one worth stress-testing, because `rp` and `g` are not free-standing
constants — they respond to the same macro forces that just moved `rf`,
and one of those responses is not obvious until you write it down.

**Step 5 — the correction that matters: nominal vs. real.** `rf` is a
nominal rate: `rf = real_rf + π` (expected inflation). But NOI is not
fixed in real terms either — commercial leases have escalations, and rents
reprice to the market over time — so nominal NOI growth is also `g =
real_g + π` (to a first approximation, real estate is a partial inflation
hedge). Substitute both into the identity:

`cap rate = (real_rf + π) + rp − (real_g + π) = real_rf + rp − real_g`

**The inflation term cancels.** That's the single most important
consequence of doing the algebra instead of eyeballing it: a fall in
*nominal* rates driven purely by falling inflation expectations, with the
real rate unchanged, should move the cap rate **not at all** — because the
discount rate and the growth rate both fell by the same inflation
component. Only a change in the *real* risk-free rate should pass through
to the cap rate at (up to) 1:1. This immediately predicts that cap rates
should track real rates much more tightly than they track headline
nominal rates — a testable, falsifiable claim that fell straight out of
the model rather than being read off a chart.

**Step 6 — why even the real-rate pass-through won't be clean 1:1 in the
short run.** Three frictions, each derivable from what real estate
actually is as an asset:

1. *Appraisal/valuation lag.* Real estate isn't continuously priced like a
   bond; it's priced by infrequent transactions and periodic appraisals
   that anchor on recent comps. An appraiser updating a going-in cap rate
   is, structurally, averaging in stale information — so the *reported*
   cap rate should lag the *true* required-return shift by multiple
   quarters, understating pass-through in any short window.
2. *Why rates moved is itself informative about `g` and `rp`.* If the real
   rate fell because the central bank is cutting into a growth scare, then
   `real_g` (rent growth, occupancy) is falling too, and `rp` (vacancy and
   credit risk) may be *rising* — both push the cap rate up, offsetting or
   even reversing the downward pressure from `real_rf`. If instead the
   real rate fell because of a global savings glut / flight-to-quality
   capital search for yield, `rp` for all risk assets including real
   estate compresses too, which would push pass-through *above* 1:1. The
   sign and magnitude of the observed relationship should therefore be
   regime-dependent, not a fixed constant — there is no single "the" beta
   of cap rates to rates; it should differ by *why* rates moved.
3. *Sticky institutional return targets.* A large share of the capital
   pricing real estate (pensions, insurers) runs on fixed target-return
   hurdles set by a governance process, not a market-clearing price — this
   creates downward stickiness in cap rates independent of the rate
   environment.

**Predictions to check against the corpus:** (a) short-run pass-through of
nominal rates into cap rates should be well under 1:1, and can even be
zero or reversed in sign depending on regime; (b) cap rates should track
*real* rates more tightly than nominal rates; (c) net-lease / credit-tenant
assets (where `g ≈ 0` and cash flow is contractual, closest to a bond)
should show pass-through closer to 1:1 than growth-sensitive property
types; (d) the lag should show up as multi-quarter serial correlation in
appraisal-based cap rate series.

## Corpus answer (web search)

The literature confirms the core shape of the prediction, sharply:

- A TIAA study cited across multiple sources found only a **0.7
  correlation** between cap rates and interest rates (1992–2015), and in
  **5 of 8 historical episodes of rising Treasury rates, cap rates moved
  the opposite direction** — even on a one-year-forward basis.
- The 2022–2023 tightening cycle is a clean natural experiment matching
  the prediction directly: the 10-year Treasury rose from ~1.5% to ~3.9%
  (Jan 2022–Mar 2023), yet private-market cap rates *kept falling* until
  September 2022 and only rose ~0.4 points by Q1 2023 — a small fraction
  of the rate move, arriving with a multi-quarter lag.
- Multiple sources (CBRE, Morgan Stanley, MMC) explicitly attribute the
  gap to **appraisal lag and thin transaction volume**, exactly the
  valuation-smoothing mechanism derived in Step 6.1 above.
- Directly confirming Step 5: sources state cap rates are "more sensitive
  to *real* interest rates... than to headline nominal rates, because real
  estate can hedge inflation," and separately note that when rates rise
  from higher real rates (rather than higher inflation expectations),
  pressure on cap rates is more direct.
- Sources also flag capital flows, credit availability, and general
  macro/fundamentals as competing drivers in the short run, matching Step
  6.2's regime-dependence argument.

Sources: [The Interplay Between Cap Rates and Interest Rates — CFA
Institute](https://blogs.cfainstitute.org/investor/2024/06/13/the-interplay-between-cap-rates-and-interest-rates/),
[Cap Rates and Interest Rates in U.S. CRE: A Data
Note](https://www.mmcginvest.com/post/cap-rates-and-interest-rates-in-u-s-commercial-real-estate-a-data-note),
[Impact of Interest Rate Cuts on Real Estate Cap Rates —
CBRE](https://www.cbre.com/insights/briefs/impact-of-interest-rate-cuts-on-real-estate-cap-rates),
[Understanding the Correlation between Cap Rates and Treasury
Yields](https://bluevaultpartners.com/wp-content/uploads/2015/11/Insight-Understanding-the-Correlation-between-Cap-Rates-and-Treasury-Yields.pdf),
[Impact of Interest Rates on Capitalization Rates — Morgan
Stanley](https://www.morganstanley.com/assets/pdfs/articles/FrozenontheRates.pdf)

## Delta category: **rediscovered**

## Commentary

The qualitative structure (sub-1:1 pass-through, appraisal lag, regime
dependence, possible sign reversal) was reproduced independently and
matches the corpus closely enough to count as real rediscovery, not a
lucky guess dressed up after the fact — the mechanism (appraisal
smoothing, sticky institutional targets, co-movement of `g` and `rp` with
the same shock that moved `rf`) is the same mechanism the practitioner
literature cites.

The more interesting result is *internal*, not a match to the corpus: my
first pass at Step 4/5 (before doing the nominal/real decomposition
algebra) would have predicted that a pure disinflation-driven rate cut
compresses cap rates close to 1:1, since I was initially tempted to treat
"real growth intact, inflation falling" as `g` unchanged. Writing out `g =
real_g + π` explicitly and substituting is what forced the inflation terms
to cancel and produced the correct, sharper claim — that cap rates should
track *real* rates, not nominal ones — which is exactly what the corpus
independently emphasizes. That's the durable lesson from this spike: the
model was right, but only the algebraically rigorous form of it, not the
first hand-wavy application, actually earns credit against the corpus.
Sloppy application of a correct framework produces a wrong number with
high confidence, which is more dangerous than not having the framework at
all.
