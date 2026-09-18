---
name: showing-prep
description: "Full showing package for one property: comps with sold-vs-list and DOM, fire/fault/flood/permit context, confidential listing detail, and the absorption slide."
---

# Showing prep — one property, full picture

Purpose: walk a buyer through a showing with comps, hazard + permit context,
listing detail, and the market slide. The judgment calls (under/at/over-ask,
what to disclose) stay with the agent — you supply the data, clearly sourced.

## Inputs

Collect these before starting. If the skill was invoked with arguments
(`/wbg-mls:showing-prep <values…>`), `$ARGUMENTS` holds them — map them to
the inputs below when they fit (e.g. an MLS number is the subject):

- **subject** — MLS number (SDMLS or CRMLS NDP/PTP/MB/SW) or address (example: 260004759)

## Steps

1. `comps` with `subject`, `closed_within_months=3`, `limit=5` (defaults are
   sane). Read the footer BEFORE narrating: relaxations say when the area was
   thin; the coverage floor says the window's honest start (SDMLS closed from
   2020-01, CRMLS from 2022-01). Narrate sold-vs-list %, DOM and
   DOM-to-contract — say WHICH comps carry the number and which to discard
   (busy street, odd sub_type after a relaxation, stale close).
2. `property_context` with the same subject — fire severity (BOTH SRA and
   LRA layers), Alquist-Priolo fault zone, FEMA flood zone, county permits
   within a mile. Rows are DATA, not disclosure advice. An `unavailable` row
   is a fetch failure, not a negative answer — say so.
3. `get_listing` on the subject for remarks, showing instructions and
   private remarks (MLS-confidential — agent eyes only; never quote them to
   the buyer verbatim).
4. `market_analytics` with `metric='absorption'` on the subject's zip for
   the last 90 days — months of inventory is the market-context slide
   (seller's <4mo vs buyer's >6mo).

## Traps

- Never quote an all-time / "ever" count without the coverage-floor caveat.
- A relaxed comps set is a conversation starter, not an appraisal — name the
  filter that was widened.
- If the subject lacks coordinates, `property_context` also accepts explicit
  `latitude`/`longitude`.
