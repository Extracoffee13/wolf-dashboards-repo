# WOLF Congressional Trading Watch — 2026-07-30

## Methodology note (read first)

This run's direct-source scan did not complete as designed. `efdsearch.senate.gov`,
`disclosures-clerk.house.gov`, `capitoltrades.com`, `quiverquant.com`,
`congressstock.com`, `altindex.com`, and the Senate/House Stock Watcher S3 JSON
mirrors all returned **HTTP 403** on every fetch attempt — the session's egress
proxy reports these as organization policy denials, not site-side bot-blocking
(`curl $HTTPS_PROXY/__agentproxy/status` confirms "403/407 from the proxy" =
"destination host not allowed by egress policy," with an explicit instruction
not to route around it). Unusual Whales was not reachable either.

WebSearch (a separate channel, not subject to the same egress block) was
usable and is the sole source for everything below. That means this is a
**news-aggregated best-effort scan**, not the direct filing-by-filing PTR pull
the task specifies. Every entry below has a real citation and a real date;
nothing here is fabricated. But it is very likely incomplete — WebSearch
surfaces what's been written about, not every PTR filed. Sizeable categories
(homebuilder-ticker filings, Brand 9 client-ticker filings, anything with no
news coverage) could not be exhaustively checked and are flagged as
"unconfirmed" rather than "clear," below.

**Recommendation for tomorrow's run:** if this repo/session gets direct
network access to efdsearch.senate.gov, clerk.house.gov, or one of the
aggregators (allowlisted proxy, different session policy, or a connector),
switch back to direct scraping — it's the only way to get a true 24h filing
list with confidence.

---

## Scored filings (real, sourced, dates as reported)

### 1. Sen. Alan Armstrong (R-OK) — Senate — Score: 5
- **What:** 703 stock transactions across ~4 months, disclosed in a single
  catch-up filing reported by NOTUS on 2026-07-27.
- **Tickers/sizes (selected, as reported):** AAPL buy ≥$250,000 (late March);
  GOOGL, BRK, NVDA buys ≥$50,000 each (late March); Corning (GLW) sell
  ~$100,000; FDX, HD, PSX, PFE sells ≥$50,000 each; Williams Companies (WMB)
  stock sell $5M–$25M (June 24) and WMB options sell ≥$250,000 (June 22).
  Aggregate: ≥$7.66M in purchases, ≥$17.37M in sales.
  Size bucket: **5M+** (aggregate; individual line items span 50k-100k up
  through 5M-25M — exact per-line SEC-style buckets not independently
  re-verified since the primary filing itself was unreachable this run).
- **Days transaction → disclosure:** late-March 2026 trades disclosed
  ~2026-07-20/27 → **~115–125 days**. **STOCK Act violation — >45 days.**
  (June 22/24 trades disclosed same batch → ~30–35 days, technically
  compliant.)
- **Why score 5:** largest dollar volume by far, mega-cap liquid names, and
  the most severe STOCK Act drift of the week — this is the story, not a
  routine filing.
