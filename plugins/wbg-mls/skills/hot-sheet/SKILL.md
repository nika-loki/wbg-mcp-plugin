---
name: hot-sheet
description: "The morning hot sheet for a farm area — today's new/cut/status changes as a call list, run on demand."
---

# Hot sheet — your farm's morning changes

Purpose: the hot sheet — the morning report every agent runs: what changed
in the farm (new listings, price cuts, status moves), as today's call list.

## Inputs

Collect these before starting. If the skill was invoked with arguments
(`/wbg-mls:hot-sheet <values…>`), `$ARGUMENTS` holds them — map them to
the inputs below when they fit (e.g. an MLS number is the subject):

- **zips** — comma-separated 5-digit zips (example: 92102)
- **price_max** — optional price ceiling (example: 1000000)

## Steps

1. `changed_listings` with `since=<yesterday's date>` (first run: 7 days
   back), `zips`, `kinds=['new','price_change']` — the call list. Price
   rows carry old→new: a cut is a seller getting real; a raise is a
   re-list in disguise. Add `status_change` to catch Pendings before they
   close (a falling-through Pending is a buyer opportunity).
2. Assemble the list by fit: new actives first, then cuts deepest-first.
   Include agent + office columns for the touch-point.

NOTE: recurring delivery is NOT available yet — do not promise scheduled
updates and do not ask the user for any delivery URL. If they ask for
every-morning updates, say it's coming and run the hot sheet on demand
for today.

## Output format

- `# Hot sheet — <zips> · <date>`
- **Today: N new · M price cuts · K status moves** — one bold line
- **Call list** — table, new actives first, then cuts deepest-first:
  Address | Price | Δ | DOM | Beds | Agent | Office
- **Worth a call today** — 2-3 bullets: the cuts (a seller getting real) and
  fresh Pendings (a fall-through opportunity)
- Footer: the sweep window ("since <date>"), one line.

## Traps

- Deletions purge on a ~2-3 day cadence — absence is not proof of deletion.
- The change log keeps 60 days; older history needs the current-state tools
  (`market_analytics`, `run_sql`), not the delta feed.
