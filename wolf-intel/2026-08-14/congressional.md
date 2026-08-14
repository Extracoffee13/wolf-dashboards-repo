# WOLF Congressional Trading Watch — 2026-08-14

## Data access note (read first)

This run could **not** reach the primary/aggregator sources listed in the task spec directly:
`efd.senate.gov`, `clerk.house.gov` (CHDP), `quiverquant.com`, `capitoltrades.com`, and
`benzinga.com` all returned `EGRESS_BLOCKED` from the sandbox's network egress proxy
(organization policy denial — not a transient error, so it was not retried or routed around).
`unusualwhales.com` was not tested directly for the same reason (same proxy policy class).

WebSearch remained available and surfaced secondary/aggregator coverage (NOTUS, Benzinga
snippets, CongressStock.com articles, Quiver Quantitative headlines, local Ohio press) that
quotes the underlying PTR data. This report is built from that coverage. **No filing dated
strictly within the last 24 hours (Aug 13–14, 2026) could be confirmed** — the most recent
verifiable, dated congressional trading activity found is the week of **Jul 31–Aug 7, 2026**,
plus a same-day-adjacent Aug 7 disclosure. Treat sizes/dates below as sourced from secondary
reporting, not a direct PTR read; flagged as `[secondary]` throughout.

**Action item for the operator:** if this watch is meant to run on a true 24h cadence, the
egress policy for this environment needs `efd.senate.gov`, `clerk.house.gov`, `quiverquant.com`,
and `capitoltrades.com` allow-listed. Until then, this job will structurally lag by up to a week
and depend on whatever secondary press happens to cover a given filing.

---

## Scored filings (most recent verifiable window)

### 1. Rep. Michael A. Rulli (R-OH-6) — Score: 4 (committee-relevant)
- **Committees:** Energy & Commerce (Energy subcommittee; Health subcommittee) — confirmed via energycommerce.house.gov.
- **Filing:** 32 trades disclosed ~Aug 7, 2026; 22 filed past the 45-day STOCK Act deadline. `[secondary: NOTUS, Benzinga, Salem News/Vindicator/Morning Journal]`
- **Tickers/types:** Sales — AAPL, CCI (Crown Castle), NOW (ServiceNow), LLY (Eli Lilly), Thermo Fisher (TMO), Prudential (PRU), Coca-Cola (KO), GOOGL, AMZN, Oracle (ORCL), Microsoft (MSFT), NVDA, GE Vernova (GEV), Pfizer (PFE), Palantir (PLTR — multiple), 3x Meta (META). Purchase — META (also appears as a buy in one leg).
- **Committee relevance:** GEV (energy) sits under Energy subcommittee jurisdiction; LLY/PFE/TMO (health) sit under Health subcommittee jurisdiction — both are Rulli's subcommittees.
- **Size bucket:** aggregate late-trade value reported as $22,022–$330,000 across the 22 late trades; full 32-trade filing reported "up to $480k." `[secondary, ranges not resolved to per-trade PTR bands]`
- **STOCK Act drift:** YES — see drift section below. Worst single trade (Pfizer, transacted ~Nov 26, 2024) disclosed Aug 7, 2026 ≈ **619 days** late.

### 2. Sen. Tommy Tuberville (R-AL) — Score: 4 (committee-relevant)
- **Committee:** Senate Armed Services (chairs the Personnel subcommittee) — confirmed via tuberville.senate.gov.
- **Filing:** First disclosed trades of 2026, reported ~Jul 16, 2026 (transaction date ~Jun 8, 2026 for the AWK leg). `[secondary: Benzinga]`
- **Tickers/types:** Sales — American Water Works (AWK), CSX, Duke Energy (DUK), **Lockheed Martin (LMT)**, Mastercard (MA), NextEra Energy (NEE), Pfizer (PFE).
- **Committee relevance:** LMT is a top-tier defense prime; a sale by a sitting Armed Services member is still committee-adjacent activity worth tracking even though it's a divestiture, not an accumulation.
- **Size bucket:** AWK leg reported $123,011–$445,000 (100k–250k / 250k–500k boundary). Other legs' sizes not resolved from available coverage.
- **STOCK Act drift:** Not flagged as late in available coverage — Jun 8 → Jul 16 ≈ 38 days, within the 45-day window.

