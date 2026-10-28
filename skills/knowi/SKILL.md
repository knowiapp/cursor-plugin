---
name: knowi
description: Answer questions from the user's Knowi data and build Knowi queries, widgets, dashboards, alerts and reports through the Knowi MCP server. Use when the user mentions Knowi, a Knowi dashboard, widget or dataset, Cloud9QL, or asks a business data question while the Knowi server is connected.
---

# Knowi

The Knowi MCP server works on the signed-in user's Knowi account: their datasources, datasets, widgets, dashboards, alerts, reports and documents. Everything you create appears in their Knowi workspace.

## Find before you build

- Use `search` to find dashboards, widgets, datasets, queries, datasources, reports, alerts and documents by name or topic. Take IDs from its results; never guess an ID.
- Use `get_details` for the full definition of one asset once you have its type and ID.
- If the user names something that already exists ("the revenue dashboard"), find it first instead of creating a new one.

## Answer data questions

- `ask` takes a natural-language question, finds the relevant datasets, generates the query and returns rows (500 by default; raise `maxRows` if the user needs more). Pass `datasetId` when you already know which dataset the question is about.
- `get_data` returns the rows and field names of a known widget or dataset. Use it when the user points at a specific asset, or when you need exact field names.
- Report the numbers you got back. If a result looks empty or partial, say so rather than filling the gap.

## Build queries, widgets and dashboards

1. `create_query` runs a query against a datasource and stores the result as a dataset. It runs once unless you pass a refresh schedule.
2. Call `get_data` on that dataset to read its exact field names and types.
3. `create_widget` charts a dataset. `xAxis` and `yAxis` must be exact field names from step 2; a wrong name renders "No Data".
4. For a new dashboard, call `create_dashboard` first, then `create_widget` with its `dashboardId`, then `layout_dashboard` to arrange the widgets.
5. Give the user the URL each tool returns so they can open the result in Knowi.

## Cloud9QL

Cloud9QL is Knowi's query language for transforming dataset results. Use `cloud9ql_assist` to generate, fix, explain, convert or validate it against the dataset's real fields instead of writing it from memory. Reference: https://docs.knowi.com/hc/en-us/articles/115006531408-Cloud9QL-Basics

## Confirm before acting on the user's behalf

Ask the user before calling a tool that changes or sends something they did not explicitly request:

- `delete`, and any `update_*` tool that overwrites an existing asset.
- `run` with a `reportId`, `test_alert`, `create_report` and `create_alert`: these deliver to the configured recipients by email, Slack, Teams or webhook.
- `get_embed_url`: it creates a share link to the data.
