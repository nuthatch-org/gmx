---
name: nuthatch
description: Query this self-hosted nuthatch nest on arbitrum-one - decoded events, balances, and read-only SQL. Use when asked about on-chain activity for these contracts.
---

# Querying the nuthatch nest

Contracts indexed on arbitrum-one:
- `c0` = 0x489ee077994b6658eafa855c308275ead8097c4a

Data is local - never call an external API for it.

## Preferred: MCP
If a `nuthatch` MCP server is configured, use its tools. Call `schema` first to learn the
data model, then `sql` / `entity` / `balance` / `top_balances`.

## Fallback: HTTP (a `nuthatch dev` must be running)
- Recent rows:  `curl localhost:8288/entities?limit=20`
- Read-only SQL: `curl -G localhost:8288/sql --data-urlencode 'q=SELECT count(*) FROM transfers'`

`sql` sees finalized data only; balances/entity cover the live tip.
