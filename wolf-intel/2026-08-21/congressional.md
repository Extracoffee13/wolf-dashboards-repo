# WOLF Congressional Trading Watch — 2026-08-21

## Run status: BLOCKED — no data collected

This scheduled scan could not reach any of its required sources. Every
outbound fetch to the configured targets was rejected by this session's
network egress policy (`EGRESS_BLOCKED`, agent proxy), including:

- `efdsearch.senate.gov` (Senate eFD)
- `clerk.house.gov` (House CHDP)
- `quiverquant.com` (Quiver Quantitative)
- `capitoltrades.com` (CapitolTrades)
- `congressstock.com`, `insiderfinance.io`, `pelositracker.app` (alternate aggregators tried after the primary four failed)
- News coverage of individual filings (e.g. `benzinga.com`) — also blocked

`WebSearch` (routed separately from `WebFetch`/direct fetch) returned only
search-result snippets, not full filing data — insufficient to responsibly
attribute specific tickers, transaction sizes, or dates to named members of
Congress.

## No filings are reported below

In line with the standing rule never to fabricate factual records —
especially ones naming real individuals alongside financial transactions —
this run is **not** publishing an invented filing list. All scoring,
STOCK Act drift, and special-flag sections below are intentionally empty
rather than filled with plausible-looking placeholder data.

| Section | Result |
|---|---|
| Senate PTRs scanned | 0 (source unreachable) |
| House PTRs scanned | 0 (source unreachable) |
| Filings scored | 0 |
| STOCK Act drift (>45 days) | none — no filings scanned |
| Homebuilder-ticker flags | none — no filings scanned |
| Brand 9 client-ticker flags | none — no filings scanned |

## Recommended fix

This environment's network policy needs an allowlist entry (or a
policy change to "unrestricted"/proxy passthrough) for the domains above
before this watch can produce real output. Until then, this daily job
will keep failing closed rather than emit fabricated congressional trade
data.
