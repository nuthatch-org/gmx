# gmx

A [nuthatch](https://github.com/nightswatchhq/nuthatch) nest: **GMX V1 Vault on Arbitrum**.

The V1 perpetuals vault.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `arbitrum-one`. **1 contract**, **21 tables**.

| alias | address |
|---|---|
| `c0` | `0x489ee077994b6658eafa855c308275ead8097c4a` |

## Verified

Indexed blocks **496,949,922 to 497,246,509** and sealed **10 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Read this before trusting it

- **The subject is dormant.** 10 logs in 300,000 blocks, 164 in 3,000,000. The nest decodes correctly and indexes almost nothing. GMX V2 routes everything through a generic `EventLog`/`EventLog1`/`EventLog2` emitter, which yields opaque encoded blobs rather than typed tables.

## Run it

```sh
nuthatch init --from https://github.com/nightswatchhq/gmx
cd gmx
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"c0__buy_u_s_d_g\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
c0__buy_u_s_d_g
c0__close_position
c0__collect_margin_fees
c0__collect_swap_fees
c0__decrease_guaranteed_usd
c0__decrease_pool_amount
c0__decrease_position
c0__decrease_reserved_amount
c0__decrease_usdg_amount
c0__direct_pool_deposit
c0__increase_guaranteed_usd
c0__increase_pool_amount
c0__increase_position
c0__increase_reserved_amount
c0__increase_usdg_amount
c0__liquidate_position
c0__sell_u_s_d_g
c0__swap
c0__update_funding_rate
c0__update_pnl
c0__update_position
```