- **Context:** Armstrong is a freshman senator (sworn in 2026-03-24 after
  Markwayne Mullin's departure to DHS), former CEO/exec chairman of Williams
  Companies — the WMB sale is a former-CEO-selling-his-own-company signal as
  much as a political-trading one.
- Sources: [NOTUS](https://www.notus.org/congress/sen-alan-armstrong-violated-stock-act-with-700-tardy-stock-disclosures), [Oklahoma Watch](https://oklahomawatch.org/2026/07/27/sen-alan-armstrong-violated-stock-act-with-700-tardy-stock-disclosures/), [Benzinga](https://www.benzinga.com/news/politics/26/07/60657916/new-senator-makes-700-stock-trades-ditches-old-oil-company-for-magnificent-seven)

### 2. Rep. William Timmons IV (R-SC) — House — Score: 4
- **Ticker:** SpaceX (private→newly public, ticker reported as SPCX in some
  coverage) — buy, $50,001–$100,000, 2026-06-15.
- **Days transaction → disclosure:** trade 2026-06-15; reported in news as of
  2026-07-28 → **~43 days**, inside the 45-day window but close to the edge.
- **Why score 4 (committee-relevant, auto criterion):** Timmons chairs the
  House Oversight subcommittee on Military and Foreign Affairs — jurisdiction
  runs directly through the Pentagon, SpaceX's largest launch customer.
  Buying the stock 3 days after IPO while sitting on that subcommittee is a
  textbook committee-relevant trade.
- Sources: [24/7 Wall St](https://247wallst.com/investing/2026/07/28/congressman-who-oversees-military-contracts-bought-100000-in-spacex-stock-hes-not-the-only-one/), [Yahoo Finance](https://finance.yahoo.com/markets/stocks/articles/congressman-oversees-military-contracts-bought-171356236.html)

### 3. Sen. Tommy Tuberville (R-AL) — Senate — Score: 4
- **Tickers:** sells — Tractor Supply (TSCO), Lockheed Martin (LMT),
  Westinghouse Air Brake (WAB). Trade dates 2026-06-08 (TSCO, LMT) and
  2026-06-09 (WAB). Size buckets not confirmed via available sources this run.
- **Days transaction → disclosure:** not independently confirmed (Benzinga
  describes the disclosure as recent; exact filing date wasn't in the
  search snippet — flagged for tomorrow's direct-source follow-up).
- **Why score 4 (committee-relevant):** Tuberville sits on Senate
  Agriculture (Tractor Supply is an ag-retail name) and Senate Armed
  Services (Lockheed Martin is a top-5 defense prime) — both sales sit
  squarely in his own committee jurisdiction.
- Source: [Benzinga](https://www.benzinga.com/news/politics/26/07/60537231/senator-who-opposes-ban-on-congress-trading-discloses-first-trades-of-2026-heres-what-hes-selling)

### 4. Rep. Jared Moskowitz (D-FL) — House — Score: 2
- **Ticker:** SpaceX buy, $1,001–$15,000, 2026-06-12 (IPO day).
- **Days transaction → disclosure:** disclosed by ~2026-07-03 → ~21 days,
  compliant.
- **Why score 2:** small size, standalone, no committee nexus identified.
- Source: [CNBC](https://www.cnbc.com/2026/07/03/spacex-stock-congress-meuser-cisneros-ipo-disclosure.html)

### 5. Rep. Gil Cisneros (D-CA) — House — Score: 2
- **Ticker:** SpaceX buy, $1,001–$15,000, 2026-06-18; filed with the House
  2026-07-02.
- **Days transaction → disclosure:** ~14 days, compliant.
- **Why score 2:** small size, standalone.
- Source: [CNBC](https://www.cnbc.com/2026/07/03/spacex-stock-congress-meuser-cisneros-ipo-disclosure.html)

### Cluster note — SpaceX (score-3 criterion territory)
Timmons, Moskowitz, Cisneros, and at least one more member ("Meuser," per
the CNBC headline, details not independently pulled this run) all disclosed
SpaceX buys within days of its June 12 IPO. That's 4+ members, same ticker,
same week → meets the "3+ members, same ticker, same week" cluster criterion
in its own right, independent of Timmons's individual committee-relevance
bump.

### Unresolved — flagged, not scored
- **Sen. Markwayne Mullin** — headline reference to "buys 10 stocks" incl.
  unnamed "$5 billion companies" (Yahoo Finance). No ticker-level detail
  surfaced in search snippets; not scored to avoid guessing at tickers/sizes.
  Follow up via direct efdsearch.senate.gov access if restored.

---

## Special flags

- **Homebuilder tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC,
  MHO, TMHC):** No individual-member trades in these names surfaced via
  WebSearch this run. Coverage found was limited to the sector-wide rally
  after the June affordable-housing bill passed — not a member-level
  filing. **Unconfirmed absence, not a confirmed clear** — direct-source
  access is needed to actually clear this list.
- **Brand 9 client tickers:** no client-ticker list exists in this repo to
  check against (checked `wolf_live_data.json` and repo root for one — none
  found). This flag could not be evaluated this run. If a client-ticker
  list should live somewhere for WOLF to reference, that's a gap worth
  closing outside this task.

## STOCK Act drift section

| Member | Chamber | Trade date(s) | Disclosed | Days late |
|---|---|---|---|---|
| Sen. Alan Armstrong (R-OK) | Senate | late March 2026 (bulk) | ~2026-07-20/27 | **~115–125 days late** — the clear outlier this run |
| Sen. Alan Armstrong (R-OK) | Senate | 2026-06-22/24 (WMB) | same batch | ~30–35 days — compliant |

No other confirmed >45-day-late filings surfaced this run; this is a
function of search coverage, not a clean bill of health across all 535
members.