### 3. Rep. Julie Johnson (D-TX-32) — Score: 3 (high-volume outlier / pattern)
- **Committee:** not confirmed from available coverage.
- **Filing:** 77 of the week's 147 congressional trades (52% of all activity, Jul 31–Aug 7, 2026) — most active filer of the week. `[secondary: CongressStock.com, Texas Tribune, Benzinga]`
- **Tickers/types:** 38 buys / 39 sells. Concentrated in Life Time Group Holdings (LTH, 9 buys/0 sells), C.H. Robinson Worldwide (CHRW, 6 buys), Formula One Group (FWONK, 6 buys); also touched MMM, AOS, ADBE, BA, COF, CI, PEP, MS and others.
- **Size bucket:** newly disclosed trades valued $76,076–$1.14M in aggregate across the batch. `[secondary, not per-trade]`
- **STOCK Act drift:** YES — dozens filed late; earliest-dated late trade reported completed **May 7, 2025**, disclosed within this Aug 2026 batch ≈ **458 days** late.

### 4. Rep. April McClain Delaney (D-MD) — Score: 2 (notable, standalone)
- **Committee:** not confirmed from available coverage.
- **Filing:** 62 of the week's 147 trades (second-most active filer, same Jul 31–Aug 7, 2026 week). `[secondary: Quiver Quantitative headline, CongressStock.com]`
- **Tickers/types:** Exits concentrated in Corpay Inc. (CPAY, 6 sells) and Service Corporation International (SCI, 6 sells); no buys reported in either name.
- **Size bucket:** not resolved from available coverage.
- **STOCK Act drift:** not individually confirmed; she is part of the week's "78 of 147 filed late" aggregate stat below.

### 5. Mega-cap tech cluster — Score: 3 (cluster behavior)
- AAPL, META, MSFT, NVDA, GOOGL, AMZN, ORCL each appear across **multiple** members' filings in the same window (Rulli's late batch alone touches six of the seven; the broader 66-stock/147-trade week pulls in more filers per CongressStock.com's summary, though only Rulli's and Johnson's/Delaney's individual tickers could be confirmed by name). Treated as a cluster signal rather than crediting each name individually, since the underlying per-member ticker list for the rest of the week's 147 trades could not be pulled from the blocked primary sources.

---

## STOCK Act drift (late-filed > 45 days)

| Member | Chamber/Party | Ticker(s) | Transaction date | Disclosed | Days late (approx) |
|---|---|---|---|---|---|
| Michael A. Rulli | House-R | PFE | ~Nov 26, 2024 | ~Aug 7, 2026 | ~619 |
| Michael A. Rulli | House-R | TMO | ~Dec 12, 2024 | ~Aug 7, 2026 | ~603 |
| Michael A. Rulli | House-R | NOW | ~Dec 16, 2024 | ~Aug 7, 2026 | ~599 |
| Michael A. Rulli | House-R | 19 other legs (GOOGL, AMZN, AAPL x2, KO, GEV, META x3, MSFT x2, NVDA x2, ORCL, PLTR x2, PRU) | various, up to ~20 months prior | ~Aug 7, 2026 | up to ~600+ |
| Julie Johnson | House-D | unspecified leg | ~May 7, 2025 | ~Aug 2026 batch | ~458 |
| Julie Johnson | House-D | ~75 other legs | Sep/Oct/Dec 2025 and later | ~Aug 2026 batch | 45–300+ (mixed) |
| Aggregate, week of Jul 31–Aug 7, 2026 | — | — | — | — | 78 of 147 trades (53%) filed past the 45-day deadline, per CongressStock.com |

Rulli is noted by NOTUS as the 2nd Ohio House member and among 28 House members in the past year found to have violated the STOCK Act's 45-day disclosure window.

---

## Special flags check

- **Homebuilder tickers** (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC): **no hits** in any filing surfaced this run.
- **Brand 9 client tickers:** Brand 9 Signs' clients are private hospitality/resort businesses, not publicly traded — this flag has no applicable tickers to check against and did not trigger. (Cross-checked for completeness against WOLF's own paper-trading book in `wolf_live_data.json` — MSFT, NOW, NVDA, and PLTR appear both there and in Rulli's late-filed batch; this is coincidental mega-cap overlap, not a Brand 9 relationship, and is not being scored as a special flag.)

---

## Sources (secondary coverage — primary portals were egress-blocked)

- NOTUS — "An Ohio Congressman Violated the STOCK Act With 22 Late Disclosures"
- NOTUS — "Rep. Julie Johnson Violated Transparency Law With Dozens of Late Stock Disclosures"
- Benzinga — "Congressman Violates Stock Act: Reports 22 Trades After Deadline..."
- Benzinga — "Senator Who Opposes Ban on Congress Trading Discloses First Trades of 2026..."
- Benzinga — "A Congress Member Sold Up To $445K In American Water Works Co Stock..."
- CongressStock.com — "Julie Johnson tops congressional trades with 77 deals" (week of 2026-07-31)
- Quiver Quantitative — news headlines for Rulli, Pelosi, McClain Delaney, Tuberville
- Local Ohio press (Salem News, The Review, Vindicator, Morning Journal, WFMJ) — Rulli coverage
- Texas Tribune — Julie Johnson coverage
