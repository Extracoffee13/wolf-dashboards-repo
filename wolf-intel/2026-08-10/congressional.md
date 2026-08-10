# WOLF Congressional Trading Watch — 2026-08-10

## Status: SCAN FAILED — no filing data collected

This run could not retrieve any congressional trading filing data. Every
required source was unreachable from this session's execution environment,
and no filing-level data (member, ticker, transaction type, size, dates)
was obtained from any channel. Nothing below is a substitute for that data
— **no filings are reported for this date because none were successfully
retrieved, not because none exist.**

## Sources attempted

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov | `EGRESS_BLOCKED` — network egress proxy denied the request |
| House CHDP | clerk.house.gov/PublicDisclosure | `EGRESS_BLOCKED` |
| Quiver Quantitative | quiverquant.com/congresstrading (web + API) | `EGRESS_BLOCKED` |
| CapitolTrades | capitoltrades.com | `EGRESS_BLOCKED` |
| Unusual Whales | unusualwhales.com/politics | `EGRESS_BLOCKED` |
| CongressStock.com (fallback aggregator) | congressstock.com | `EGRESS_BLOCKED` |
| congress.gov (fallback context) | congress.gov | `EGRESS_BLOCKED` |
| en.wikipedia.org (control test) | wikipedia.org | `EGRESS_BLOCKED` |

The control test against Wikipedia — a domain with no plausible policy
reason to be blocked — also failed with the same `EGRESS_BLOCKED` error.
This indicates the WebFetch tool has no working egress path at all in this
session (not a source-specific policy denial), so no direct-fetch source
could have succeeded regardless of which one was tried.

Web search (a separate tool, not blocked) was used as a fallback and
returned only generic background on the STOCK Act, disclosure mechanics,
and named aggregator sites — it did not surface individual filing-level
data (member/ticker/date/size) for the trailing 24 hours, which is not
something search snippets reliably carry.

## What this means

- No scored filing list is available for 2026-08-10.
- No STOCK Act drift (>45 day) filings could be checked.
- No homebuilder-ticker or Brand 9 client-ticker auto-bump checks could run,
  since no filings were seen.
- This is a tooling/access failure, not a "quiet day" finding. Treat it as
  unknown, not zero.

## Recommended fix

Either allowlist the required domains (efdsearch.senate.gov,
clerk.house.gov, quiverquant.com + api.quiverquant.com, capitoltrades.com,
unusualwhales.com) in this session's egress policy, or wire this watch to
a data path that doesn't depend on WebFetch (e.g., a pre-authorized API
key called directly over an allowlisted host, or a separate fetch service
that already has network access).
