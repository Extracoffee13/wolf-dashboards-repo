# WOLF Congressional Trading Watch — 2026-08-13

Scan window: prior 24h (2026-08-12 → 2026-08-13 ET), extended where needed to source the most recent verifiable filings.

## Access note (read before trusting the counts below)

Direct fetch access to the primary and aggregator sources named in this routine's spec was **blocked at the network egress layer** in this run's environment (org egress policy, not a fixable proxy error — confirmed via `/root/.ccr/README.md` and reproducible `EGRESS_BLOCKED` errors):

- `efdsearch.senate.gov` — blocked
- `disclosures-clerk.house.gov` — blocked
- `www.capitoltrades.com` — blocked
- `www.quiverquant.com` — blocked
- `unusualwhales.com` — blocked
- `www.congressstock.com` — blocked
- `www.benzinga.com` — blocked

No workaround was attempted (per policy: do not retry or route around organization egress denials). Everything below was reconstructed from indexed search-engine snippets of coverage of those filings, not from a direct scrape of the Senate eFD / House CHDP databases or aggregator APIs. This means:

- Coverage is **not a complete 24h census** of all PTRs filed — it's limited to what surfaced in search results and got picked up by financial press.
- Exact filing timestamps (vs. "disclosed in August 2026" per news coverage) could not be independently confirmed against the primary portals.
- "Cluster behavior" (3+ members trading the same ticker the same week) could not be computed — that requires a full daily transaction feed, which was not reachable.
- Brand 9 client tickers: no client-ticker list exists in this repo to check filings against, so that special flag could not be evaluated this run.

Treat this as a degraded-mode run. Recommend the operator either allowlist the above domains for this environment or supply a data feed (API key / CSV drop) so future runs can do a real 24h scrape.

---

## Scored filings

### 1. Rep. Julie Johnson (D-TX-32) — SCORE: 4 (committee-relevant) + STOCK Act violation

- **Chamber / party:** House, Democrat, TX-32
- **Committee relevance:** Vice Ranking Member, House Homeland Security Committee (Border Security & Enforcement; Emergency Management & Technology subcommittees)
- **Tickers involved (late-filed batch, 76 transactions):** Boeing (BA), Honeywell (HON), Alaska Air Group (ALK), Fifth Third Bancorp (FITB), International Paper (IP), Kroger (KR), Molson Coors (TAP), Cigna (CI)
- **Why score 4:** Boeing and Honeywell both hold active Department of Homeland Security contracts. Johnson sits on Homeland Security Committee leadership. A committee member trading the contractors her committee oversees is the textbook committee-relevance case this rubric is built to catch.
- **Transaction type:** Mixed buys/sells across the batch
- **Reported size bucket:** Aggregate across the 76-transaction late batch is described as "up to $1.1 million in buys and sales" — per-transaction buckets not resolved from available coverage; likely spans 1k-15k through 100k-250k given the transaction count.
- **Trade dates vs. disclosure:** Transactions dated back to May 7 2025, and September, October, and December 2025 — disclosed August 2026. **Days late: ~240 to ~460+ days past the 45-day STOCK Act deadline.** Reported framing: "transfers between accounts to complete final divestment," with the final sales filed on time but the underlying transfers not.
- **Separate context (same member, on-time filing):** Johnson also topped the week of Jul 31–Aug 7 2026 with 77 timely transactions (38 buys / 39 sells), concentrated in Life Time Group Holdings (LTH, 9 buys), C.H. Robinson Worldwide (CHRW, 6 buys), Formula One Group (FWONK, 6 buys). This volume is high but none of these tickers connect to her committee assignments, so it's noted as context, not separately scored.
- **Sources:** NOTUS ("Rep. Julie Johnson Violated Transparency Law With Dozens of Late Stock Disclosures"), Benzinga ("Congresswoman Discloses New Stock Trades Made a Year Ago"), congressstock.com weekly recap (indexed snippets only — direct fetch blocked).

