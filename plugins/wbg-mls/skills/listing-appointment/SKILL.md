---
name: listing-appointment
description: "Defensible market story for a farm area: what's selling at what pace and discount, the 2-year trend, and the competitive board."
---

# Listing appointment — the one-pager

Purpose: win the room with a defensible market story for the farm area:
what's selling, at what pace, at what discount, against whom.

## Inputs

Collect these before starting. If the skill was invoked with arguments
(`/wbg-mls:listing-appointment <values…>`), `$ARGUMENTS` holds them — map them to
the inputs below when they fit (e.g. an MLS number is the subject):

- **zips** — comma-separated 5-digit zips (example: 92102,92113)

## Steps

1. `market_report` with `filters={{"zips": [...], "date_from": <6 months
   ago>, "date_to": <today>}}` and sections
   `closed_stats,inventory,dom,absorption,price_bands` — the core deck.
   CONFIRM the `[report filters: …]` header matches the ask before
   narrating; NULL sub_type rows fall to *_other buckets.
2. `market_analytics` with `metric='price_trend'`, `bucket='month'` on the
   zips for the 2-year trend lines (the "where is the market going" slide).
3. `agent_production` with the zips over the last 12 months,
   `role='list'`, `top_n=10` — who they are competing against. Sides credit
   co-listed deals to both agents; placeholder attributions are filtered.
4. Close with the coverage discipline: any pre-floor question gets the
   partial-answer caveat said OUT LOUD, not just in a footer.

## Traps

- Every number needs the place + timeframe said with it; the footer carries
  the snapshot watermark — surface it when quoting medians.
- Zip coverage can start later than the feed floor (mid-range gaps) — the
  report header discloses clamps; repeat them.
- Don't improvise an absorption number from closings alone — the tool
  computes months of inventory already.
