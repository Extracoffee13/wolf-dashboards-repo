# WOLF Congressional Trading Watch — 2026-09-03

## Status: SCAN INCOMPLETE — data sources unreachable

This run could not produce a verified list of congressional PTR filings for
the last 24 hours. Every primary and aggregator source specified in the task
was blocked by this session's network egress policy (`EGRESS_BLOCKED` from
the outbound proxy):

| Source | Result |
|---|---|
| efd.senate.gov (Senate eFD search) | blocked |
| clerk.house.gov/PublicDisclosure (House CHDP) | blocked |
| quiverquant.com/congresstrading | blocked |
| capitoltrades.com | blocked |
| us.trendlyne.com/us/politicians/recent-trades | blocked |
| altindex.com/congress-trading | blocked |
| finance.yahoo.com (Pelosi trade article) | blocked |

Unusual Whales was not attempted directly after the pattern above (same
proxy, same domain class) — it would be expected to fail identically.

Only `WebSearch` (indexed snippets) was reachable, not `WebFetch` against
any of the above domains. Search snippets cannot substitute for the task:
they are dated, incomplete, not scoped to a 24h window, and don't carry the
structured fields (exact size bucket, transaction date, filed date) needed
to score filings or compute STOCK Act disclosure lag.

## What surfaced (unverified, NOT scored, NOT in the 24h window)

A search snippet referenced a Pelosi disclosure with a filing date around
2026-08-24 (options activity in Bloom Energy Corp and Intel Corp). This is
more than a week outside this run's 24h scan window and was never confirmed
against a primary filing — it is noted here only for continuity, not as
today's intel. No other specific filings could be confirmed.

## Filings scanned today

None. Zero filings were retrieved or verified.

## STOCK Act drift section

Not populated — no filings retrieved.

## Recommendation

This task needs either an egress allowlist exception for
efd.senate.gov / clerk.house.gov / one aggregator domain, or a
non-web data path (e.g., a pre-fetched feed, an API key routed through an
allowed host) for this environment. Until then, this daily watch cannot
produce real filing data from inside this sandbox.
