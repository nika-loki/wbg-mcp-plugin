# WBG MLS (Claude plugin)

Real-estate market analytics for San Diego County — 14 MCP tools (market
reports, comps, open houses, farm monitoring, agent production boards,
hazard/permit context) plus the four classic workflow skills. All data access
is OAuth-gated per user; this repo carries methodology only, no secrets.

## Install (one-time)

1. Claude Desktop → Customize → Plugins → Personal plugins → **+**
2. Add marketplace from this GitHub repo (`wbg-internal`)
3. Install **WBG MLS** (v2026.9.18)
4. Connect the data plane (one paste, already a working flow): Claude Desktop →
   Settings → Connectors → Add custom connector →
   `https://mls-mcp-i6dr.onrender.com/mcp` → sign in with Google → Allow.

## Use

Skills appear on "/" — try `/showing-prep <MLS number>`. First tool use
triggers the OAuth login (Google sign-in; thewbgroup.com, whisselrealty.com
and kylewhissel.com domains are auto-approved).

## Updates

Artifacts here are GENERATED from the playbook registry in the mls repo
(`make plugins`) — never hand-edit; changes are regenerated and pushed.
