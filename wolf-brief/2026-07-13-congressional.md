# WOLF Congressional Trading Watch — 2026-07-13

**No brief today.** Today's scan hit a data-access failure — every source
(Senate eFD, House CHDP, CapitolTrades, Quiver Quantitative, Unusual Whales,
and other aggregators) returned HTTP 403 on every attempt, including a
control fetch against a mainstream news site. That points to a blocked
outbound-fetch path in this run's environment rather than a quiet trading
day.

No filings were verified, so no scored trades are published. This is a
gap in coverage, not a "nothing happened" signal — see
`wolf-intel/2026-07-13/congressional.md` for the full failure log and the
fix needed before the next run.
