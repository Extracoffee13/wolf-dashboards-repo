# First-Principles Spike — 2026-07-09

## Question
Why do real estate capitalization rates move (roughly) inversely with interest rates, and why isn't that relationship 1:1?

*(Backlog was empty at bootstrap, so this question was generated fresh — relevant to Hartley Capital strategy and any real-estate-adjacent capital allocation decisions.)*

## First-principles answer (derived before any search)

**1. What a cap rate literally is.** Cap Rate = NOI / Price — a yield snapshot, like a bond's current yield.

**2. Where price comes from.** A rational buyer pays the present value of future NOI. Assuming constant growth g forever (Gordon growth / perpetuity model): Price = NOI / (r − g), where r is the required rate of return.

**3. Combine.** Cap Rate = NOI / Price = r − g. A cap rate is algebraically "required return minus expected growth" — not a free-floating market number.

**4. Where r comes from.** r = risk-free rate + risk premium (illiquidity, vacancy/credit risk, capex uncertainty, operating leverage vs. a bond).

**5. Full equation.** Cap Rate = (risk-free rate + risk premium) − g.

**Why the inverse relationship exists at all:** holding risk premium and g constant, a rise in the risk-free rate mechanically raises r, which mechanically raises the cap rate; since Price = NOI/CapRate, a higher cap rate at fixed NOI means a lower price. Same discounting logic that makes bond prices fall when yields rise — real estate is just a longer-duration, less liquid asset going through the identical math.

**Why it isn't 1:1** — the equation has three moving parts, and rates rarely move alone:
1. **g often moves with rates in the same direction, canceling part of the effect.** Rates commonly rise because the economy is strong or inflation is hot — and NOI (especially from short-lease assets like apartments/hotels, which reprice in months) rises with inflation too, partially offsetting the rate move.
2. **Risk premium is not fixed** — it's a function of the same macro regime. A "good" rate hike (growth-driven) can compress risk premium and offset the rate rise; a "bad" one (inflation without growth, credit stress) can expand it and amplify the move past 1:1.
3. **Lease structure gates how much of the shock reaches g.** Long fixed-escalator leases (office, net-lease) can't reprice NOI quickly, so those cap rates should track rates closer to 1:1 than multifamily/hotel — a cross-sectional prediction mirroring bond duration.
4. **Private-market pricing isn't continuously marked.** Properties reprice only at transaction, anchored to trailing comps — so cap rates lag rate moves (bid-ask standoff, volume drop) rather than adjusting instantly, unlike public REIT pricing.
5. **Leverage is a second, non-formulaic channel.** If cost of debt outruns cap rates, deals go negative-leverage, pushing levered buyers out of the bidding pool independent of the r−g algebra.

**Prediction going in:** the corpus would frame this via a "build-up" formula (risk-free + premium − growth), discuss cap-rate lag/stickiness vs. REITs, and note real-vs-nominal-rate and lease-duration effects — expected delta: rediscovered.

## Corpus answer (found via search)

- Standard formula, confirmed near-verbatim: **cap rate = (risk-free rate + risk premium) − long-run NOI growth**, explicitly derived from the Gordon Growth Model (apers.app, StableBread build-up method).
- Risk premium is explicitly non-fixed and decomposes into sub-components (tenant credit risk, illiquidity vs. listed REIT proxy, asset-class basis premium, sponsor/operator premium) and moves with market sentiment and capital flows.
- Empirically, cap rates lag interest-rate moves by **6–18 months** (cited example: 10Y Treasury +250bp from early 2022–mid 2023, cap rates lagged 12–18 months) — matches the "private pricing isn't continuously marked" mechanism.
- Corpus explicitly states **real rates, not nominal rates, are the true driver** — because real estate can hedge inflation via rent growth, cap rates are more sensitive to real yields than headline nominal rates; when nominal rates rise on inflation expectations, anticipated NOI growth rises too and dampens the impact. This is the same mechanism as point 1 above, framed in real/nominal terms rather than "g moves with rates."
- Historical risk-premium spread over Treasuries clusters ~2.0–4.0% in normalized markets.

Sources:
- [Cap Rate Formula: Treasury + Premium − Growth](https://apers.app/learn/financial-modeling/valuation/cap-rate-decomposition-risk-free-premium-growth)
- [How to Calculate and Interpret the Build-Up Method — StableBread](https://stablebread.com/build-up-method/)
- [Cap Rates and Interest Rates | Relationship in Real Estate — Wall Street Prep](https://www.wallstreetprep.com/knowledge/cap-rates-and-interest-rates/)
- [Cap Rates and Interest Rates in U.S. Commercial Real Estate: A Data Note](https://www.mmcginvest.com/post/cap-rates-and-interest-rates-in-u-s-commercial-real-estate-a-data-note)
- [Impact of Interest Rate Cuts on Real Estate Cap Rates — CBRE](https://www.cbre.com/insights/briefs/impact-of-interest-rate-cuts-on-real-estate-cap-rates)

## Delta category: **rediscovered**

## Commentary

The derivation landed on the corpus's exact formula (cap rate = risk-free + premium − growth) purely from combining the cap-rate definition with the Gordon growth perpetuity model — no retrieval needed, since it's two algebra steps once you accept "price = PV of a growing perpetuity." The lag/stickiness mechanism (point 4, private pricing isn't continuously marked) also matched the corpus's cited 6–18 month empirical lag almost exactly, and the "risk premium isn't fixed, moves with macro regime" point matched too.

Two points didn't show up verbatim in the corpus snippets and are worth flagging as the closest thing to a novel angle here, though neither contradicts anything found:
- The corpus frames the growth-offset mechanism as "real vs. nominal rates" (real estate hedges inflation, so real yields matter more than nominal). My reasoning arrived at the same net effect via a different frame — "g and r are driven by the same macro cause, so they move together and partially cancel" — which is a restatement, not a new claim, but the lease-duration cross-sectional prediction (long-fixed-lease assets should show closer-to-1:1 rate sensitivity than short-lease assets, mirroring bond duration) is a sharper, testable version of that idea than what turned up in the search results.
- The leverage/negative-leverage channel (point 5) — buyer pool shrinking when debt cost outruns cap rates — is a real, separate transmission mechanism from the r−g algebra, and wasn't surfaced by the corpus search, though it's standard enough in CRE capital markets that it likely exists in sources not surfaced here rather than being genuinely undiscovered.

Net: strong validation that reasoning from "price = PV of NOI" primitives reconstructs professional CRE valuation theory without needing to have studied it directly — the algebra does the work.
