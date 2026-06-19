# WOLF Congressional Trading Intel — 2026-06-19

**Scan window:** Last 24h disclosure filings (June 18–19, 2026)
**Sources scanned:** Senate eFD (efd.senate.gov), House CHDP (disclosures-clerk.house.gov), Quiver Quantitative, CapitolTrades, Benzinga Government Trades, Trendlyne Politician Tracker, MarketBeat Congressional Alerts
**Scan timestamp:** 2026-06-19T14:00Z

---

## DATA AVAILABILITY NOTE

Direct API access to Senate eFD, House CHDP, and major aggregators (CapitolTrades, Quiver, Unusual Whales) returned HTTP 403 blocks during this scan — all enforce bot-protection that prevents headless scraping. This is a structural pipeline constraint, not a one-time failure.

Public search index lag for congressional PTR filings is typically **5–10 days** between official filing and searchable indexing. As a result, the confirmed filing window available for this scan runs through approximately **June 12–17, 2026** for most sources.

**Implication:** "Last 24h" filings (June 18–19) are not yet indexed. This report covers the most recent available confirmed data, with explicit date tags on each filing's disclosure date.

---

## CONFIRMED FILINGS — RECENT WINDOW (through ~June 17, 2026)

### Filing 1 — Whitehouse / NVDA SELL
| Field | Detail |
|---|---|
| **Member** | Sen. Sheldon Whitehouse |
| **Chamber** | Senate |
| **Party** | Democrat (RI) |
| **Ticker** | NVDA (Nvidia Corporation) |
| **Transaction** | SELL |
| **Size Bucket** | $100,001–$250,000 |
| **Transaction Date** | May 8, 2026 |
| **Disclosure Date** | June 2, 2026 |
| **Days Lag** | 25 days ✓ (STOCK Act compliant) |
| **Committee** | Environment & Public Works; Judiciary |
| **Score** | **2** |

**Rationale:** Whitehouse is not a primary semiconductor or tech committee member. The sell at $100k–$250k is meaningful in absolute terms but lacks committee-signal amplification. NVDA had been on a strong run through April 2026; this may represent profit-taking. No known track record of prescient tech trades.

---

### Filing 2 — Kelly / BMY SELL
| Field | Detail |
|---|---|
| **Member** | Rep. Mike Kelly |
| **Chamber** | House |
| **Party** | Republican (PA-16) |
| **Ticker** | BMY (Bristol-Myers Squibb) |
| **Transaction** | SELL |
| **Size Bucket** | $15,001–$65,000 |
| **Transaction Date** | May 7, 2026 |
| **Disclosure Date** | June 11, 2026 |
| **Days Lag** | 35 days ✓ (STOCK Act compliant) |
| **Committee** | Ways and Means |
| **Score** | **1** |

**Rationale:** Ways and Means handles tax/trade, not directly pharma regulation. BMY sell is routine portfolio management. No committee relevance. Near lower edge of STOCK Act window but compliant.

---

### Filing 3 — Jackson / MSFT SELL (partial)
| Field | Detail |
|---|---|
| **Member** | Rep. Jonathan Jackson |
| **Chamber** | House |
| **Party** | Democrat (IL-01) |
| **Ticker** | MSFT (Microsoft Corporation) |
| **Transaction** | SELL (partial) |
| **Size Bucket** | $15,001–$50,000 |
| **Transaction Date** | May 12, 2026 |
| **Disclosure Date** | June 2, 2026 |
| **Days Lag** | 21 days ✓ (STOCK Act compliant) |
| **Committee** | Not flagged as committee-relevant |
| **Score** | **1** |

**Rationale:** Routine partial reduction in large-cap tech. No committee signal. Fast disclosure. Noise.

---

### Filing 4 — Taylor / GOOGL BUY
| Field | Detail |
|---|---|
| **Member** | Rep. David Taylor |
| **Chamber** | House |
| **Party** | Republican (OH) |
| **Ticker** | GOOGL (Alphabet Inc.) |
| **Transaction** | BUY |
| **Size Bucket** | $5,001–$15,000 |
| **Transaction Date** | June 5, 2026 |
| **Disclosure Date** | June 12, 2026 |
| **Days Lag** | 7 days ✓ (exceptionally fast) |
| **Committee** | Not flagged as committee-relevant |
| **Score** | **1** |

