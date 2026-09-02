# WOLF Congressional Trading Watch — 2026-09-02

**Status: DATA COLLECTION FAILED — no filings reported below are real; none were fabricated.**

## What happened

This run attempted to scan the last 24h of US congressional PTR (periodic
transaction report) filings via the sources specified in the task brief:

| Source | Result |
|---|---|
| Senate eFD (`efdsearch.senate.gov`) | Blocked — `EGRESS_BLOCKED` by the sandbox's network egress proxy |
| House CHDP (`clerk.house.gov/PublicDisclosure`) | Blocked — `EGRESS_BLOCKED` |
| Quiver Quantitative (`quiverquant.com/congresstrading`) | Blocked — `EGRESS_BLOCKED` |
| CapitolTrades (`capitoltrades.com`) | Blocked — `EGRESS_BLOCKED` |
| Unusual Whales congressional feed | Blocked — `EGRESS_BLOCKED` |
| Secondary attempts: congressstock.com, gurufocus.com, barchart.com | Also blocked — `EGRESS_BLOCKED` |

Every direct fetch (`WebFetch`) to a congressional-trading data source in this
session's network environment was rejected by the sandbox's egress proxy
before any content was returned. `WebSearch` (a separate, non-proxied hosted
tool) remained available, but it only returns indexed snippets/summaries, not
live per-filing rows — the snippets it surfaced were stale (dated weeks to
years old, e.g. a Feb 2024 Tuberville trade, a May 2026 Pelosi filing) and
carried no reliable "filed in the last 24h" signal, no verifiable size-bucket
precision, and no days-to-disclosure figure that could be trusted.

## Why no filings are listed

Given those constraints, this run is **not** publishing a scored filing list.
Congressional trading intel that feeds a public brief and a trading pipeline
must be sourced from verifiable primary filings — inventing plausible-looking
member names, tickers, sizes, or filing dates to fill out the requested
format would be worse than reporting nothing, so none were generated.

## Action needed

This is an environment/access issue, not a one-off fluke — re-running the
scan will hit the same block until the sandbox's egress policy allows
`efdsearch.senate.gov`, `clerk.house.gov`, and/or one of the aggregators. If
WOLF's operator has a way to run this scan from an environment with open
egress to those domains (or has an API key for Quiver Quantitative that
accepts an authenticated request through an allowed proxy path), that's the
fix. No manual data entry was substituted here.

## STOCK Act drift section

Not populated — no filings were retrieved this run.
