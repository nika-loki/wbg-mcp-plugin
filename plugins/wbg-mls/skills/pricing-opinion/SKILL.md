---
name: pricing-opinion
description: "Seller-side pricing: the comps that matter, market tempo and 12-month trend, assembled into a defensible list-price RANGE with the evidence attached."
---

# Pricing opinion — where should this list?

Purpose: the seller conversation. Assemble what the comps actually support,
at what market tempo and direction, into a defensible list-price RANGE with
the evidence attached. The number you recommend is your professional
judgment — this supplies the support and the framing, never "the" price.

## Inputs

Collect these before starting. If the skill was invoked with arguments
(`/wbg-mls:pricing-opinion <values…>`), `$ARGUMENTS` holds them — map them to
the inputs below when they fit (e.g. an MLS number is the subject):

- **subject** — MLS number (SDMLS or CRMLS NDP/PTP/MB/SW) or address (example: 260004759)

## Steps

1. `comps` with `subject`, `closed_within_months=3`, `limit=5`. Read the
   footer first: relaxations and coverage floors bound how hard you can
   lean on the set. Sort the comps INTO a ladder vs the subject — clearly
   superior, roughly equal, clearly inferior (beds, sqft, sub_type, street,
   condition from remarks) — and say which rungs are thin.
2. `market_analytics` with `metric='absorption'` on the subject's zip, last
   90 days — the tempo (months of inventory: <4mo seller's market carries
   the top of a range, >6mo buyer's market punishes it).
3. `market_analytics` with `metric='price_trend'`, `bucket='month'`, same
   zip, last 12 months — the direction line for the narrative ("flat at the
   top", "still climbing", "rolling over").
4. Assemble the opinion: a RANGE bracketed by the best inferior comp and
   the best superior comp; the sold-to-list % the market is currently
   enforcing (price to SELL, not to sit); the tempo + trend caveat; and the
   one-liner on what would have to be true to justify pricing above the
   range. Present the 2-3 comps that carry the number, named by address.

## Traps

- Never average the comps into a single number and call it the price — the
  deliverable is a range with rungs.
- A relaxed comps set means a WIDER range and softer language — say so.
- Say the data window out loud ("closed sales since <date>") — the coverage
  floor (SDMLS 2020-01, CRMLS 2022-01) bounds every claim.
