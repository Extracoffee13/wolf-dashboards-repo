# WOLF Congressional Trading Watch — 2026-07-24

## Data access note (read first)

Direct fetch of the primary disclosure portals was attempted and blocked at
the source (HTTP 403 from bot/WAF protection, not the local network — proxy
status showed zero relay failures, confirming the block is server-side):

- efd.senate.gov (Senate eFD search) — 403
- clerk.house.gov Public Disclosure — not reachable via fetch
- capitoltrades.com — 403
- quiverquant.com/congresstrading — 403
- altindex.com, congresstocks.com, congressstock.com — 403

Fallback: web search against news coverage that cites those same filings
(Benzinga, Quiver Quantitative's own syndicated news posts, CNBC, NOTUS,
Investing.com, Yahoo/Motley Fool). This means **the "last 24h" window could
not be verified against a live primary-source feed** — the filings below are
the most recent ones with confirmed transaction/filing dates surfaced by that
search, spanning roughly June 1 – July 22, 2026. Treat this run as directional
intel, not a certified real-time PTR feed, until direct portal access is
restored. No filing below is claimed to have posted in the strict trailing
24 hours unless its filing/report date is explicitly dated July 23–24, 2026.

---

## Scored filings

### 1. SpaceX (SPCX) post-IPO buying cluster — Score: 5
**Cluster / committee-relevant / high news salience**

SpaceX completed a ~$75B IPO in June 2026. At least six members of Congress
disclosed purchases within weeks of listing:

| Member | Chamber/Party | Committee | Txn date | Size bucket | Notes |
|---|---|---|---|---|---|
| Rep. Dan Meuser | House-R (PA) | Financial Services | 2026-06-15 | 15k–50k | Bought via dependent child, 3 days post-IPO |
| Rep. Gil Cisneros | House-D (CA) | Armed Services | 2026-06-18 | 1k–15k | Committee oversees DoD, a major SpaceX customer |
| Rep. William Timmons | House-R (SC) | Oversight & Govt Reform | 2026-06-15 | 50k–100k | First trade since 2019; notification date 2026-06-17 |
| Rep. John James | House-R (MI) | — | ~June 2026 | unspecified | Named in Quiver's 6-member roundup |
| Rep. John McGuire | House-R (VA) | — | ~June 2026 | unspecified | Named in Quiver's 6-member roundup |
| Rep. Lisa McClain* | House-R (MI) | — | ~June 2026 | unspecified | *Source listed as "Sen."; McClain is a House member — flagging the discrepancy rather than asserting chamber |
| Rep. Dan Newhouse | House-R (WA) | — | ~July 2026 | n/a | Filed 30 trades in a single disclosure (SpaceX among them) |

**Why score 5:** cluster of 6+ members (rubric floor for score 3) *plus*
committee relevance (Armed Services/Financial Services touching a company
that is simultaneously a top-tier DoD contractor) *plus* it's the single
most-covered congressional-trading story of the window. Days-to-disclosure
for the confirmed pairs (Timmons: txn 6/15, notice 6/17 → 2 days; well inside
STOCK Act's 45-day rule).

### 2. Sen. Tommy Tuberville (R-AL) — sold American Water Works (AWK) — Score: 5
- Transaction: 2026-06-08 · Filed/reported: ~2026-07-16 · **38 days** (compliant, near the 45-day edge)
- Size: $123,011–$445,000 (sale)
- Rationale: named track-record trader in the scoring rubric itself; large
  size; continues his multi-year pattern of net selling.

### 3. Rep. Dan Crenshaw (R-TX) — bought USOU (3x leveraged oil ETF) — Score: 4
- Committee: House Energy & Commerce (also House Intelligence)
- Transaction: 2026-06-01 · Filed: 2026-07-16 · **45 days — at the statutory limit**
- Size: $1,001–$15,000 (buy)
- Same PTR also disclosed sales of GOOG, AMZN, AAPL, META, and FAS (3x
  leveraged financial-bull ETF)
- Rationale: committee-relevant (Energy) + notably aggressive instrument
  (leveraged single-commodity ETF) for a sitting Energy/Intel committee
  member.

### 4. Rep. Maria Elvira Salazar (R-FL) — bought Brookfield Renewable (BEP) x6 — Score: 2
- Committee: House Foreign Affairs (chairs Western Hemisphere subcommittee)
- Transactions: 6 purchases over 3 days, mid-June 2026 · Disclosed: ~2026-07-10
- Size: $20,000–$125,000 aggregate
- Rationale: repeated same-ticker accumulation by a single member draws
  attention but does not meet the rubric's cluster definition (3+ *different*
  members, same ticker, same week) and her committee has no direct nexus to
  utilities/renewables — scored as notable-but-standalone rather than
  committee-relevant.

---

## Special flags

- **Homebuilder tickers** (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
  MHO, TMHC): none found in this scan. No auto-bump triggered.
- **Brand 9 client tickers**: no client-ticker reference list exists in this
  repo to check against. Flag check skipped — recommend adding a
  `wolf-intel/config/brand9-tickers.txt` (or similar) so future runs can
  actually evaluate this rule instead of skipping it.

---

## STOCK Act drift (late-filed disclosures, context/background)

These are ongoing/recent STOCK Act compliance stories surfaced by search;
none has a confirmed filing date inside this run's window, so they're logged
as background drift rather than scored filings:

- **Rep. Julia Letlow (R-LA)** — disclosed 210+ trades past the 45-day
  deadline, some over a year late; amended every annual financial disclosure
  she's filed. (Reported January 2026 — ongoing story, not a new filing today.)
- **Rep. Rob Menefee** — 5 stock sales disclosed weeks past deadline;
  attributed to leaving reports in draft status instead of submitting.
- **Rep. Jim Jordan (R-OH)** — ~1 month late disclosing his wife's sale of
  up to $100,000 in stock.
- **Rep. Linda Sánchez (D-CA)** — failed to report a trade within the 45-day
  window.
- **Rep. Scott Franklin (R-FL)** — reportedly failed to disclose 31 trades
  on time.

None of these were independently re-verified against a primary source this
run (portals blocked); treat as leads for the next run once direct access is
restored.

---

## Regulatory context (not a filing, but shapes the whole beat)

The House passed the **Stop Insider Trading Act** on 2026-07-23 and, on
2026-07-22, passed a separate GOP-led bill (232–198) that would bar members
of Congress, spouses, and dependent children from buying new stocks going
forward. Worth tracking — if a Senate companion moves, the entire PTR data
stream this watch depends on could shrink or change shape.

---

## Sources
Benzinga (politics/government trading beat), Quiver Quantitative news posts,
CNBC, NOTUS, Investing.com company-news feed, Yahoo Finance/Motley Fool,
The Globe and Mail (syndicated Quiver content). Direct portal/aggregator
fetch was blocked (see note at top).
