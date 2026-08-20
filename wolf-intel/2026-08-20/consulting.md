# WOLF Consulting Pulse — 2026-08-20

**Status: NO DIGEST. Run blocked by network egress policy.**

No papers are reported today. Not because the scan found nothing worth
reporting, but because the scan could not be performed. This file is a run
log, not a digest. It contains no research findings and none should be read
into it.

## What was attempted

Three parallel scanners covering the full source list: McKinsey/MGI, BCG +
BCG Henderson Institute, Bain, Deloitte, KPMG, EY, PwC, Strategy&, Oliver
Wyman, Roland Berger, and arXiv (cs.AI / econ.GN / q-fin).

## What blocked it

`WebFetch` returns `EGRESS_BLOCKED` for every source domain. Verified by
direct test, not only via subagent report:

| Domain | Result |
|---|---|
| mckinsey.com, bcg.com, bain.com | EGRESS_BLOCKED |
| bcghendersoninstitute.com | EGRESS_BLOCKED |
| deloitte.com, kpmg.com, ey.com, pwc.com | EGRESS_BLOCKED |
| strategyand.pwc.com, oliverwyman.com, rolandberger.com | EGRESS_BLOCKED |
| arxiv.org, export.arxiv.org | EGRESS_BLOCKED |
| en.wikipedia.org (control) | EGRESS_BLOCKED |

The control domain failing is the key diagnostic: this is a broad egress
allowlist, not publisher anti-scraping or paywalls. `curl "$HTTPS_PROXY/__agentproxy/status"`
reports the proxy healthy with `selective: false`, and logs 403 CONNECT
denials for arxiv.org, export.arxiv.org, openreview.net, huggingface.co,
api.semanticscholar.org, paperswithcode.com, and alphaxiv.org.

Per `/root/.ccr/README.md`, policy denials are reported, not routed around.
No mirrors, caches, or alternate hosts were attempted.

## Why WebSearch was not used as a substitute

`WebSearch` still functions, and it would have been easy to assemble three
plausible-looking entries from it. That would have been fabrication, for two
concrete reasons:

1. **No date verification is possible.** The digest's entire premise is a
   24-48h window. Search returns titles and URLs but not publisher-stamped
   dates. Nothing could be confirmed as published 2026-08-17..20. The search
   index also skews heavily toward evergreen "2026 Outlook" pages that are
   2026-branded but were published months earlier — precisely the failure
   mode that would corrupt a freshness-based digest.

2. **The search summarizer is provably contaminated.** Asked for McKinsey
   agent-adoption data, it returned confident, precise figures ("31% of
   enterprises run at least one AI agent in production", "88% of agent pilots
   fail to graduate", "median time-to-value 5.1 months") while the underlying
   link list contained only vendor blogs — onereach.ai, joget.com, azumo.com,
   digitalapplied.com. These are not McKinsey figures. Publishing them under
   a consulting firm's name would have put invented statistics into the
   PRAXIS pipeline and, via wolf-brief, in front of readers.

A digest whose value proposition is "expensive research, filtered" is worth
nothing if the research is hallucinated. Skipping a day costs one day.
Publishing fabricated statistics under McKinsey's and BCG's names costs the
credibility of every prior and future entry.

## Candidate leads (UNVERIFIED — do not cite, do not treat as findings)

Recorded only so tomorrow's run has a starting point, and so the gap is
visible. Every item below is second-hand from search snippets. No page was
opened. No date is confirmed. Several may predate the window or not exist as
described.

- BCG, "Powering AI Through Grid-Positive Data Centers" — URL appeared in
  search results so the page likely exists; asserted 2026-08-18 by one
  snippet. Unverified.
- McKinsey, public-sector AI maturity piece — asserted 2026-08-18, syndicated
  same week by GovMedia and Tribune India. The article's own URL could not be
  resolved. Reported claim (third-hand): domain-based programs reach
  production at a far higher rate than single-use-case projects. Unverified.
- McKinsey, "Agentic AI change management: Closing the adoption gap" —
  asserted 2026-08-07, likely outside the window. Reported 1:3:5 ratio
  (technology : process redesign : capability building). Unverified, and the
  most load-bearing claim to check first when access is restored.

The arXiv scanner returned more, and more specific, candidates — real-looking
IDs cross-checked against each other (one wrong ID, arXiv:2608.09256, was
caught and corrected to 2608.09251), with dates inferred from ID position
rather than a fetched submission date. No abstract page was opened, so none
of the reported findings or statistics below are confirmed:

- arXiv:2608.14588, "The Hallucination Snowball" — multi-agent LLM pipelines,
  error propagation across handoffs, tested on a 4-agent financial-analysis
  pipeline (FinanceBench). Most directly on-theme for (C) if real: argues
  end-of-pipeline review is close to useless and verification belongs at
  every handoff. Est. ~Aug 14.
- arXiv:2608.13926, "Never the Number" — structural abstention for LLM
  systems whose output is consumed as fact (text-to-SQL / agent actions);
  proposes generation should never sit in the value-return path. Est.
  ~Aug 13-14.
- arXiv:2608.12236, "How Organizations Use AI: Evidence from ChatGPT" —
  Chatterji, Holtz, Rakholia, Tambe, Weeratunga; ChatGPT Enterprise telemetry
  linked to firm financials, adoption concentrated in larger/higher-SG&A/R&D
  firms. Plausible as real work (these authors have published adjacent
  ChatGPT-usage research before) but unconfirmed here. Est. ~Aug 12, likely
  just outside the window.
- arXiv:2608.13871, "Financial Technologies, Labor Markets, and Wage
  Inequality: Evidence from Instant Payment Systems" — Brazil's Pix rollout,
  wage gains concentrated in small, cash-intensive establishments. Est.
  ~Aug 13-14.
- arXiv:2608.09988, "OpenPM" — point-in-time-audited LLM portfolio-management
  agent benchmark; reported finding that analyst/selection quality dominates
  constructor choice. Est. ~Aug 10, likely outside the window.

If access is restored, verify 2608.14588 and 2608.12236 first — they're the
best fit for (C) and (B) respectively if the reported content holds up.

## Required fix

Either:

1. **Allowlist the source domains** for this environment: the ten publisher
   domains above plus `export.arxiv.org`.
2. **Switch the job to RSS/Atom feeds** (preferred). Several of these firms
   publish feeds, and feeds carry publisher-stamped `pubDate` fields. That
   solves the date-verification problem structurally, in a way HTML scraping
   never does — even with full network access, scraped pages often bury or
   omit publication dates.

Also worth confirming whether this scheduled job is intended to run in an
environment with broader network policy than the one it currently gets.

## Files not written

`wolf-brief/2026-08-20-consulting.md` was deliberately not created. A public
brief requires at least one verified paper; there were none. No
`RESEARCH_TARGETS` block was emitted — targets derived from unverified leads
would spend the local research budget chasing possibly-nonexistent papers.