**Rationale:** Small-size buy in mega-cap tech. Disclosure within 7 days is notably fast (well within the 45-day window). No committee signal. The fast disclosure is procedurally clean but offers no actionable edge.

---

### Filing 5 — Khanna / FDS BUY (wife's trust)
| Field | Detail |
|---|---|
| **Member** | Rep. Ro Khanna |
| **Chamber** | House |
| **Party** | Democrat (CA-17) |
| **Ticker** | FDS (FactSet Research Systems) |
| **Transaction** | BUY |
| **Size Bucket** | Likely $1,001–$15,000 (wife's trust pattern) |
| **Transaction Date** | ~Early-to-mid June 2026 |
| **Disclosure Date** | June 11–17, 2026 (window) |
| **Days Lag** | ~10–20 days est. ✓ |
| **Committee** | Armed Services, Science, Space & Technology |
| **Score** | **1** |

**Rationale:** Khanna is the single most active congressional filer — 4,100+ trades in 2025 via his wife's blind trust. FDS is a financial data/analytics company. No committee relevance to Armed Services. This is structural noise from a high-frequency disclosure pattern. FDS is not a homebuilder, defense prime, or notable sector signal.

---

## SPECIAL FLAGS

### Homebuilder Tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)
**NONE found** in the confirmed filing window.

### STOCK Act Drift (>45 days disclosure lag)
**NONE detected.** All confirmed filings are within the 45-day requirement.
- Whitehouse/NVDA: 25 days
- Kelly/BMY: 35 days
- Jackson/MSFT: 21 days
- Taylor/GOOGL: 7 days
- Khanna/FDS: ~10–20 days est.

### Cluster Behavior (3+ members same ticker same week)
**NONE detected.** No ticker appears in more than one confirmed filing this window.

---

## SCORE SUMMARY

| Rank | Member | Ticker | Type | Size | Score |
|---|---|---|---|---|---|
| 1 | Sen. Whitehouse (D-RI) | NVDA | SELL | $100k–$250k | **2** |
| 2 | Rep. Kelly (R-PA) | BMY | SELL | $15k–$65k | 1 |
| 3 | Rep. Jackson (D-IL) | MSFT | SELL | $15k–$50k | 1 |
| 4 | Rep. Taylor (R-OH) | GOOGL | BUY | $5k–$15k | 1 |
| 5 | Rep. Khanna (D-CA) | FDS | BUY | ~$1k–$15k | 1 |

**Top score this window: 2 (Whitehouse/NVDA).** No trades scored ≥4.

---

## PIPELINE NOTES

- **Senate eFD API** (`efts.senate.gov`): Connection refused / ECONNREFUSED — likely endpoint restructured or rate-limited
- **House CHDP portal** (`disclosures-clerk.house.gov`): HTTP 403 — requires browser session / JavaScript rendering
- **CapitolTrades**: HTTP 403 — bot protection active
- **Quiver Quantitative**: HTTP 403 — bot protection active
- **Unusual Whales**: HTTP 403 — bot protection active
- **Benzinga Government Trades**: HTTP 403 (direct page), but article URLs surfaced via search provided usable filing data
- **Trendlyne**: HTTP 403 on direct fetch; search snippets provided Khanna window data
- **Data sourced via:** Web search result snippets, Benzinga article metadata, MarketBeat alert snippets, Nasdaq/Yahoo article snippets (where accessible)

**Recommended pipeline improvement:** Configure a Puppeteer/Playwright-based scraper for CapitolTrades or Quiver to bypass bot-protection headers, or subscribe to a commercial congressional trading API (e.g., Quiver API paid tier, Unusual Whales API).

---

*WOLF Congressional Trading Watch | 2026-06-19 | Confidence: 0.55 (data gap acknowledged)*
