# Notes

- [Solana Clusters](https://docs.solana.com/clusters)
  - [Mainnet](https://docs.solanalabs.com/clusters/available#mainnet-beta)
  - [Testnet](https://docs.solanalabs.com/clusters/available#testnet)
  - [Devnet](https://docs.solanalabs.com/clusters/available#devnet)

# Metrics

- [Network Status](https://status.solana.com/)
- [Solana Explorer](https://explorer.solana.com/)
  - [Cluster stats](https://explorer.solana.com/?cluster=mainnet)
- [Solana Beach](https://solanabeach.io/)
  - [Blocks](https://solanabeach.io/blocks)
  - [Cluster Valdators](https://solanabeach.io/validators)
- [Solscan](https://solscan.io/)
- [Solana FM](https://solana.fm/?cluster=mainnet-alpha)
- [Solana Compass](https://solanacompass.com/)
- [Shyft Translator to review transactions](https://translator.shyft.to/)
- [Grafana Solana Cluster Telementry](https://metrics.solana.com:3000/d/monitor-edge/cluster-telemetry?orgId=1)
- [Grafana RPC Replay](https://metrics.solana.com:3000/d/KCLhfAbMz/replay?orgId=1&var-datasource=HsKEnOt4z&var-testnet=mainnet-beta&var-hostid=mr1hDW1GR4ZwQCW8L3p1yfGDd1153rCv4xQUtDewzu6&from=now-24h&to=now)
- [Chronograf](Chronograf.md)
- [Validator Metrics](Validator.md#metrics)
- [RPC Node Metrics](RPC-Node.md#metrics)

# CLI

- Check Cluster version: `solana cluster-version -um`
- Get the current epoch info(slot, block etc): `solana epoch-info -um`
- Get the latest transaction fee: `solana fees -um`
- Get the latest [prioritization fees](https://solana.com/docs/rpc/http/getrecentprioritizationfees): `curl https://api.mainnet-beta.solana.com -X POST -H "Content-Type: application/json" -d '{"jsonrpc":"2.0", "id":1, "method": "getRecentPrioritizationFees" }'`
- Get the Cluster Validators: `solana validators --um`. The delinquent stake is at the bottom.
  - Show delinquent validators: `solana validators -um --keep-unstaked-delinquents`
- Get the leader schedule: `solana leader-schedule -um`
- [The Validator CLI](Validator.md#cli)
- [The Ledger CLI](Solana-Validator-Ledger.md#cli)
- [Dev CLI](Solana-Development-Resources.md#cli)
  - [LUTs](Solana-Development-Resources.md#luts)
