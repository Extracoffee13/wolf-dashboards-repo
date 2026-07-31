# WOLF Congressional Trading Watch — 2026-07-31

## Status: NO VERIFIED DATA — source access blocked

This run could not retrieve any congressional Periodic Transaction Report
(PTR) filing data for the last 24 hours. **No filings, scores, tickers, or
member names are reported below because none were verifiably obtained.**
This file intentionally contains zero synthesized or estimated trades.

## What was attempted

| Source | Method | Result |
|---|---|---|
| efd.senate.gov / efdsearch.senate.gov | Direct fetch | Blocked — proxy returned 403 (organization egress policy) |
| clerk.house.gov/PublicDisclosure, disclosures-clerk.house.gov | Direct fetch (including specific PTR PDF URLs surfaced by search) | Blocked — proxy returned 403 |
| quiverquant.com/congresstrading | Direct fetch | Blocked — proxy returned 403 |
| capitoltrades.com/trades | Direct fetch | Blocked — proxy returned 403 |
| unusualwhales.com/politics (incl. specific disclosure page) | Direct fetch | Blocked — proxy returned 403 |
| congressstock.com, insiderfinance.io, trendspider.com, capitolmarkets.org, investorlens.capital, amsflow.com, polytick.us | Direct fetch | Blocked — proxy returned 403 |
| web.archive.org (Wayback snapshot lookup) | Direct fetch (fallback attempt) | Blocked — proxy returned 403 |
| General web search for named members / tickers / dated queries | Search-only queries | Returned only generic descriptive text about the STOCK Act and aggregator sites — no itemized per-filing data (member, ticker, transaction type, size, filed date) for the last 24 hours |

## Diagnosis

Checked `$HTTPS_PROXY/__agentproxy/status` per the environment's proxy
troubleshooting doc. No relay failures were logged and the proxy is not in
selective/tool-scoped mode, which points to every one of the above hosts
being outside this session's allowed egress list — i.e. an organization
policy block, not a transient site-side issue. The proxy README is explicit
that 403/407 responses of this kind should be reported, not routed around
(no header/UA spoofing, no alternate mirrors, no retry loop was attempted).

## What this means for today's watch

- No Senate eFD or House CHDP filings could be enumerated.
- No CapitolTrades / Quiver / Unusual Whales aggregation could be cross-checked.
- The homebuilder-ticker auto-bump rule and the Brand 9 client-ticker
  auto-bump rule have nothing to evaluate against.
- The STOCK Act drift (>45 day) section is empty because no filings were
  retrieved, not because none exist.

## Recommendation

This watch needs either (a) an allowlisted egress exception for
efd.senate.gov, disclosures-clerk.house.gov, and one aggregator API
(Quiver Quantitative has a paid API with structured JSON, which would be far
more reliable than scraping HTML), or (b) a connector/MCP tool with its own
authenticated network path outside this proxy. Recommend routing this
request to whoever administers the session's egress policy before the next
scheduled run, otherwise tomorrow's run will hit the identical wall.

## Special flags evaluated

None — no filing data was available to check against the homebuilder-ticker
list or the Brand 9 client-ticker list.

## STOCK Act drift section

None — no filings were available to compute days-to-disclosure.
