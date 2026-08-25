# WOLF Congressional Trading Watch — 2026-08-25

## Methodology note (read first)

This session's network egress policy blocks direct `WebFetch` access to every
data source named in the standing task — `efdsearch.senate.gov`,
`disclosures-clerk.house.gov`, `capitoltrades.com`, `quiverquant.com`, and
`unusualwhales.com` all returned `EGRESS_BLOCKED` (confirmed the block is
general-purpose, not source-specific, by testing `en.wikipedia.org`, which
was also blocked). No MCP tool in this environment provides an alternate
path to those portals or aggregators.

The only working channel was `WebSearch`, which returns indexed snippets
from news coverage and aggregator pages rather than raw PTR filing data.
Everything below is therefore **sourced from secondary news coverage of
filings**, not a direct pull from Senate eFD / House CHDP / Quiver /
CapitolTrades. Coverage is necessarily incomplete — it reflects whatever
got picked up by financial press in the last day, not a full scan of all
PTRs filed. Days-since-transaction figures are computed from dates stated
in that coverage.

**Do not treat this file as a complete daily filing list.** Treat it as a
best-effort digest of the congressional-trading stories that surfaced in
search during this run, each attributed to its source. No filing details
below were invented; where a detail could not be confirmed it is marked
"unconfirmed" rather than guessed.

Brand 9 client-ticker flag: no client-ticker reference list exists in this
repo, so that auto-bump rule could not be evaluated this run.

---

## Filings / disclosures identified

### 1. Rep. Nancy Pelosi (D-CA, House) — Bloom Energy (BE) + Intel (INTC)

- **Chamber/party:** House, Democrat
- **Ticker(s):** BE (Bloom Energy), INTC (Intel, add-on)
- **Transaction type:** Buy (stock + call options)
- **Detail:** 15,000 BE Class A common shares across two tranches (Jul 24
  and Jul 28, 2026), plus 200 BE call options ($100 strike, exp. Jun 17
  2027). Aggregate disclosed value for the filing reported at roughly
  **$4.25M–$14.5M** (Benzinga); a related Benzinga piece puts her combined
  disclosed stock+options trades at **up to $13.5M** — first-ever BE
  position, framed as part of an AI-power-demand thesis alongside her
  existing Intel stake.
- **Reported size bucket:** 1M–5M at minimum on the stock leg alone per
  the low end of the reported range; combined filing may reach into 5M+ —
  source ranges are wide and not broken out per-transaction, so bucket is
  reported as **1M–5M to 5M+ (unconfirmed exact bucket)**.
- **Transaction date:** Jul 24 / Jul 28, 2026
- **Disclosure date:** Reported as Aug 21, 2026 by one source and Aug 24,
  2026 by another (Quiver Quantitative news item) — **date conflict,
  unresolved**, both are within the 45-day window either way.
- **Days between transaction and disclosure:** ~28–31 days. **Within the
  45-day STOCK Act window — no drift flag.**
- **Score: 5** — known-track-record member (Pelosi) trading large size.
  Not committee-relevant in the strict sense (no Energy/Commerce seat tied
  to BE), scored on track-record + size alone.
- Sources: Benzinga ("Recent Filing Shows That Rep. Nancy Pelosi Bought
  Over $4.25M Worth of Bloom Energy Stock"), Benzinga ("Nancy Pelosi
  Discloses Up to $13.5 Million in Stock, Options Trades"), Quiver
  Quantitative ("Nancy Pelosi Discloses First-Ever Bloom Energy Trade,
  Adds to Intel Bet Amid AI Power Boom"), 24/7 Wall St (Aug 25, 2026,
  "Nancy Pelosi Made Millions On Nvidia Options. Now She's Betting $3
  Million On 1 AI Energy Stock").

No other individual filings from the last 24–48h could be confirmed with
specific member/ticker/size detail through search alone. Two additional
items surfaced but are **excluded from the scored list** because their
underlying transactions/filings fall outside the last-24h window:

- Rep. Josh Gottheimer (D-NJ) — Alphabet (GOOGL) buy, $8,008–$120,000,
  transaction Jul 24 2026, **filed Aug 10, 2026** (outside window).
- Rep. Maria Elvira Salazar (R-FL) — Peloton (PTON) buy, $2,000–$30,000,
  transaction Mar 19 2026 (old filing being recirculated in an Aug 2026
  comparison piece, not a new disclosure).

---

## STOCK Act drift — late-filed (>45 days)

### Rep. Michael A. Rulli (R-OH, House)

- Disclosed **32 trades** in one batch, spanning transaction dates from
  **November 2024 through Aug 6, 2026** — per NOTUS and local Ohio outlets
  (The Vindicator, The Review, Morning Journal), all reporting in
  August 2026.
- Tickers involved per coverage: Palantir (PLTR), Pfizer (PFE), Alphabet
  (GOOGL), Amazon (AMZN), Apple (AAPL), Meta (META), Microsoft (MSFT),
  Nvidia (NVDA), Oracle (ORCL), Thermo Fisher (TMO), ServiceNow (NOW).
- Breakdown per NOTUS: 3 trades from 2024, 12 from 2025, 7 from before
  June 2026 — the oldest is roughly **21 months** late against the
  45-day STOCK Act deadline.
- **Could not confirm the exact date this batch was filed** (i.e.,
  whether it lands inside this run's last-24h window) — flagged here
  regardless because it's a live, ongoing STOCK Act violation story in
  this week's coverage and belongs in the drift record.
- Sources: Yahoo Finance / Benzinga ("Congressman Violates Stock Act:
  Reports 22 Trades After Deadline..." — note headline says 22, body text
  says 32; discrepancy is in the source, not this summary), NOTUS ("An
  Ohio Congressman Violated the STOCK Act With 22 Late Disclosures"),
  The Vindicator, The Review, Morning Journal.

---

## Homebuilder ticker check (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

No filing touching a homebuilder ticker was identified in the last-24h
window. Background context only: Congress Stock Tracker shows a
cumulative 94 disclosed trades in DHI across 6 members historically
(26 buys / 24 sells split) — not a new-filing signal, cited only to show
the ticker has standing congressional interest.

---

## Committee-relevance / cluster notes

- Defense contractor names (LMT, RTX, NOC, GD, BA, LHX, HON, PLTR) are
  recurring holdings among Armed Services Committee members per general
  background coverage, but no specific new filing in the last 24h was
  confirmed against this list.
- No 3+-member same-ticker cluster was confirmed for this window.

---

## Confidence

Low-to-moderate on the one scored filing (Pelosi/BE) — well-corroborated
across four independent sources. Very low on completeness of the overall
scan given the tooling constraint described above; this should not be
read as "only one filing happened in the last 24h," only as "this is what
search-only access surfaced and could verify."
