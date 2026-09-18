---
name: open-house-round
description: "The weekend open-house round for a farm area — schedule, per-open cheat sheet, and which opens you could sit."
---

# Open-house round — the weekend plan

Purpose: build the weekend open-house round for a farm area — the schedule
in order, a cheat sheet per stop, and which opens you could sit.

## Inputs

Collect these before starting. If the skill was invoked with arguments
(`/wbg-mls:open-house-round <values…>`), `$ARGUMENTS` holds them — map them to
the inputs below when they fit (e.g. an MLS number is the subject):

- **zips** — comma-separated 5-digit zips (example: 92101,92103)
- **price_max** — optional price ceiling for the buyer you're hosting (example: 950000)

## Steps

1. `open_houses` with `zips` (defaults to the upcoming Sat–Sun window;
   schedules print in Pacific time). Skim before filtering — a light
   weekend is a farming opportunity, not a failure.
2. Filter for fit: `price_max` for the buyer you're hosting,
   `sub_type_group` when it matters (e.g. 'condo'). To find opens you
   could SIT (the side-hustle), add `exclude_office_names` with YOUR
   brokerage's name — everything left is another agent's listing.
3. Assemble the round chronologically — per stop: time, address, price,
   beds/baths, DOM, sub_type, list agent + phone (all in the open_houses
   output already).
4. For the 1-2 stops you'll sit or preview seriously: `get_listing` for
   remarks + showing instructions (MLS-confidential — never read private
   remarks to buyers verbatim).

## Traps

- The window must be within today-7..+60 days and at most 14 days wide —
  widen week by week, not in one ask.
- Feeds lag and open houses get cancelled same-day — confirm times in the
  MLS before driving; this is a plan, not a promise.
- Showing instructions in the output are agent-to-agent confidential; keep
  them out of anything you hand to a buyer.
