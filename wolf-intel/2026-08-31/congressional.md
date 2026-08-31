# WOLF — Congressional Trading Watch — 2026-08-31

Status: **NO SCAN COMPLETED — DATA SOURCES UNREACHABLE**

## What happened

This session's network egress policy blocks direct fetches to every source
this task specifies. `WebFetch` returned `EGRESS_BLOCKED` for all of:

- `efdsearch.senate.gov` (Senate eFD)
- `disclosures-clerk.house.gov` (House CHDP)
- `www.capitoltrades.com`
- `www.quiverquant.com`
- `unusualwhales.com`
- even generic domains (`en.wikipedia.org`, `www.google.com`) — confirming
  this is a blanket environment-level block, not a per-site one.

`WebSearch` (a separate, server-side search backend not subject to the same
block) still worked, but it only returns indexed news summaries, not
filing-level rows — no per-transaction ticker/size-bucket/filed-date triples
that could be scored per the rubric. Notably, one aggregator's own search
result stated its most recent indexed trade was dated **August 19, 2026** as
observed on **August 28, 2026** — a ~9-day lag on the aggregator side, before
this session's access problem even enters the picture.

Given that, no filing-level table is included below. Fabricating tickers,
size buckets, member names, or day-counts to fill this rubric out would be
worse than an honest gap — this file exists to feed a decision pipeline
(PRAXIS inbox, wolf-brief), and false structured "intel" is more dangerous
than a missed day.

## Incidental context (not verified as last-24h, not scored)

- Search turned up a Benzinga/Yahoo Finance report of a Pelosi PTR disclosing
  large stock/options activity (including Bloom Energy, Intel), but the
  reporting itself reads as roughly a week old relative to today, not a
  last-24h filing. Not usable for this brief's "last 24h" requirement.

## Recommendation

WOLF cannot do this job from an environment without browsing access to
efd.senate.gov / clerk.house.gov / the aggregators. Options, in order of
preference:
1. Allowlist those specific domains in this environment's egress policy for
   scheduled WOLF runs.
2. Run this watch from an execution path that already has real browser
   access (e.g. a Hermes/Claude-in-Chrome session), if one exists in this
   ecosystem, rather than this sandboxed session.
3. If neither is available, treat this scan as a known daily gap rather than
   silently filling it with invented data.

## STOCK Act drift section

Not populated — no filings were retrieved this run.
