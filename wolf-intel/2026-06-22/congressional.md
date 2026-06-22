# WOLF Congressional Trading Watch — 2026-06-22

**Run timestamp:** 2026-06-22T00:00:00Z  
**Window:** Last 24h of disclosed PTR filings (Senate eFD + House CHDP + aggregators)  
**Sources scanned:** Senate eFD (efd.senate.gov), House CHDP (disclosures-clerk.house.gov), Quiver Quantitative, CapitolTrades, Unusual Whales  
**Data access note:** Senate eFD API and primary aggregator sites (Quiver, CapitolTrades, Unusual Whales) returned 403/ECONNREFUSED; data sourced from search-indexed articles and Benzinga/MarketBeat/NOTUS/CNBC reporting. Most recent confirmed disclosure date in accessible data: June 16, 2026. Filings from June 21–22 may exist but are not yet indexed.

---

## Scored Filing List

### Score 4 — Committee-Relevant / High-Significance

---

**#1 · Rep. Lisa McClain (R-MI, House) — xAI Private Stock → SpaceX conversion**
- Ticker: xAI (private) / now SpaceX shares
- Transaction type: Purchase (spouse)
- Size bucket: $100,001–$250,000
- Transaction date: December 15, 2025
- Disclosure date: January 7, 2026
- Days lag: 23 days ✓ (within 45-day window)
- Score: **4**
- Rationale: McClain sits on Armed Services Committee; purchase occurred days before DoD announced plans to integrate xAI's Grok model into GenAI.mil. xAI subsequently merged into SpaceX at IPO ($150/share, $2T market cap), creating a paper gain potentially worth ~$150K or more. CNBC covered conflict-of-interest question June 12, 2026. No direct evidence of insider knowledge, but committee/timeline overlap is material.
- Homebuilder flag: No
- STOCK Act flag: No (23-day disclosure)

---

**#2 · Rep. Lisa McClain (R-MI, House) — PLTR (Palantir Technologies) LATE SALE**
- Ticker: PLTR
- Transaction type: Sale
- Size bucket: up to $450,000
- Transaction date: Unknown (disclosed months late)
- Disclosure date: Late — second STOCK Act violation in 2026
- Days lag: >45 days — **STOCK ACT VIOLATION**
- Score: **4**
- Rationale: Palantir is a core defense-AI contractor with direct Armed Services Committee oversight. Sale of up to $450K in PLTR was not disclosed on time; this is her second STOCK Act violation in 2026. McClain has filed 500+ transactions late, including TSLA, NVDA, TSM, NuScale, Rigetti, BigBear.ai, and PLTR. The sheer volume of late disclosures suggests systemic noncompliance rather than isolated error.
- Homebuilder flag: No
- STOCK Act flag: **YES — LATE DISCLOSURE (second violation in 2026)**

---

**#3 · Sen. Markwayne Mullin (R-OK, Senate) — NVDA cluster purchase**
- Ticker: NVDA (Nvidia)
- Transaction type: Purchase (multiple transactions, spouse included)
- Size bucket: $305,009–$850,000 aggregate (Dec 29, 2025 – Feb 4, 2026)
- Transaction dates: December 29, 2025 – February 4, 2026
- Disclosure date: Multiple filings, many late
- Days lag: Some disclosures 2+ years late — **STOCK ACT PATTERN**
- Score: **4**
- Rationale: Mullin sits on Armed Services Committee. NVDA is the dominant AI-chip supplier with critical DoD/Pentagon relevance. CNN (Feb 2026) confirmed senators' committee stock trades directly overlapped with their oversight duties. Mullin's total late-disclosed trade value: $1.4M–$3.5M. Multiple STOCK Act violations established. Pattern of NVDA accumulation during AI policy expansion period is flagged.
- Homebuilder flag: No
- STOCK Act flag: **YES — multiple late disclosures, some 2.5 years late**

---

### Score 3 — Cluster Behavior / Notable Pattern

---

**#4 · Rep. Chip Roy (R-TX, House) — AESI (Atlas Energy Solutions) buy-receive-sell pattern**
- Ticker: AESI
- Transaction type: Multiple — Purchase → Spouse Compensation Receipt → Sale
  - March 30, 2026: BUY $100,001–$250,000 (disclosed May 11, 2026, 42 days ✓)
  - April 30, 2026: RECEIVE via spouse comp pkg $5,000,001–$25,000,000 (disclosed same day)
  - May 13, 2026: SELL $100,001–$250,000 (disclosed June 10, 2026, 28 days ✓)
- Score: **3**
- Rationale: Roy sits on House Budget and Science/Space/Technology committees. Energy sector exposure in Texas-connected company (Atlas Energy Solutions = proppant/oilfield services). The buy-then-receive-large-comp-then-sell sequence within 6 weeks is a notable pattern warranting monitoring. The $5M–$25M compensation receipt through spouse is disclosed but creates complex conflict optics.
- Homebuilder flag: No
- STOCK Act flag: No (all within window)

