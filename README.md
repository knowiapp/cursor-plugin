# Knowi plugin for Cursor

Query, visualize, and act on your [Knowi](https://www.knowi.com) data without leaving Cursor. The plugin connects Cursor's agent to the Knowi MCP server and adds a skill that teaches it how to use Knowi well.

With it, the agent can:

- Answer data questions in plain English from your datasets ("What were signups by region last month?").
- Find dashboards, widgets, datasets, queries, reports and alerts by name.
- Create queries, widgets and dashboards, and lay dashboards out.
- Write, fix and validate Cloud9QL against your dataset's real fields.
- Create and manage alerts and reports, and export data as CSV or PDF.

## Install

1. In Cursor, open **Customize**, search for **Knowi**, and select **Install**.
2. The first time the agent uses a Knowi tool, Cursor asks you to sign in. Sign in with your Knowi account and approve access.

The plugin acts as you: it sees and changes only what your Knowi account can.

### EU Cloud and on-premise

The plugin points at Knowi's US cloud (`https://www.knowi.com/api/2.0/mcp`). On Knowi EU Cloud, use `https://eu.knowi.com/api/2.0/mcp` instead; on an on-premise install, use `https://<your-knowi-host>/api/2.0/mcp`. Add it in Cursor's MCP settings in place of the plugin's server.

## Try it

- "Which Knowi dashboards do we have about revenue?"
- "What were total orders last quarter, by region?"
- "Build a dashboard of weekly signups and churn from the Customers dataset."
- "Write Cloud9QL that groups the Orders dataset by month and sums revenue."
- "Alert me when daily signups drop below 50."

## What's in this plugin

| Path | Purpose |
|---|---|
| `mcp.json` | Connects to the Knowi MCP server. |
| `skills/knowi/SKILL.md` | How the agent should find assets, answer questions, build dashboards and when to confirm with you. |
| `.cursor-plugin/plugin.json` | Cursor plugin manifest. |
| `plugin.json` | [Agent Plugins](https://agent-plugins.org) manifest for other compatible tools. |

## Links

- MCP server docs: https://docs.knowi.com/hc/en-us/articles/50397548438931-MCP-Server
- Cloud9QL reference: https://docs.knowi.com/hc/en-us/articles/115006531408-Cloud9QL-Basics
- Privacy policy: https://www.knowi.com/privacy
- Terms: https://www.knowi.com/terms
- Support: support@knowi.com

## License

[MIT](LICENSE)
