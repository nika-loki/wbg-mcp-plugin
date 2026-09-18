---
name: buyer-match-sweep
description: "Run a buyer profile against the last 48 hours of new listings and price cuts; ranked shortlist with quick comp checks."
---

# Buyer-match sweep — 48h matches for a buyer profile

Purpose: run a buyer's criteria against the last 48 hours of movement and
hand back a ranked shortlist with a quick comp check on each — the
"anything new for my buyer" answer.

## Inputs

Ask the user for any you don't already have:

- **zips** — comma-separated 5-digit zips (example: 92101,92103)
- **price_max** — price ceiling (example: 950000)

## Steps

1. `changed_listings` with `since=<48 hours ago>`, `zips`, `price_max`,
   `kinds=['new','price_change']`, `status='Active'` — the fresh matches.
   A price CUT on something previously above budget can now qualify —
   that's why price changes are in the sweep, not just new listings.
2. Rank by fit (budget headroom, beds/baths match from the joined listing
   context, DOM — new-to-market first).
3. For the top 3: `comps` with the subject, `closed_within_months=3`,
   `limit=3` — one-line support for "priced right / room to offer".
4. Present a table (address, price, Δprice if cut, DOM, beds/baths, the
   comp verdict) + the caveat line.

## Traps

- Say the sweep window out loud ("since <date>") — it bounds the claim.
- Status filter is CURRENT status: a just-Pended listing won't appear as a
  new Active match; catch those with `status_change` kind sweeps.
- If nothing matched, say "zero matches in 48h" — do not pad with stale
  inventory unless asked (the user can widen with `open_houses` /
   `run_sql` on actives).
