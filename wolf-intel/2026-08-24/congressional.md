# WOLF Congressional Trading Watch — 2026-08-24

## Run status: BLOCKED — no verified filings retrieved

This run could not produce a scored list of last-24h congressional PTR
filings. Every required source was unreachable from this execution
environment:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov | `EGRESS_BLOCKED` (network egress proxy) |
| House CHDP | disclosures-clerk.house.gov | `EGRESS_BLOCKED` |
| CapitolTrades | capitoltrades.com | `EGRESS_BLOCKED` |
| Quiver Quantitative | quiverquant.com | `EGRESS_BLOCKED` |
| Unusual Whales | unusualwhales.com | `EGRESS_BLOCKED` |

Direct fetches to unrelated control domains (`google.com`, `en.wikipedia.org`)
were also blocked, confirming this is a session-level network policy
restricting outbound HTTP fetches generally, not a per-site block on
trading-intel sites specifically. `WebSearch` (hosted search, not a direct
fetch) remained available and was used as a fallback, but it only returns
summarized snippets of indexed pages — not the itemized, dated, sized filing
records this watch needs to score and diff against a 24h window.

## What WebSearch surfaced (not verified, not scored — for context only)

These are stale or aggregate data points pulled from search snippets, **not**
confirmed last-24h filings. None of them meet the bar for the scored list or
the public brief:

- Rep. Michael A. Rulli (R-OH-06) — filing reported ~2026-08-10 covering
  sales of NVDA, AAPL, CCI, NOW and a purchase of META, KO. Two weeks stale
  relative to this run; exact size buckets and disclosure lag not available
  from search snippets.
- Aggregate stat as of 2026-07-31: 59 of 100 sitting senators have disclosed
  trades this Congress; Tommy Tuberville (R-AL) remains the most active
  discloser by trade count (1,499 lifetime). Not filing-level, not dated to
  this window.
- H.R. 7008 (congressional stock-trading restriction bill) passed the House
  232–198 on 2026-07-22; pending in the Senate. Context, not a filing.

No homebuilder-ticker or Brand 9 client-ticker touches were identified in
any of the above (none of it is dated to the last 24h, so this is not a
clean read either way).

## STOCK Act drift section

Not populated this run — no filing-level disclosure-lag data was retrievable.

## Recommendation

This watch needs one of: (a) an allowlisted egress path to
efdsearch.senate.gov / disclosures-clerk.house.gov / capitoltrades.com /
quiverquant.com for this session's environment, or (b) a licensed data feed
/ API key (e.g. Quiver's paid API) fetched through an approved endpoint.
Until then, this daily slot cannot produce a real scored list — flag to the
operator rather than let the brief silently drift to a fabricated or
copy-pasted forecast that has no basis in an actual filing.
