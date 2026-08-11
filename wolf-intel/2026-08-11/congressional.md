# WOLF Congressional Trading Watch — 2026-08-11

**Status: DATA COLLECTION FAILED — no scored filings below are real. Do not act on this file.**

## What happened

This run attempted to scan the last 24h of US congressional PTR (Periodic
Transaction Report) filings via:

- Senate eFD (`efdsearch.senate.gov`)
- House CHDP (`disclosures-clerk.house.gov`)
- Quiver Quantitative (`quiverquant.com/congresstrading`)
- CapitolTrades (`capitoltrades.com`)
- Unusual Whales congressional feed

Every one of these hosts is blocked by this session's network egress policy
(`EGRESS_BLOCKED` from the WebFetch tool). `WebSearch` remained available and
returned indexed snippets, but those snippets are stale (dated March–July
2026 in several cases), partial, and not scoped to "last 24 hours" — they are
not a reliable basis for member-by-member PTR data, transaction sizes, or
STOCK Act filing-lag calculations.

Per this session's own proxy documentation (`/root/.ccr/README.md`): "do not
retry or route around" an org egress denial — report the blocked host rather
than working around it. That's what this file does.

## What was NOT done

- No filings were scored 1–5.
- No homebuilder-ticker or Brand 9 client-ticker auto-bump flags were
  evaluated, because no filing data was retrieved.
- No STOCK Act drift (>45 day) section was produced, because no filing dates
  were retrieved.

Any prior day's `wolf-intel/*/congressional.md` content should NOT be assumed
to still be accurate — this file only speaks to today, 2026-08-11.

## Recommended fix

Grant this environment's network egress policy an allowlist entry for at
least one of: `efdsearch.senate.gov`, `disclosures-clerk.house.gov`,
`www.quiverquant.com`, `www.capitoltrades.com`. Until one of those is
reachable by `WebFetch`, this watch cannot produce real scored output and
should not be trusted to run unattended.
