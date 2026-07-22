# WOLF Congressional Trading Watch — 2026-07-22

## Status: SCAN BLOCKED — no verified filing data retrieved

This is the first run of this watch. Every primary and aggregator source attempted
returned a hard block (HTTP 403) to automated fetch, and the one open dataset
mirror found on GitHub is stale (no entries past ~2021). No congressional PTR
filing data for the last 24h could be verified from a live source this run.
Rather than fabricate member/ticker/size entries, this report documents what
was attempted and what should change before tomorrow's run.

## Sources attempted (all failed)

| Source | URL | Result |
|---|---|---|
| Senate eFD | efdsearch.senate.gov/search/home/ | 403 |
| House Clerk FD portal | disclosures-clerk.house.gov/FinancialDisclosure | 403 |
| House Clerk PTR PDF (direct, found via search) | disclosures-clerk.house.gov/public_disc/ptr-pdfs/2026/20033725.pdf | 403 |
| Quiver Quantitative | quiverquant.com/congresstrading/ | 403 |
| CapitolTrades (page) | capitoltrades.com/trades | 403 |
| CapitolTrades (internal API) | bff.capitoltrades.com/trades | 403 |
| Unusual Whales | unusualwhales.com/politics | 403 |
| Benzinga government trades tracker | benzinga.com/government-trades | 403 |
| Benzinga individual article (Tuberville 2026 first trades) | benzinga.com/news/politics/26/07/60537231/... | 403 |
| MarketBeat politicians tracker | marketbeat.com/politicians/ | 403 |
| AltIndex congress tracker | altindex.com/congress-trading | 403 |
| InsiderFinance congress trades | insiderfinance.io/congress-trades | 403 |
| CongressStock.com | congressstock.com | 403 |
| GovTrades.com | govtrades.com/congress-stock-tracker | 403 |
| PelosiTracker.app | pelositracker.app/stocks | 403 |
| GitHub open dataset mirror | github.com/timothycarambat/senate-stock-watcher-data | Reachable, but data stops ~Jan 2021 (stale, not maintained through 2026) |

All of the above were checked directly (not just search snippets). WebSearch
(Google-indexed snippets) worked throughout the run and is how the table above
and the note below were sourced — it just can't substitute for a live filing
feed with ticker/size/date granularity.

## What WebSearch surfaced (unverified against a primary filing — context only, NOT scored)

- Benzinga headline (via search, article body itself blocked): "Senator Who
  Opposes Ban on Congress Trading Discloses First Trades of 2026" — appears to
  reference Sen. Tommy Tuberville, but the size/ticker/date detail could not be
  confirmed from the source article (403). **Not scored — unverified.**
- Roll Call, 2026-07-21: "Dashed dreams for consensus group ahead of
  stock-trading vote" — the House was preparing a floor vote on a bill to
  restrict/ban members of Congress from trading individual stocks. This is
  legislative-process news, not a PTR filing, and is included only as relevant
  background for the STOCK Act beat.

## Cluster / homebuilder / Brand 9 client-ticker flags

No positions checked — zero verified filings this run means no size-bucket,
cluster, or ticker-flag scoring could be performed.

## STOCK Act drift (late filings >45 days)

Not computed — no verified filing set to check against.

## Recommendation for tomorrow's run

The blocking pattern (uniform 403 across ~15 distinct hosts including .gov
domains) indicates bot/WAF protection on these sites rejects the fetch tool's
request signature — this is not an egress-proxy policy block (proxy status
showed zero relay failures; the destination hosts themselves are the ones
returning 403). To get real data flowing:
1. Use a paid/keyed API (Quiver Quantitative has a documented REST API with an
   API key) instead of scraping the HTML/JS front end.
2. Or wire this task to a connector/MCP tool with authenticated or
   browser-based access rather than plain WebFetch, if one becomes available.
3. Or accept a manual seed: paste in filing data from a source the user has
   direct access to, and this watch will score/format it.
