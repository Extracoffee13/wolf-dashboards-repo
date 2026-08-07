# WOLF Congressional Trading Watch — 2026-08-07

**Status: RUN FAILED — no filing data collected.**

## What happened

This scan is a scheduled automated task with no live operator watching. It
attempted to pull the last 24h of US congressional Periodic Transaction
Reports (PTRs) from:

- Senate eFD (`efdsearch.senate.gov`)
- House CHDP (`disclosures-clerk.house.gov`)
- Quiver Quantitative (`www.quiverquant.com`)
- CapitolTrades (`www.capitoltrades.com`)
- Congress Stock Tracker (`www.congressstock.com`) and TrendSpider (`trendspider.com`), tried as fallbacks

Every one of these hosts returned `EGRESS_BLOCKED` from this session's
network policy proxy (`/root/.ccr/`, org egress allowlist). Per the proxy's
own operating instructions, a blocked host is an organization policy denial
that must be reported, not retried or routed around. A generic web search
was also attempted and returned only general/background material (how the
STOCK Act works, an April 2026 article snippet) — nothing dated within the
last 24 hours, and nothing usable as a real, sourced filing record.

**No filing data was retrievable this run.** Rather than fabricate member
names, tickers, trade sizes, or filing dates — which would be actively
dangerous to publish as "intel" in a trading-adjacent pipeline — this report
is being filed empty, with the blocker documented, so the failure is visible
instead of silently papered over.

## Filings found (last 24h)

None retrieved. 0 filings scored.

## STOCK Act drift (>45 days late)

Not evaluable this run — no filing data retrieved.

## Special flags status

- Homebuilder tickers (LEN, KBH, DHI, PHM, TOL, MTH, TPH, NVR, BZH, MDC, MHO, TMHC): not evaluable, no data.
- Brand 9 client tickers: no client-ticker list exists in this repo to check against; also not evaluable regardless due to the data outage.

## Recommended fix

For this task to run for real, this session (or the scheduled environment
it runs in) needs egress allowlisting for at least one of: `efdsearch.senate.gov`,
`disclosures-clerk.house.gov`, `www.capitoltrades.com`, or `www.quiverquant.com`.
Until one of those is reachable, this daily watch cannot produce real output.
