# WOLF Congressional Trading Watch — 2026-07-13

## Status: DATA ACCESS FAILURE — no verified filings scanned

This run could not retrieve congressional trading filing data. This is **not**
a "clean scan, no activity" result — it is a tooling failure. Treat today's
watch as incomplete, not as evidence of a quiet trading day.

### What was attempted

| Source | Method | Result |
|---|---|---|
| efd.senate.gov (Senate eFD) | direct fetch | HTTP 403 |
| disclosures-clerk.house.gov (House CHDP) | direct fetch | HTTP 403 |
| quiverquant.com/congresstrading | direct fetch | HTTP 403 |
| capitoltrades.com/trades | direct fetch | HTTP 403 |
| unusualwhales.com/politics | direct fetch | HTTP 403 |
| congressstock.com, insiderfinance.io, trendlyne.com, govtrades.com, altindex.com | direct fetch | HTTP 403 (all) |
| cnn.com (control — non-financial-data mainstream news site) | direct fetch | HTTP 403 |

Every fetch attempt returned HTTP 403, including a mainstream news domain
(cnn.com) used as a control and a `.gov` domain (efd.senate.gov). Since a
plain news site and a federal disclosure site failed identically to the
trading-data aggregators, this looks like a blanket outbound-fetch
restriction in this session's environment rather than per-site bot
protection — see the agent proxy status/README, which explicitly says 403s
of this shape are an organization egress-policy block and instructs
"report the blocked host, do not retry or route around it."

Web search (a separate, non-blocked path) returned only indirect summaries —
platform descriptions, generic STOCK Act explainers, and a handful of
month-old data points (e.g., a search snippet referencing a Pelosi
GOOGL/UBER/INTC disclosure dated 2026-06-23, and a Rep. Julia Letlow
late-filing story from January 2026). None of this is a verified, dated
list of filings from the last 24 hours, so none of it is reported below as
a scored filing — reporting search-snippet fragments as if they were
confirmed PTR filings would risk fabricating financial intelligence.

### Filings identified in the last 24h (2026-07-12 → 2026-07-13)

None — could not be determined. No filing list, score, or STOCK Act drift
entry is reported today because no source could be reached to confirm one.

### Homebuilder ticker watch (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC)

Not checked — same access failure.

### Brand 9 client ticker watch

Not checked — same access failure.

### STOCK Act drift (>45 days late)

Not checked — same access failure.

### Recommendation

This watch needs a data path that survives this environment's egress
policy — an allowlisted MCP connector or API (e.g., a Quiver Quantitative
API key routed through an approved connector) rather than raw WebFetch
against efd.senate.gov / clerk.house.gov / aggregator sites, all of which
are currently unreachable. Flag to the operator before the next scheduled
run.
