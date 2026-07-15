# WOLF Congressional Trading Watch — 2026-07-15

## Methodology & access notes (read first)

This scan attempted direct automated access to all five specified primary/aggregator sources:

| Source | Result |
|---|---|
| Senate eFD (efd.senate.gov) | Blocked — 403 Forbidden (bot protection; the eFD search is also a POST-based form, not a crawlable listing) |
| House CHDP (disclosures-clerk.house.gov) | Blocked — 403 Forbidden, including direct PDF links |
| Quiver Quantitative (quiverquant.com) | Blocked — 403 Forbidden on trades page, politician pages, and news category page |
| CapitolTrades (capitoltrades.com) | Blocked — 403 Forbidden on /trades and homepage |
| Unusual Whales congressional feed | Not attempted directly (same class of site; expected same result) — reachable only via search snippets |

Every direct fetch to these five sources, plus a dozen secondary aggregators (AltIndex, CongressStock, InvestorLens, StockCircle, Benzinga, Nasdaq, ForeignPolicyJournal, NOTUS), returned HTTP 403. The outbound proxy status check showed no proxy-side policy block (`recentRelayFailures: []`), so these are the destination sites' own bot protection, not an environment restriction.

**Workaround used:** web search, which surfaces secondary reporting (Benzinga, MarketBeat, TickerReport, Nasdaq, Yahoo Finance, ForeignPolicyJournal, etc.) that itself cites and quotes the primary PTR filings. This recovered real, cross-corroborated filings, but with two caveats the reader should weigh:

1. **Not a strict last-24h window.** Search-engine indexing lag means the most recent *confirmed, multi-source-corroborated* disclosures found were filed July 2–13, 2026. No new PTR disclosed specifically July 14–15, 2026 could be confirmed through accessible sources — only a July 14 analysis piece that aggregates prior weeks' filings (see below).
2. **Coverage is a sample, not a full feed.** Without direct listing access, this is not an exhaustive capture of every PTR filed in the window — it's every filing that surfaced across ~15 targeted queries. Treat absence of a ticker/member as "not found," not "didn't trade."

Recommend for tomorrow's run: either an API-based data source (e.g., a paid Quiver/CapitolTrades API key, or the House Clerk's bulk XML/ZIP disclosure index which may not carry the same bot protection as the HTML portal) so this doesn't depend on search-engine indexing lag.

---

## Filings found (most recent disclosure date first)

### 1. Sen. John Boozman (R-AR, Senate) — Score 2
- **Disclosed:** July 13, 2026
- **Transactions** (traded June 4, 2026 → 39-day lag, compliant):
  - SELL Boston Scientific Corp (BSX) — $1,001–$15,000
  - BUY UnitedHealth Group Inc (UNH) — $1,001–$15,000
  - Additional same-filing transactions reported in secondary coverage (iShares 7-10 Year Treasury Bond ETF (IEF) sale, energy-sector holdings, a commodity ETF) — exact tickers/amounts for these could not be confirmed against a primary source; flagged as **unconfirmed detail**, not included in scoring.
- **Committee:** Senate Agriculture (Chair), Appropriations. No committee-jurisdiction overlap with BSX/UNH/IEF.
- **Score rationale:** Standalone, small size, no committee nexus, no cluster. Score 2.

### 2. Rep. Richard McCormick (R-GA-06, House) — Score 4 — COMMITTEE-RELEVANT
- **Disclosed:** July 9, 2026
- **Transaction:** BUY L3Harris Technologies (LHX) — two transactions, $1,001–$15,000 each (traded June 12, 2026 → 27-day lag, compliant)
- **Committee:** House Armed Services Committee; House Science, Space & Technology Committee.
- **Score rationale:** Direct committee-relevant trade — Armed Services Committee member buying a top-tier defense contractor. Auto-scored 4 per rubric.
- **Pattern flag:** This is not an isolated incident for this member. Benzinga (June 2025) previously reported McCormick as one of two Armed Services members who "quietly snapped up L3Harris shares" ahead of prior Iran-related tensions, and OpenSecrets (Sept 2025) reported he was **two years late** disclosing two dozen prior stock transactions. Today's trade continues a recognizable defense-committee/defense-stock pattern from a member with an existing late-filing history. Worth a standing watch item independent of any single filing's score.

