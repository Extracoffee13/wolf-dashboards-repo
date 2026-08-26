# WOLF Congressional Trading Watch — 2026-08-26

## Run status: DEGRADED — primary sources blocked

This run could not complete a true last-24h scan. Every primary and
aggregator source specified in the task is blocked by this session's
network egress policy (direct fetch, not a search):

- `efdsearch.senate.gov` — EGRESS_BLOCKED
- `disclosures-clerk.house.gov` — EGRESS_BLOCKED
- `www.capitoltrades.com` — EGRESS_BLOCKED
- `www.quiverquant.com` — EGRESS_BLOCKED
- `www.congressstock.com` — EGRESS_BLOCKED
- `us.trendlyne.com` — EGRESS_BLOCKED
- Unusual Whales congressional feed — not attempted directly; same proxy would apply

No itemized, timestamped PTR list for the Aug 25–26 window could be pulled
from any of these. Web search (a separate, non-egress channel) surfaced
scattered secondary coverage (mostly Benzinga per-filing writeups), but none
of it carries a confirmed transaction-to-disclosure timestamp inside the
last 24 hours — the most recent dated item found (Pelosi/Bloom Energy) is
from Aug 21, five days old. **Nothing below should be read as "filed in the
last 24 hours."** It's the closest verifiable context available this run,
included so the log isn't empty, with dates as reported.

Do not fabricate filings to fill the format. The two files this task
requests (full list + public top-3) are written honestly short this run.

## What was found (secondary coverage, not a verified 24h scan)

| Date reported | Member | Chamber/Party | Ticker | Type | Size bucket | Score | Notes |
|---|---|---|---|---|---|---|---|
| 2026-08-21 (filing); trade 2026-07-24 | Nancy Pelosi | House / D | BE (Bloom Energy) | Buy | $4,250,007–$14,500,000 (as reported) | 5 | Track-record member, large size; ~28 days trade-to-disclosure, within 45-day window. Source: Benzinga. |
| 2026-08 (exact date not confirmed) | Tim Moore | House / R (NC) | T (AT&T) | Sell | $50,001–$100,000 | 2 | Standalone, no committee linkage found. Source: Benzinga. |
| 2026-08-03 | Sheldon Whitehouse | Senate / D | LOW (Lowe's) | Sell | $1,001–$15,000 | 1 | Small size, noise. Source: Benzinga. |
| 2026-08 (exact date not confirmed) | Unnamed House member | House | GOOGL (Alphabet) | Buy | ~$120,000 | 2 | Committee relevance not established from available coverage. Source: Benzinga. |
| 2026-08 (exact date not confirmed) | Unnamed House member | House | GD (General Dynamics) | Sell | up to $30,000 | 2 | Defense name, small size; committee assignment unconfirmed. Source: Benzinga. |
| 2026-08-24 (filing); earliest trade ~late 2024 | Michael Rulli | House / R (OH) | Multiple: PLTR, PFE, GOOGL, AMZN, AAPL, META, MSFT, ORCL | Mixed buy/sell | $22,022–$330,000 aggregate across 22 trades | 4 | **STOCK Act drift** — see below. Source: Benzinga, NOTUS, Vindicator, Salem News. |

Homebuilder-ticker scan (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
MHO, TMHC): no member-specific trade in this list touches a homebuilder
ticker. No auto-bump triggered this run.

Brand 9 client-ticker scan: client ticker list is not present anywhere in
this repo, so the auto-bump rule could not be evaluated. Flagging as a gap
— see lesson below.

## STOCK Act drift — late filings

**Rep. Michael Rulli (R-OH)** disclosed 22 trades late, including several
dating back to late 2024 — well past the 45-day STOCK Act window. Names
involved: Palantir, Pfizer, Alphabet, Amazon, Apple, Meta, Microsoft,
Oracle. Reported as the 28th House member to violate the STOCK Act in the
past year per NOTUS; second Ohio member after Jim Jordan. This is a
genuine, well-corroborated drift case (multiple local + national outlets),
even though it isn't a same-day filing.

## Sourcing

- [Recent Filing Shows That Rep. Nancy Pelosi Bought Over $4.25M Worth of Bloom Energy Stock](https://www.benzinga.com/government/26/08/61385680/recent-filing-shows-rep-nancy-pelosi-bought-over-4-25m-worth-bloom-energy-stock)
- [North Carolina Rep. Tim Moore Sold Up to $100K Worth of AT&T Stock](https://www.benzinga.com/government/26/08/61358142/north-carolina-rep-tim-moore-sold-100k-worth-t-stock)
- [Congressional Trading Report: Sen. Sheldon Whitehouse Sold Over $1K In Lowe's Companies Stock](https://www.benzinga.com/government/26/08/60911866/congressional-trading-report-sen-sheldon-whitehouse-sold-over-1k-lowe-s-companies-stock)
- [A Congress Member Bought Up To $120K In Alphabet Stock](https://www.benzinga.com/government/26/08/61114113/congress-member-bought-120k-alphabet-stock-here-s-what-you-need-know)
- [A Congress Member Sold Up To $30K In General Dynamics Stock](https://www.benzinga.com/government/26/06/60102603/congress-member-sold-30k-general-dynamics-stock-here-s-what-you-need-know)
- [Congressman Violates Stock Act: Reports 22 Trades After Deadline](https://www.benzinga.com/news/politics/26/08/61161946/congressman-violates-stock-act-reports-22-trades-after-deadline)
- [An Ohio Congressman Violated the STOCK Act With 22 Late Disclosures — NOTUS](https://www.notus.org/money/michael-rulli-stock-disclosures)
- [Rulli violates federal law on stock trading — The Vindicator](https://www.vindy.com/news/local-news/2026/08/rulli-violates-federal-law-on-stock-trading/)

## Lesson for next run

This session's network egress proxy blocks every domain this task is
configured to scan (Senate eFD, House CHDP, CapitolTrades, Quiver,
Trendlyne). Web search is not a substitute for a real-time 45-day-window
PTR scan — it surfaces whatever secondary press happened to cover, with
unreliable/absent timestamps, so it cannot support a genuine "last 24h"
claim. To make this task actually deliver what it promises, one of the
following needs to happen before the next scheduled run: (1) whitelist
the specific data-source domains in the egress policy, or (2) wire in an
API-based feed (e.g. Quiver's API) that isn't subject to the browser-style
block. Also: no Brand 9 client-ticker list exists in this repo, so that
auto-bump rule is currently unenforceable — needs a source file.
