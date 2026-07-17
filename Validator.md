# Docs
* [Solana Validator Documentation](https://docs.solanalabs.com/)
  * [Monitoring Best Practices](https://docs.solanalabs.com/operations/best-practices/monitoring)
* [Validator Educational Workshops on YouTube](https://www.youtube.com/playlist?list=PLilwLeBwGuK6jKrmn7KOkxRxS9tvbRa5p)
* [How to become a Validator on Solana](https://medium.com/@Cogent_Crypto/how-to-become-a-validator-on-solana-9dc4288107b7)
* [Solana Staking Rewards & Validator Economics](https://laine-sa.medium.com/solana-staking-rewards-validator-economics-how-does-it-work-6718e4cccc4e)

# Links
* [Validator Profit Calculator](https://cogentcrypto.io/ValidatorProfitCalculator)
* [Validator Profit Estimator](https://docs.google.com/spreadsheets/d/1HPU_uG3iJ_ns27CItdWGllW0c-Pn07J0_LEDZs1otQY/edit#gid=0)

# Notes
* [Anatomy of a Validator](https://docs.solanalabs.com/validator/anatomy)
  * [TPU](https://docs.solanalabs.com/validator/tpu)
  * [Runtime - transaction processing](https://docs.solanalabs.com/validator/runtime)
* [Economics of running Validator](https://docs.solanalabs.com/operations/validator-or-rpc-node#economics-of-running-a-consensus-validator)
  * Validator earns 1 vote credit per slot that became rooted. The vote credit rewards are calculated in the end of epoch and earn percentage of inflation proportional it the Validator's percentage of total stake.
  * According to [Validator Calculator](https://cogentcrypto.io/ValidatorProfitCalculator) just running a voting Validator with the $110 SOL price will cost __$3,600__ a month. The break even point is  __80,000 SOL__ stake with 5% commission.
* The "Costs" section of the [How to become a Validator on Solana](https://medium.com/@Cogent_Crypto/how-to-become-a-validator-on-solana-9dc4288107b7) explains what it takes to run Validator.
* [Validator version on Mainnet](https://solanabeach.io/validators)
* [Transition identity from primary to backup Validator](https://pumpkins-pool.gitbook.io/pumpkins-pool/)
* [Operating a Validator](https://docs.solanalabs.com/operations/)
   * [Validator Monitoring](https://docs.solanalabs.com/operations/best-practices/monitoring)

# Components
## [Ledger](Solana-Validator-Ledger)
   * [Solana Ledger Tool](Solana-Validator-Ledger#solana-ledger-tool)
## [Geyser Plugin](Geyser-Plugin)
## [Test Validator](test-validator)

# Operate
## [Install and Configure](install-and-configure-validator)
  
## Run
1. `cd ~`
1. `rm -f logs/validator.log; rm -f nohup.out; nohup ./bin/validator.sh &`
   
### Validator Startup Sequence
1. Download the latest full snapshot.
1. Download the latest incremental snapshot.
1. Rebuild the storages from downloaded snapshots.
1. Rebuild the bank from snapshot storages and generate account indexes.
1. Clean up accounts cache and verify the bank.
1. Flush generated indexes to either in-memory or disk location, depending of the configuration.
1. Start requesting and replaying shreds from other validators until it catches up.
1. Start replaying the Leader generated blocks realtime.

## Metrics
* [Validator Leaderboard](https://cogentcrypto.io/Validators#apy_estimate_desc)
* [Stakeview - Validator Performance Ranking](https://stakeview.app/)
  * [Good Performers](https://stakeview.app/good.html)
  * [Poor Performers](https://stakeview.app/poor.html)
  * [Stake Distribution](https://stakeview.app/stakes)
* [Validators.app - Validator metrics](https://www.validators.app/)
  * [Validator Concentration](https://www.validators.app/data-centers?locale=en&network=mainnet&sort_by=data_center)
* [Stakeonomy Solana Monitoring Tool](https://github.com/stakeconomy/solanamonitoring?tab=readme-ov-file)
* [RPC Node Metrics](RPC-Node#metrics)
* [Cluster Metrics](Solana-Cluster#metrics)

# How To
* Tweak Validator logging: `solana-validator --ledger <LEDGER_DIR> set-log-filter "solana=<LOG_LEVEL>"`. Example: [rpc_adjust_logging.sh](../../research/bin/rpc_adjust_log.sh)
* [Ledger How To](solana-Validator-Ledger#how-to)
  * [Manually Download snapshots from third party](solana-Validator-Ledger#manually-download-snapshots-from-third-party)

# CLI
* Check the Validator startup replay status: `solana catchup -um <IDENTITY_KEY>`
* Monitor Validator: `solana-validator --ledger <LEDGER_DIR> monitor`
* Check if the Validator participating in Gossip: `solana gossip -um | grep <IDENTITY_KEY>` 
* Check if the Validator in the Solana Validators list: `solana validators -um | grep <IDENTITY_KEY>`
* Gracefully stop the Validator: `solana-validator --ledger <LEDGER_DIR> exit --monitor --skip-new-snapshot-check`
* Review the Validator log: 
  * Startup parameters: `grep -B1 -A61 "Starting validator with" <VALIDATOR_LOG>`
  * Creation of snapshot directory: `egrep "Creating bank snapshot for slot | bank serialize took" <VALIDATOR_LOG>`
  * Creation of snapshot archive, either full of incremental: `egrep "Generating snapshot archive for slot | Successfully created" <VALIDATOR_LOG>` 
* [RPC CLI](RPC-Node#rpc-cli)
* [The Ledger CLI](Solana-Validator-Ledger#cli)
* [The Cluster CLI](Solana-Cluster#cli)