### 3. Rep. Maria Elvira Salazar (R-FL-27, House) — Score 3
- **Disclosed:** July 7, 2026
- **Transactions:** BUY Brookfield Renewable Partners (BEP) — six separate purchase transactions across June 2–4, 2026 (three consecutive days), each in the $1,001–$50,000 range per tranche, cumulative disclosed value over $50,000 (secondary sources give a $20,000–$125,000 aggregate estimate; exact cumulative total not independently confirmed).
- **Committee:** House Foreign Affairs. No direct jurisdiction over utilities/renewables.
- **Score rationale:** Not committee-relevant, not a multi-member cluster (single member, single ticker). Scored above baseline "notable" because six buys of the same name in a three-day window is an accumulation pattern distinct from a one-off trade — media (Benzinga, Kavout) flagged it specifically for that reason, plus an apparent tension with Salazar's public policy positioning on energy. Score 3.

### 4. Rep. Daniel Meuser (R-PA-09, House) — Score 2
- **Disclosed:** July 2, 2026
- **Transaction:** SELL NVIDIA Corp (NVDA) — $1,001–$15,000 (traded May 27, 2026 → 36-day lag, compliant), executed via a Schwab brokerage account.
- **Committee:** No Energy/Commerce/Science committee seat identified. No jurisdiction nexus to semiconductor policy.
- **Score rationale:** Small size, standalone, no committee nexus. Elevated to 2 rather than 1 only because NVDA is a bellwether name amid live AI-policy debate (per ForeignPolicyJournal's framing of this and the Jacobs trade below as "Congress trading in sectors they regulate").

### 5. Rep. Sara Jacobs (D-CA-51, House) — Score 4 — CONFLICT-OF-INTEREST FLAG
- **Disclosed:** approx. May 20, 2026 (14-day lag from trade — well inside the 45-day window; surfaced this cycle via a July 14, 2026 retrospective piece grouping it with the Meuser trade)
- **Transactions:** SELL Qualcomm Inc (QCOM) — two transactions, $500,001–$1,000,000 each (traded May 6 and May 7, 2026), held via a family trust. Aggregate reported value up to ~$2 million.
- **Committee:** House Armed Services, House Foreign Affairs. No formal semiconductor-policy jurisdiction, but Qualcomm has defense-adjacent business lines.
- **Score rationale:** Not a committee-jurisdiction match by the letter of the rubric, but scored 4 rather than the standalone default of 2–3 because of (a) size — two separate six-figure-to-seven-figure tranches, among the largest size buckets in this scan, and (b) an explicit, widely-reported conflict-of-interest angle: the congresswoman's grandfather, Irwin Jacobs, co-founded Qualcomm, and the shares sold originate from a family trust tied to that founding stake. That combination of size + direct personal/family nexus to the traded company is treated here as functionally equivalent to the rubric's committee-relevance concern.

---

## Cluster check

No 3+-member same-ticker cluster was confirmed this cycle. Given the sourcing limitations above, this should be read as "none surfaced in the sample," not a confirmed absence — a proper cluster scan needs the full feed, which was inaccessible today.

## Special-flag check

- **Homebuilder tickers** (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC): none found in any filing surfaced this cycle. Note: DHI/LEN/PHM appeared in general market-news search results (housing-legislation-driven price moves), but none of that coverage tied to a congressional PTR filing.
- **Brand 9 client tickers:** no client-ticker list was found in this repository to check against (searched for a "clients" reference across .md/.json/.html/.txt — none found). If a client ticker list exists elsewhere (e.g., in a different Brand 9 system), point WOLF at it and this check can run properly next cycle. Flagging this as a gap rather than silently skipping it.

## STOCK Act drift (>45 days)

None of the five filings found this cycle exceeded the 45-day window (range: 14–39 days, all compliant). However, two members surfaced in this scan carry **known prior STOCK Act drift** worth tracking as standing context, not as today's news:

- **Rep. Julia Letlow (R-LA-05):** disclosed 210+ trades in a single January 2026 filing, many over a year late (some dating to 2024), reported value $225,000–$3.3 million. Currently running for Senate; disclosure timing has drawn press and opponent scrutiny. Not a new filing this cycle — flagged because it's the most severe active STOCK Act compliance story in Congress and because Letlow's late-filing pattern could resurface with any new PTR.
- **Rep. Richard McCormick (R-GA-06):** separately reported (OpenSecrets, Sept 2025) as two years late on two dozen transactions. His fresh July 9 L3Harris filing (above) is itself timely, but the member has a documented drift history.

## Confidence

Moderate-low. Five filings are cross-corroborated across 2+ independent secondary sources each (ticker, amount, and date agree). Zero filings were confirmed against a primary-source document directly (all primary portals blocked). Treat dollar amounts and committee assignments as accurate; treat this as a partial sample of the last ~2 weeks of disclosure activity, not a complete last-24h feed.
