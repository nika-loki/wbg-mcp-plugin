---
name: farm-monitor
description: "Morning delta for a farm area \u2014 today's new/cut/status call list plus the saved_searches webhook digest that delivers it daily."
---

# Farm monitor — daily delta on a farm area

Purpose: the morning routine — what changed in the farm (new listings, price
cuts, status moves), as a call list today and a delivered digest every day
after.

## Inputs

Collect these before starting. If the skill was invoked with arguments
(`/wbg-mls:farm-monitor <values…>`), `$ARGUMENTS` holds them — map them to
the inputs below when they fit (e.g. an MLS number is the subject):

- **zips** — comma-separated 5-digit zips (example: 92102)
- **price_max** — optional price ceiling (example: 1000000)

## Steps — the one-time sweep

1. `changed_listings` with `since=<yesterday's date>` (first run: 7 days
   back), `zips`, `kinds=['new','price_change']` — today's call list. Price
   rows carry old→new: a cut is a seller getting real; a raise is a
   re-list in disguise. Add `status_change` to catch Pendings before they
   close (a falling-through Pending is a buyer opportunity).
2. Assemble the list by fit: new actives first, then cuts deepest-first.
   Include agent + office columns for the touch-point.

## Steps — set up the recurring digest

3. Ask the user ONCE for a Slack-style webhook URL (https only), then
   `saved_searches` with `action='create'`, `tool='changed_listings'`,
   `args={{"zips": [...], "kinds": ["new","price_change"]}}` (leave `since`
   out — the runner substitutes the last 24h), `schedule='daily'`,
   `webhook_url=<the url>`. Args are validated at save time.
4. `saved_searches` with `action='run'` on the new search to fire a first
   digest immediately and confirm delivery works.

## Traps

- Deletions purge on a ~2-3 day cadence — absence is not proof of deletion.
- The change log keeps 60 days; older history needs the current-state tools
  (`market_analytics`, `run_sql`), not the delta feed.
- Digests are private per account — create with the user's own key/session.