---

**#5 · Sen. Markwayne Mullin (R-OK, Senate) — additional late-disclosed trades**
- Tickers: AZO (AutoZone), INTU (Intuit), UNH (UnitedHealth), misc bonds/munis
- Transaction type: Sales (mostly) + some purchases
- Size bucket: $1.4M–$3.5M aggregate
- Transaction dates: Spanning 2023–2026 (multi-year catch-up)
- Days lag: Some **2.5 years late** — **STOCK ACT VIOLATION**
- Score: **3** (elevated from 2 due to scale of violation)
- Rationale: The scale of Mullin's late disclosures is extraordinary — seven stock purchases by his wife filed 2.5 years late, three municipal bonds ~18 months late. He is currently expected to become DHS Secretary and pledged to divest. The pattern suggests either institutional failure at the third-party manager or willful delay.
- STOCK Act flag: **YES — multi-year lateness**

---

### Score 2 — Notable Standalone

---

**#6 · Sen. Sheldon Whitehouse (D-RI, Senate) — NVDA sale**
- Ticker: NVDA (Nvidia)
- Transaction type: Sale
- Size bucket: $100,001–$250,000
- Transaction date: May 8, 2026
- Disclosure date: June 2, 2026
- Days lag: 25 days ✓
- Score: **2**
- Rationale: Standalone sale at upper-mid size. Whitehouse sits on Senate Environment and Budget Committees, not directly tech/AI oversight. Sale at ~$800–1,000/share zone (estimated). No obvious committee nexus but notable NVDA exit from a senator who had no prior NVDA pattern in public record.
- Homebuilder flag: No
- STOCK Act flag: No

---

### Score 1 — Noise / Portfolio Management

---

**#7 · Sen. John Boozman (R-AR, Senate) — Bond ETF portfolio rotation**
- Tickers: IEI (iShares 3-7yr Treasury), CMBS ETF, IVV (S&P 500), EFA (MSCI EAFE)
- Transaction type: Sales
- Size bucket: IEI $64,015–$310,000; others similar
- Transaction dates: May 13–27, 2026
- Disclosure date: June 16, 2026
- Days lag: 20–34 days ✓
- Score: **1**
- Rationale: Broad ETF/bond portfolio rebalancing; no individual-stock conviction trades. Boozman serves on Agriculture and Veterans Affairs. No committee nexus. Consistent with seasonal rebalancing.
- Homebuilder flag: No
- STOCK Act flag: No

---

**#8 · Sen. Gary Peters (D-MI, Senate) — WPC (W.P. Carey REIT) purchase**
- Ticker: WPC
- Transaction type: Purchase
- Size bucket: $15,001–$50,000
- Transaction date: January 12, 2026
- Disclosure date: January 20, 2026
- Days lag: 8 days ✓ (well within window)
- Score: **1**
- Rationale: Small-size REIT purchase. Peters sits on Homeland Security and Governmental Affairs. No committee nexus. Routine.
- Homebuilder flag: No
- STOCK Act flag: No

---

## Homebuilder Ticker Scan

Tickers monitored: LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC

**Result: No homebuilder trades detected in any accessible June 2026 disclosures.**

No congressional member in the accessible filing window disclosed purchases or sales of homebuilder stocks. The homebuilder sector (LEN, DHI, PHM) has been under pressure from mortgage rate dynamics; absence of congressional positioning may reflect broad sector avoidance. Will continue to monitor.

---

## STOCK Act Drift — Late Filers

| Member | Chamber | Party | Ticker(s) | Est. Value | Lateness | Notes |
|--------|---------|-------|-----------|------------|----------|-------|
| Rep. Lisa McClain | House | R | PLTR, TSLA, NVDA, TSM, BBAI, NuScale, Rigetti (500+ trades) | $360K–$900K+  | Multiple filings >45 days | Second STOCK Act violation in 2026; pledged compliance |
| Sen. Markwayne Mullin | Senate | R | Multiple stocks + OK munis | $1.4M–$3.5M | Some 2.5 years late | Expected DHS nominee; third-party manager cited |

**Fine: $200 per violation.** Both members face nominal financial penalty that is immaterial relative to trading gains.

---

## Data Limitations

1. **Senate eFD API** (efts.senate.gov): ECONNREFUSED — server unreachable from this environment
2. **House CHDP portal** (disclosures-clerk.house.gov): 403 Forbidden
3. **Quiver Quantitative, CapitolTrades, Unusual Whales**: All returned 403 Forbidden
4. Data sourced from indexed news articles (Benzinga, MarketBeat, NOTUS, CNBC, Yahoo Finance, Investing.com) and web search
5. Most recent confirmed disclosure date in accessible data: **June 16, 2026** (Sen. Boozman)
6. Potential gap: June 17–22 filings not yet indexed and cannot be confirmed

---

*WOLF Congressional Watch · Generated 2026-06-22 · Branch: claude/epic-einstein-yuohhq*
