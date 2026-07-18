# Docs

- [What is RPC Node](https://docs.solanalabs.com/what-is-an-rpc-node)
- [Stake Weighted QoS](https://solana.com/developers/guides/advanced/stake-weighted-qos)
  - [Helious blog on SWQoS](https://www.helius.dev/blog/stake-weighted-quality-of-service-everything-you-need-to-know)
- [RPC Infra and Providers](https://solana.com/rpc)
- [RPC Methods](https://solana.com/docs/rpc)

# Links

- [RPC Clients](Solana-Development-Resources.md#solana-clients)
- [RPC providers](DeFI#rpc-providers)
- Public Endpoints
  - Mainnet-beta: https://api.mainnet-beta.solana.com
  - Testnet: https://api.testnet.solana.com
  - Devnet: https://api.devnet.solana.com
  - Localnet: http://localhost:8899

# Operate

- [Install and Configure](Install-and-Configure-RPC.md)
- Run: `rm -f nohup.log; nohup ~/src/research/bin/rpc_run.sh &`

## Metrics

- [Solana Grafana Telemetry](https://metrics.solana.com:3000/d/monitor-edge/cluster-telemetry?orgId=1&var-datasource=HsKEnOt4z&var-testnet=mainnet-beta&var-hostid=mr1hDW1GR4ZwQCW8L3p1yfGDd1153rCv4xQUtDewzu6&from=now-1h&to=now)
- [Stakeonomy Validator Dashboard](https://metrics.stakeconomy.com/d/f2b2HcaGz/solana-community-validator-dashboard?orgId=1&refresh=1m&var-pubkey=mr1hDW1GR4ZwQCW8L3p1yfGDd1153rCv4xQUtDewzu6&var-server=&var-inter=1m&var-netif=&var-version=)
- [Validator Metrics](Validator#metrics)
- [Cluster Metrics](Solana-Cluster#metrics)

# How To

- Restart fresh:
  1. Wipe the ledger, accounts and snapshots directories. Use [rpc_wipe.sh](../../research/blob/main/bin/rpc_wipe.sh) as reference.
  1. [Download](solana-Validator-Ledger#manually-download-snapshots-from-third-party) the latest available full and incremental snapshots and place them in the snapshots directory. The directory should have been wiped empty.
  1. Startup RPC. It should restore ledger from the downloaded snapshots and then request and replay the latest shreds to catch up. [The startup sequence](Validator#validator-startup-sequence).
- [Validator How To](Validator#how-to)

# RPC CLI

- [Validator CLI](Validator#cli)
