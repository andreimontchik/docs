# Docs
  * [Solana Docs](https://solana.com/docs)
    * [Core Concepts: Accounts, Programs, Transactions](https://solana.com/docs/core/accounts)
    * [Terminology](https://solana.com/docs/terminology)
    * [Solana Program Library](https://spl.solana.com/)
  * [Solana Labs Docs](https://docs.solanalabs.com/)
  * [Medium - Solana Core Tech](https://medium.com/solana-labs/sealevel-parallel-processing-thousands-of-smart-contracts-d814b378192)

# Links
  * [Web Site](https://solana.com/)
  * [Solana Forums](https://forum.solana.com/)
  * [Solana StackExchange](https://solana.stackexchange.com/)
  * [Solana Programs](https://spl.solana.com/)
    * [SFDP](SFDP)
      * [Ecosystem Contributor Priority Queue](https://solana.org/faq#ecosystem_contributor_priority_queue_experimental)
    * [SF Server Program](https://solana.org/server-program)
  * [Staking](Staking)
  * [SolDev: jobs, bounties, grants etc](https://www.soldev.app/)
  * [Solana Releases](https://github.com/solana-labs/solana/releases)
    * [Anza Release Schedule](https://github.com/anza-xyz/agave/wiki/v1.17-Release-Schedule)

# Info
  * [Maximum Transmission Unit a.k.a MTU](https://en.wikipedia.org/wiki/IPv6_packet) size in Solana network is 1_280 bytes. That dictates the [shred](https://solana.com/docs/terminology#shred) size.
  * There are around 600-700 shreds in a [block](https://solana.com/docs/terminology#block).
  * At most one block is being generated per a [slot](https://solana.com/docs/terminology#slot). It is possible to have slots without blocks, meaning the blocks were missed. The usually cause if Leading Validator to be down, delinquent or building blocks off a fork.
  * There are 2 slots per second and 432_000 slots total in an [epoch](https://solana.com/docs/terminology#epoch), meaning the epoch time is around 60 hours.
  * There are 64 [ticks](https://solana.com/docs/terminology#tick) per block. Ticks are coming from the [proof of history a.k.a. PoH](https://solana.com/docs/terminology#proof-of-history-poh) thread. Each tick contains 64_000_000 PoH hashes that can be used for ???.
  * Conversion between [Sol](https://solana.com/docs/terminology#sol), [lamports](https://solana.com/docs/terminology#lamport) and [micro-lamports](https://github.com/solana-labs/solana/blob/ced8f6a512c61e0dd5308095ae8457add4a39e94/program-runtime/src/prioritization_fee.rs#L1-L2):
    * 1 Sol is 1_000_000_000 lamports.
    * 1 lamport is 1_000_000 micro-lamports.
    * 1 Sol is 1_000_000_000_000_000 micro-lamports.
    * 1 lamport is 0.000_000_001 sol.
    * 1 micro-lamport is 0.000_001 lamports.
    * 1 micro-lamport is 0.000_000_000_000_001 Sols.
  * [Transaction Info](solana-transactions#info)

# [Install](install-solana)

# Components
  ## [Cluster](Solana-Cluster)
  ## [Validator](Validator)
  * [Ledger](Solana-Validator-Ledger)
  * [Test Validator](test-validator)
  ## [RPC Node](Rpc-Node)
  ## [Wallet](Solana-Wallet)
  ## [Solana Bigtable](Solana-Bigtable)

# [Dev Resources](Solana-Development-Resources)
  * [SPL Tokens](SPL-Tokens)
  * [On-chain Programs](Solana-On‐Chain-Programs)
  * [Transactions](solana-transactions)
    * [Calculate Transaction Calculate Transaction Fees and Compute Units](Solana-Transactions#calculate-transaction-fees-and-compute-units)

# [How To](solana-how-to)

# [Solana CLI](https://docs.solanalabs.com/cli/usage)
  * Update Solana to the latest version: `solana-install update`
  * Update Solana to specific version: `solana-install init 1.17.22`
  * Review Solana CLI config: `solana config get`
  * Configure Solana CLI to work with specific cluster: `solana config set -[um|ut|ud|ul]`
  * Download the confirmed block: `solana block <slot>`
  * Work with keypairs: `solana-keygen --help`.
  * [Cluster CLI](Solana-Cluster#cli)
  * [Ledger CLI](Solana-Validator-Ledger#cli)
  * [Transactions CLI](Solana-Transactions#cli)
  * [Wallet CLI](Solana-Wallet#cli)
  * [SPL Tokens CLI](SPL-Tokens#spl-tokens-cli)

