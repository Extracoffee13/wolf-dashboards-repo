# WOLF Congressional Trading Watch — 2026-08-18

## Data access notice (read first)

This scan could **not** complete as a true last-24h database pull. Direct access to
all five specified sources was blocked at the network egress layer for this session
(organizational policy denial, confirmed via the proxy status endpoint — not a
transient error, so no retries/workarounds were attempted):

- `efd.senate.gov` — EGRESS_BLOCKED
- `clerk.house.gov` (CHDP) — not reachable (same egress policy)
- `quiverquant.com` — EGRESS_BLOCKED
- `capitoltrades.com` — EGRESS_BLOCKED
- `unusualwhales.com` — not reachable (same egress policy)

Fallback: web search (news-summary access only, no direct site fetch). This surfaces
*already-published news coverage* of filings, not a live filing feed, and search
coverage of the exact last-24h window (2026-08-17 18:00 → 2026-08-18 18:00 UTC) was
thin. Nothing below is presented as a complete 24h filing list — it's the verified
subset that search coverage turned up, correctly dated. No ticker, size, or date was
invented to fill gaps.

No in-repo reference list of "Brand 9 client tickers" was found to check filings
against, so that auto-bump rule could not be applied this run.

---

## Verified filings found (dates as sourced, none confirmed inside the strict 24h window)

### 1. Sen. Tim Sheehy (R-MT) — private-company disclosures
- **Filed:** 2026-08-13 (covered by Benzinga ~2026-08-18)
- **Transactions** (all private companies, not public tickers):
  - Sold $500,000–$1,000,000 — Ansett Holdings (Australian aviation training co.), transaction 2025-06-28
  - Sold $50,000–$100,000 — Sana Labs (Swedish software co.), transaction 2025-11-04
  - Bought $1,000–$15,000 — Grant Street Group, transaction 2025-11-03
  - Bought $1,000–$15,000 — AIA Contract Documents, transaction 2025-07-08
  - Bought $1,000–$15,000 — Constitution Surgery Alliance, transaction 2025-06-16
- **Days between transaction and disclosure:** ~253–423 days depending on line item — **all five exceed the 45-day STOCK Act limit.**
- **Score: 4/5** — sitting senator with a wealthy, closely-watched profile (co-founder of Bridger Aerospace, NASDAQ:BAER) and a cluster of multi-month-late private-company disclosures. Not scored 5 because these are private-company stakes, not liquid public-market trades.
- **Note:** none of these five names are homebuilder or (as far as could be checked) Brand 9 client tickers.

### 2. Rep. Michael Rulli (R-OH) — batch disclosure, 32 trades / 22 late
- **Filed:** 2026-08-07
- **What:** 22 of 32 disclosed trades were filed past the 45-day deadline, some from late 2024 — nearly two years late in the worst cases. Names involved include Palantir, Pfizer, Alphabet, Amazon, Apple, Meta, Microsoft, Nvidia, Oracle. Trade sizes reported in the $22,022–$330,000 range in aggregate.
- **Days between transaction and disclosure:** up to ~600+ days on the oldest lines — **STOCK Act violation.**
- **Score: 3/5** — cluster of large-cap tech/defense names from a sitting House member on the Energy & Commerce Committee, but this is a compliance story (lateness), not a fresh signal — the trades themselves are stale by the time of disclosure.
- Rulli is the second Ohio House member (after Jim Jordan) flagged for a STOCK Act violation in the past year, per NOTUS.

### 3. Rep. Julie Johnson (D-TX) — late disclosure
- **Filed:** August 2026 (exact date not resolved via search)
- **What:** trades dated back to 2025-05-07, 2025-09, 2025-10, and 2025-12 disclosed together; resulted in a $200 STOCK Act fine.
- **Score: 2/5** — standalone lateness item, no committee-relevance or cluster signal found.

### 4. Rep. Michael Guest (R-MS), House Ethics Committee Chair — family-trust sales
- **Reported by NOTUS on 2026-08-17.** More than six months late disclosing sales of Chevron, Airbnb, and e.l.f. Beauty stock held by a family trust benefiting his wife. Second STOCK Act violation for Guest (first was in 2021, ExxonMobil/BP).
- **Score: 3/5** — notable because the violator chairs the House Ethics Committee, but again a compliance story rather than a fresh trading signal. CVX is an energy-sector name; Guest does not sit on an energy committee as far as could be confirmed, so no committee-relevance bump applied.

---

## STOCK Act drift section (>45 days late)

All four items above are late-filed and belong here as much as in the scored list:

| Member | Chamber/Party | Filed | Worst lateness | Names involved |
|---|---|---|---|---|
| Tim Sheehy | Senate / R-MT | 2026-08-13 | ~423 days | Ansett Holdings, Sana Labs, Grant Street Group, AIA Contract Documents, Constitution Surgery Alliance (all private) |
| Michael Rulli | House / R-OH | 2026-08-07 | ~600+ days | Palantir, Pfizer, Alphabet, Amazon, Apple, Meta, Microsoft, Nvidia, Oracle |
| Julie Johnson | House / D-TX | Aug 2026 | ~15 months | not itemized in search coverage |
| Michael Guest | House / R-MS | reported 2026-08-17 | 6+ months | Chevron, Airbnb, e.l.f. Beauty |

Observation: four separate lateness stories broke in the same ~2-week window
(Aug 7–18, 2026) across both chambers and both parties — reads as a wave of
overdue-filing catch-up rather than four independent incidents. Worth checking
whether a compliance sweep or reporting deadline triggered a batch of backlog filings.

## Homebuilder ticker flags
None found in verified data (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC).

## Brand 9 client ticker flags
Not checked — no client ticker list found in this repo to check against.

## Filings that could not be verified
Search results referenced but could not confirm: Rep. Shri Thanedar (Strategy/MSTR
purchase, $15,001–$50,000) and Rep. Tim Moore (Centene/CNC purchase, $258,020–$895,000)
appear in earlier Benzinga coverage but without a confirmed August 2026 date — **excluded
from scoring, listed here only as leads for tomorrow's run** once site access is restored.