### 2. Rep. Michael A. Rulli (R-OH-6) — SCORE: 4 (committee-relevant) + STOCK Act violation

- **Chamber / party:** House, Republican, OH-6
- **Committee relevance:** Energy & Commerce Committee (Energy and Health subcommittees); also Education & Workforce.
- **Tickers involved (32 trades disclosed, 22 late):** Alphabet (GOOGL), Amazon (AMZN), Apple (AAPL), Coca-Cola (KO), Eli Lilly (LLY), GE Vernova (GEV), Meta (META), Microsoft (MSFT), Nvidia (NVDA), Oracle (ORCL), Palantir (PLTR), Prudential Financial (PRU)
- **Why score 4:** GE Vernova is a pure-play energy/power-generation name sitting directly under his Energy & Commerce committee's jurisdiction. The rest of the late batch (Palantir, the mega-cap tech cluster) is high-visibility but not committee-linked on its own — GEV is what pushes this past a plain "notable standalone."
- **Transaction type:** Mixed buys/sells across the 22 late trades
- **Reported size bucket:** Late trades aggregate to "$22,022–$330,000" — spans roughly the 15k-50k through 250k-500k buckets depending on individual transaction; per-line breakdown not resolved from available coverage.
- **Trade dates vs. disclosure:** Late trades dated as far back as November 2024, most recent activity in the disclosed batch as recent as Aug 6 2026 — disclosed publicly in press coverage this month (August 2026). **Days late: up to ~600+ days on the oldest trade.**
- **Sources:** Benzinga ("Congressman Violates Stock Act: Reports 22 Trades After Deadline, Including Some Nearly Two Years Old"), NOTUS ("An Ohio Congressman Violated the STOCK Act With 22 Late Disclosures"), Salem News / Morning Journal / Vindicator / WFMJ regional wire pickups (indexed snippets only — direct fetch blocked).

### 3. Rep. April McClain Delaney (D-MD) — SCORE: 2 (notable, standalone)

- **Chamber / party:** House, Democrat, MD
- **Filed 62 of the week's 147 transactions** (Jul 31–Aug 7 2026), second-busiest filer after Johnson.
- No ticker-level breakdown surfaced in available coverage; no committee linkage identified. Logged for volume awareness only — not enough detail to score higher.
- **Source:** congressstock.com weekly recap (indexed snippet only).

---

## Special flags checked

- **Homebuilder tickers** (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC): **none found** in any filing surfaced this run. Note: unrelated congressional housing legislation (21st Century ROAD to Housing Act) passed both chambers this period — no member trading of homebuilder names tied to it was found in available coverage.
- **Brand 9 client tickers:** not evaluable — no client-ticker list exists in this repository for WOLF to check against. Flag this to the operator if this check is meant to run against a specific list.

## STOCK Act drift (>45 days late)

Both scored filings above are drift cases and are the most significant finding of this run:

| Member | Oldest late transaction | Disclosed | Days late (approx.) |
|---|---|---|---|
| Rep. Michael A. Rulli (R-OH-6) | Nov 2024 | Aug 2026 | ~600+ |
| Rep. Julie Johnson (D-TX-32) | May 7, 2025 | Aug 2026 | ~460+ |

Both cases involve dozens of transactions disclosed in a single batch well past the 45-day window, both drew local/national press attention this month for exactly that reason, and both members hold committee seats adjacent to at least one late-filed ticker (Johnson–Homeland Security/Boeing-Honeywell; Rulli–Energy & Commerce/GE Vernova). This is the pattern worth watching: large retroactive "catch-up" batches, not single missed trades.

## Not independently verified this run

- Precise per-transaction dollar buckets for the Johnson and Rulli batches (press coverage gives aggregates, not line items)
- Any filings strictly within the literal last 24h window, given blocked access to the live Senate eFD / House CHDP feeds
- Cluster behavior (3+ members, same ticker, same week)
