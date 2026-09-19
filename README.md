<div align="center">

# 🏠 WBG MLS

**Your AI copilot for San Diego real-estate data.**

Ask in plain English. Get clean, ready-to-use answers — instant MLS-number
lookups, comps, pricing support, market one-pagers, hot sheets, buyer
matches, weekend open-house plans — straight from the MLS.

**v2026.919.5** · San Diego County (SDMLS + CRMLS feeds) · For WBG agents

</div>

---

## 🚀 Get started — pick your app

| Your app | Setup | Time |
|---|---|---|
| **Claude Desktop** ⭐ recommended | [3 steps below](#-claude-desktop-3-clicks) | ~5 min |
| **Claude in the browser** (claude.ai) | [Connectors flow](#-claude-on-the-web-claudeai) | ~5 min |
| **ChatGPT** | [Custom connector](#-chatgpt) | ~5 min |
| Prefer typing commands? | [Terminal / Claude Code](#-terminal--claude-code) | ~2 min |

> 💡 **Not technical? Start with Claude Desktop.** The plugin does the
> connecting for you — you just sign in with Google once.

### 🖥 Claude Desktop (3 clicks)

1. Open **Claude Desktop** → click the **pencil ✏️ (Customize)** → **Plugins**
   → **Personal plugins** → **+**
2. Paste this repo's URL → **Add marketplace**
3. Click **Install** on **WBG MLS**

That's it. The first time you ask for data, a window opens — **sign in with
your Google work account** (`@thewbgroup.com`, `@whisselrealty.com`, or
`@kylewhissel.com` are approved instantly) and click **Allow**. You never
paste a password or code into chat.

> ⚠️ **"Marketplace sync failed"?** That's a network hiccup on your Mac/PC,
> not a broken plugin. Quit Claude Desktop fully, get off VPN (or try a phone
> hotspot), reopen, and re-add. Still stuck? Install from Terminal instead —
> same plugin, one line:
> `claude --plugin-url https://github.com/nika-loki/wbg-mcp-plugin/releases/latest/download/wbg-mls.zip`

### 🌐 Claude on the web (claude.ai)

**Settings → Customize → Connectors → + → Add custom connector** → paste
`https://mls-mcp-i6dr.onrender.com/mcp` → **Connect** → Google sign-in → **Allow**. Then in any chat,
click **+ → Connectors** and tick **WBG MLS**.

### 💬 ChatGPT

**Settings → Apps & Connectors → Advanced** (turn on developer mode) →
**Create custom connector** → name it "WBG MLS" → paste
`https://mls-mcp-i6dr.onrender.com/mcp` → sign in with Google when it asks.

### ⌨️ Terminal / Claude Code

```bash
claude plugin marketplace add https://github.com/nika-loki/wbg-mcp-plugin
claude plugin install wbg-mls@wbg-internal
```

---

## ✨ What you can ask — the seven workflows

Everything below works in **plain English** — just ask like you'd text your
TC. Name an MLS number, an address, or zips and let it run.

### 🔎 Search by MLS number

The fastest ask: one MLS number — or a pasted batch, up to 8 in one call — resolved to the full record: status, prices, dates, agent + office, photos rendered inline, agent-only notes.

> **Try saying:** _"Client texted me a number off a yard sign — MLS 260016635. Look it up: what is it, what's it listed at, and who do I call?_"

**You get:** The **full record** for one number — or a comparison table for a pasted batch (up to 8 in one call) — status, prices, dates, agent + phones, photos rendered inline on request, agent-only notes marked.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:search-by-mls-number` with the inputs it needs (`mls_number`). Example: ``/wbg-mls:search-by-mls-number` 260004759`

</details>

### 🔑 Showing prep

Full showing package for one property: comps with sold-vs-list and DOM, fire/fault/flood/permit context, confidential listing detail, and the absorption slide.

> **Try saying:** _"I'm taking a buyer to see 1643 6th Unit 406 in San Diego this afternoon — MLS 260016635. Give me the full showing prep._"

**You get:** A **30-second read**, a comps table, hazard/permits (fire, fault, flood), listing notes, and the market snapshot for that zip.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:showing-prep` with the inputs it needs (`subject`). Example: ``/wbg-mls:showing-prep` 260004759`

</details>

### 💰 Pricing opinion

Seller-side pricing: the comps that matter, market tempo and 12-month trend, assembled into a defensible list-price RANGE with the evidence attached.

> **Try saying:** _"Seller wants to list their condo at 1643 6th Unit 406 (MLS 260016635 is the pending comp next door — use it as the subject). What price range does the data support?_"

**You get:** A defensible **list-price range** with the comps that carry it, market tempo, the 12-month trend — never one averaged number.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:pricing-opinion` with the inputs it needs (`subject`). Example: ``/wbg-mls:pricing-opinion` 260004759`

</details>

### 📊 Listing appointment one-pager

Defensible market story for a farm area: what's selling at what pace and discount, the 2-year trend, and the competitive board.

> **Try saying:** _"I have a listing appointment in Barrio Logan and South Park tomorrow (zips 92102 and 92113). Build me the one-pager._"

**You get:** A **market one-pager**: what's selling at what pace and discount, the 2-year trend, and the competitive board.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:listing-appointment` with the inputs it needs (`zips`). Example: ``/wbg-mls:listing-appointment` 92102,92113`

</details>

### ☀️ Hot sheet

The morning hot sheet for a farm area — today's new/cut/status changes as a call list, run on demand.

> **Try saying:** _"Run my morning hot sheet for zip 92101 under $1,000,000 — today's new listings and price cuts call list._"

**You get:** Today's **call list** — new listings first, then price cuts deepest-first — plus the 2-3 moves worth calling on today.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:hot-sheet` with the inputs it needs (`zips` · `price_max`). Example: ``/wbg-mls:hot-sheet` 92102`

</details>

### 🤝 Buyer matches

Run a buyer profile against the last 48 hours of new listings and price cuts; ranked shortlist with quick comp checks.

> **Try saying:** _"My buyer can go to $950k in downtown or Hillcrest (92101, 92103). What's new or freshly cut in the last 48 hours?_"

**You get:** A **ranked shortlist** of the last 48 hours' new listings and price cuts under budget, with a quick comp verdict on each.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:buyer-matches` with the inputs it needs (`zips` · `price_max`). Example: ``/wbg-mls:buyer-matches` 92101,92103`

</details>

### 🏡 Open-house round

The weekend open-house round for a farm area — schedule, per-open cheat sheet, and which opens you could sit.

> **Try saying:** _"Plan my open-house round for this weekend in 92101 and 92103 — schedule and a cheat sheet for each stop._"

**You get:** The **weekend plan** in order — time, stop, price, beds, agent, phone — plus which opens you could sit.

<details><summary>Power move — the exact command</summary>

`/wbg-mls:open-house-round` with the inputs it needs (`zips` · `price_max`). Example: ``/wbg-mls:open-house-round` 92101,92103`

</details>


> 📌 **Daily auto-delivery (morning hot sheet to your inbox) is coming
> soon.** Until then, just ask each morning — it takes ten seconds. We will
> never ask you to set up a webhook.

---

## 🗣 Tips for great answers

- **Be specific:** an MLS number ("260016635"), an address, or zips
  ("92102 and 92113") beats "my area."
- **Say the timeframe** you care about ("last 90 days", "this year").
- **Ask for the caveat line** when quoting numbers — every answer carries
  the data window; use it in front of clients and you'll never get caught
  off guard by "where's that from?"
- **Watch for "agent-only" notes** — private remarks and showing
  instructions are for your eyes, and the answers mark them.

---

## 🔐 Your data & privacy

- You sign in with **your own Google work account** — your history and saved
  items belong to you, not the team.
- **MLS-confidential fields** (private remarks, showing instructions) come
  through marked *agent-only* and are never quoted to clients.
- Data comes from the **SDMLS and CRMLS feeds**, refreshed roughly every
  few minutes. Closed-sale history is complete for **SDMLS since Jan 2020**
  and **CRMLS since Jan 2022** — any "all-time" question before that gets an
  honest partial answer, not a guess.

---

## 🧭 Reading the answers

- Answers arrive as **clean tables and short sections** — the shape is the
  same every time for each workflow.
- A line like `[coverage: SDMLS closed from 2020-01]` is the **data
  footprint** — quote it with the number.
- Numbers refresh from the live feeds; a slow first answer (~2s) is the
  connection warming up, everything after is instant.

---

## 🧰 Troubleshooting

| What you see | What to do |
|---|---|
| "Sign in" window keeps reappearing | Sign in with your **work** Google account (approved domains only). Personal Gmail lands in a pending queue — ping an admin. |
| "I don't have access to that tool" | Your account may still be **pending approval** — an admin approves it in the admin console, usually same-day. |
| Marketplace sync failed (Desktop) | Quit fully → off VPN / try hotspot → reopen → re-add the repo. Or use the Terminal one-liner above. |
| Answer says "zero matches in 48h" | That's honest, not broken — nothing new fit the criteria. Widen the zips or budget and ask again. |
| Everything was working yesterday, now errors | The data connection may be restarting — wait 2 minutes and retry. If it persists for 10+ minutes, report it. |

---

## ❓ FAQ

**Does this cost me anything?** No — it's included for WBG agents. It runs
on your existing Claude/ChatGPT plan.

**Is my client data safe?** You're querying the MLS through your own
credentials; nothing you ask is shared with other agents.

**Can I use it on my phone?** The claude.ai connector works in your phone's
browser; the Desktop plugin is for Mac/PC.

**Why does it ask for Google sign-in?** That's how it knows the MLS data is
coming back to *you* — same security as your email.

**Will it email me every morning?** Coming soon. We'll announce it — and
we'll never ask you to paste webhook URLs.

**Who do I call for help?** Post in the team channel, or open the
[troubleshooting guide](https://github.com/nika-loki/wbg-mcp-plugin#-troubleshooting)
above.

---

## 📚 For the tech folks

<details><summary>Technical reference (click to expand)</summary>

- This plugin bundles 14 MCP tools (market_analytics, market_report, comps,
  get_listing, changed_listings, open_houses, agent_production,
  property_context, saved_searches, run_analytics, run_sql, count_rows,
  explore_schema, sync_status) + the seven workflow skills above, with the
  remote server declared in `.mcp.json` (OAuth on first use via the Supabase
  AS; RFC 9728 discovery at origin root).
- Health: `https://mls-mcp-i6dr.onrender.com/health` → `{"ok": true}`.
- Direct API-key installs (Claude Code, Cursor, VS Code, Windsurf) and the
  full internal docs live in the mls repo: `docs/mcp-client-setup.md`.
- Everything here is GENERATED from the playbook registry (`make plugins`
  in the mls repo) — never hand-edit this README.
- Test the plugin: `cd plugins/wbg-mls && claude plugin eval .` (MCP tools are
  mocked; needs Claude Code ≥ 2.1.269).

</details>

---
<sub>Built for The WB Group · Generated 2026-09-19 from the playbook registry · v2026.919.5</sub>
