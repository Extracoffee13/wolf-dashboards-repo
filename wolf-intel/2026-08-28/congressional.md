# WOLF Congressional Trading Watch — 2026-08-28

## Run status: BLOCKED — no verified filing data

This scheduled run could not produce a scored list of congressional PTR
filings for the last 24 hours. Every required data source is unreachable
from this execution environment:

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov | Blocked by network egress proxy (403 on CONNECT) |
| House CHDP | disclosures-clerk.house.gov | Blocked by network egress proxy (403 on CONNECT) |
| Quiver Quantitative | quiverquant.com/congresstrading | Blocked by network egress proxy (403 on CONNECT) |
| CapitolTrades | capitoltrades.com | Blocked by network egress proxy (403 on CONNECT) |
| Unusual Whales | unusualwhales.com/politics | Blocked by network egress proxy (403 on CONNECT) |
| congressstock.com | congressstock.com/trades | Blocked by network egress proxy (403 on CONNECT) |

Both the WebFetch tool and direct `curl` from this container hit the same
proxy-level block (`CONNECT tunnel failed, response 403`), confirming this
is an environment network-policy restriction, not a per-site failure.

A general web-search tool (not a live-page fetch) returned only stale,
non-itemized snippets — e.g. a cached CapitolTrades meta-description citing
its newest indexed filing as **2026-08-14**, 14 days before this run, and a
Quiver news snippet about AT&T trades with no confirmed date inside the
last 24h window. That is not a reliable basis for STOCK Act filing dates,
transaction sizes, or member attribution, and none of it is used below —
publishing invented member names, tickers, or dollar amounts as if they
were real disclosures would be worse than publishing nothing.

## What did not happen

- No filings were scored (1-5).
- No STOCK Act drift (>45 day) list was produced.
- No homebuilder-ticker or Brand 9 client-ticker flags were evaluated.
- The public brief for today (`wolf-brief/2026-08-28-congressional.md`)
  is a stand-down notice, not a top-3 list — do not publish it as real
  intel.

## What needs to change before the next run

This container's outbound network policy only allowlists a short list of
package registries and the Anthropic API (see `noProxy` in the agent
proxy status); it does not allowlist efdsearch.senate.gov,
disclosures-clerk.house.gov, quiverquant.com, capitoltrades.com, or
unusualwhales.com. To get real data on the next scheduled run, one of the
following is needed:
1. Add those domains to the environment's network egress allowlist, or
2. Point this task at an already-allowlisted API/data proxy for
   congressional trading data, or
3. Run this specific task from a session/environment with broader network
   access and have it write results back to this repo.

Filed by the scheduled WOLF congressional-trading-watch routine.
