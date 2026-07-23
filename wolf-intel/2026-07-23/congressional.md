# WOLF Congressional Trading Watch — 2026-07-23

## Run status: BLOCKED — no verified filing data collected

This run could not scan primary or aggregator sources for congressional PTR
filings. Every outbound `WebFetch` call this session — including a control
fetch to `example.com` with no relation to congressional trading data —
returned `HTTP 403 Forbidden`. Per this session's proxy diagnostics
(`/root/.ccr/README.md`), a 403 at the proxy layer signals an organization
egress-policy denial, not a transient/retryable failure, and the guidance is
explicit: **do not retry or route around it, report the blocked host.**

Sources attempted and blocked:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/ | 403 |
| House CHDP | disclosures-clerk.house.gov/PublicDisclosure/FinancialDisclosure | 403 |
| Quiver Quantitative | quiverquant.com/congresstrading | 403 |
| CapitolTrades (site) | capitoltrades.com/trades | 403 |
| CapitolTrades (API) | bff.capitoltrades.com/trades | 403 |
| Unusual Whales | unusualwhales.com/politics/insider_trades | 403 |
| Control fetch (sanity check) | example.com | 403 |

Because `WebFetch` was unavailable for the entire session, no filing could be
read, dated, sized, or scored against the STOCK Act 45-day window with any
confidence. **No scored list is included below** — publishing one would mean
either leaving it empty (misleading — implies a clean scan) or filling it
from unverifiable secondary snippets, which risks attributing specific
trades, sizes, and dates to real, named members of Congress without a
primary-source citation. That risk is not acceptable for a file meant to
feed downstream decisions, so this run stops here instead.

## What did surface (WebSearch only, NOT verified — do not treat as filings)

`WebSearch` (a separate, working tool that returns curated snippets rather
than fetched pages) surfaced a small number of secondary-source fragments
during triage. These are **not confirmed against a primary source, not
confirmed to be within the last 24 hours, and must not be used for scoring
or the public brief**:

- A Benzinga headline referenced a senator "who opposes a ban on congress
  trading" disclosing first-2026 trades — headline only, body unreadable
  (403), ticker/size/date unconfirmed.
- A Seven Lakes Research post referenced Paul Pelosi disclosures (Broadcom
  call options, reported size $1M–$5M) covering activity disclosed between
  June 24 and July 1 — outside the last-24h window even at face value, and
  unreadable in full (403).
- A search summary referenced a Tuberville PTR disclosed July 16 covering
  trades from June 8–9 (American Water Works, Lockheed Martin, Tractor
  Supply, Westinghouse Air Brake) — also outside the last-24h window, and
  not independently verified against the Senate eFD record.

None of the above meets the bar for inclusion in a scored intel list. No
homebuilder-ticker or Brand 9 client-ticker auto-bump flags apply, since no
verified filing was reviewed. No STOCK Act drift section is included for the
same reason.

## Next scheduled attempt

Retry on the next scheduled run. If `WebFetch` is still blocked, this same
status should be reported again rather than backfilling with unverified
data — an administrator needs to review whether efdsearch.senate.gov,
clerk.house.gov, and the aggregator domains above are intended to be in this
session's egress allowlist.
