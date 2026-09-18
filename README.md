# WBG MLS (Claude plugin)

Real-estate market analytics for San Diego County — 14 MCP tools (market
reports, comps, open houses, farm monitoring, agent production boards,
hazard/permit context) plus six agent workflow skills — showing prep, pricing
opinion, hot sheet, buyer matches, open-house round, listing appointment. The MCP server
is bundled (`.mcp.json`): first tool use triggers an OAuth login (Google
sign-in; thewbgroup.com, whisselrealty.com and kylewhissel.com are
auto-approved). All data access is OAuth-gated per user; this repo carries
methodology only, no secrets.

## Install

**Claude Code / Desktop with plugins:** Customize → Plugins → Personal
plugins → **+** → add marketplace from this GitHub repo → Install
**WBG MLS** (v2026.919.1).

**No marketplace? Direct load (works even if marketplace sync fails):**

```bash
claude --plugin-url https://github.com/nika-loki/wbg-mcp-plugin/releases/latest/download/wbg-mls.zip
```

## Use

Skills appear on "/" namespaced as `/wbg-mls:…` — try
`/wbg-mls:showing-prep 260016635` (arguments fill the skill inputs).

## Updates

Artifacts here are GENERATED from the playbook registry in the mls repo
(`make plugins`) — never hand-edit; changes are regenerated and pushed.

## Test

`claude plugin eval .` from this repo's plugins/wbg-mls/ runs the bundled eval
suite (MCP tools are mocked — no live server needed).
