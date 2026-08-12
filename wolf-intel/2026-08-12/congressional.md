# WOLF Congressional Trading Watch — 2026-08-12

**Status: BLOCKED — no filings scanned.** This is not a "zero filings today" report; it is a source-access failure. Do not treat the absence of entries below as evidence of no congressional trading activity in the last 24h.

## What happened

Every configured source for this scan was unreachable from this session:

| Source | Method tried | Result |
|---|---|---|
| efd.senate.gov (Senate eFD) | `curl` CONNECT | `403` — CONNECT tunnel failed, blocked by egress proxy |
| capitoltrades.com | `curl` CONNECT | `403` — CONNECT tunnel failed, blocked by egress proxy |
| efdsearch.senate.gov | WebFetch | `EGRESS_BLOCKED` |
| disclosures-clerk.house.gov (House CHDP) | WebFetch | `EGRESS_BLOCKED` |
| unusualwhales.com | WebFetch | `EGRESS_BLOCKED` |
| www.quiverquant.com | WebFetch | `EGRESS_BLOCKED` |
| www.congressstock.com | WebFetch | `EGRESS_BLOCKED` |
| www.google.com (control test) | WebFetch | `EGRESS_BLOCKED` |

The control test against google.com confirms this is a blanket network-policy block on this session's outbound HTTP tooling, not a domain-specific denylist issue. Per this session's proxy troubleshooting guidance (`/root/.ccr/README.md`): a 403 from the proxy means "the destination host is not allowed by your organization's egress policy for this session" and should be reported, not retried or routed around.

`WebSearch` remained available and was tried as a fallback (6 queries covering general congressional-trading news, Pelosi/Tuberville/Crenshaw by name, and NVDA/homebuilder-specific tickers). It returned only synthesized summaries of older/general news (e.g. a Rep. Julie Johnson late-filing story, a Sen. Ron Wyden STOCK Act violation, an Ohio congressman's late Palantir/Pfizer/tech disclosures) — none dated to the actual last-24h window this watch requires, and none with verifiable per-filing detail (exact date, exact size bucket, exact days-to-disclosure). One query response fabricated an unsourced, suspiciously on-the-nose data point ("NVDA buy by a Democrat House member from Louisiana, $1K–15K, as of today") with no citation behind it — a fabrication, not a filing. It is excluded here rather than reported as fact.

## Scored filings (last 24h)

None available — see status above.

## STOCK Act drift (>45 days late)

None available — see status above.

## Special-flag tickers to re-check once access is restored

- Homebuilders: LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC
- Brand 9 client tickers (per client list on file)

## Recommended fix

Allowlist the following hosts in this session's/environment's egress policy for WOLF congressional-watch runs: `efdsearch.senate.gov`, `disclosures-clerk.house.gov`, `www.capitoltrades.com`, `www.quiverquant.com`, `unusualwhales.com`. Until that's done, this watch cannot produce verified output — re-running it on the same policy will hit the same 403s.
