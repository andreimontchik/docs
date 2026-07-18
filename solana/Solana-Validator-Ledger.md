# Docs

- [Snapshots explanation](https://solana.stackexchange.com/questions/1051/what-is-an-exact-definition-of-a-snapshot-on-solana/1064#1064)
- [RocksDB](https://github.com/facebook/rocksdb/wiki)
- Historical Data
  - [Solana BigTable](solana-bigtable)
  - [Triton Old Faithful](https://old-faithful.net/)
  - [Epoch Information](https://api.stakewiz.com/all_epochs_history)
  - [Google Cloud](https://console.cloud.google.com/storage/monitoring?project=mainnet-beta&pli=1)

# Snapshots

## What is Snapshot

Snapshot is a compressed tar archive (.tar.bz2, .tar.gz, .tar.xz or .tar.zst file) containing the following data:

- A dump of Solana accounts (pubkey, owner, SOL balance, data, etc) in the AppendVec file format. This is the same format that the accounts database uses.
- The bank state: Metadata about the implicit state of the chain when the snapshot was taken (network stakes, etc)

Each snapshot targets a specific slot number and uses a cryptographic hash value that uniquely identifies the data stored within the snapshot.
Full vs incremental snapshots

## Snapshot Types

There are further two types of snapshots that differ in the amount of data they store:

1. Full snapshots contain **all accounts at a specific slot**, example: `snapshot-100-D17vR2iksG5RoLMfTX7i5NwSsr4VpbybuX1eqzesQfu2.tar.zst`
1. Incremental snapshots contain **accounts that were changed between specific slots**. Example: `incremental-snapshot-100-200-AvFf9oS8A8U78HdjT9YG2sTTThLHJZmhaMn2g8vkWYnr.tar.zst`

## Uses of snapshots

Solana nodes load snapshots on startup to start syncing at a recent block height instead of having to execute the entire blockchain history from genesis.

Currently validators delete their accounts database and start from a snapshot even if their account data is recent. Naturally nodes automatically generate full and incremental snapshots while they are running to ensure they can start up again.

When a new node joins the network for the first time, it loads a snapshot from a trusted provider (e.g. another node you operate or a slot where the accounts hash has been agreed on by stake supermajority).

Additionally, snapshots are useful for analytics purposes to quickly load a collection of accounts.

# Solana Ledger Tool

## Links

- [Source Code](https://github.com/anza-xyz/agave/tree/master/ledger-tool)

## Install

1. [Increase swap file](../../public/wiki/memory#swap-file).
1. [Increase the memory mapped files limit](../../public/wiki/memory#swap-file).
1. [Install and configure Solana](Install-Solana.md) to install the `solana-ledger-tool`.

# How To

## Manually Download Snapshots from another Validator

[Solana Doc](https://docs.solanalabs.com/operations/best-practices/general#manually-downloading-snapshots)

1. Find the appropriate Validator. Consider using the [Solana](https://docs.solanalabs.com/clusters/available) instances.
1. Find the selected Validator IP address and port: `solana gossip | grep <validator address>`
1. Download Full snapshot: `wget --continue --trust-server-names http://<ip:port>/snapshot.tar.bz2`
   - Mainnet: `wget --continue --trust-server-names http://145.40.93.177:80/snapshot.tar.bz2`
   - Devnet: `wget --continue --trust-server-names http://147.75.55.147:8899/snapshot.tar.bz2`
1. Download incremental snapshot: reuse the same command but add `-incremental` to the archive name. Example: `incremental-snapshot.tar.bz2`.

## Manually download snapshots from third party

- The [Avorio Validator](https://avorio.network/snapshots/):
  ```
  wget --trust-server-names https://snapshots.avorio.network/mainnet-beta/snapshot.tar.bz2; \
  wget --trust-server-names https://snapshots.avorio.network/mainnet-beta/incremental-snapshot.tar.bz2`
  ```
- [Solana Snapshot Finder](https://github.com/c29r3/solana-snapshot-finder)

## Manually download Genesis bin from another Validator

1. Use the same validator servers as for the manual snapshot download.
   - Mainnet: `wget --continue --trust-server-names http://145.40.93.177:8899/genesis.tar.bz2`
   - Devnet: `wget --continue --trust-server-names http://147.75.55.147:8899/genesis.tar.bz2`

## Restore ledger state from snapshot

1. [Download a snapshot](Solana-Validator-Ledger#manually-download-snapshots-from-another-validator)
1. Run solana-ledger-tool command with the following params. It will build the ledger state from full snapshot. If there are incremental snapshots in the `snapshots` directory, the tool will process account updates from them as well.
   ```
   solana-ledger-tool verify \
   --disable-accounts-disk-index \
   --skip-verification \
   --no-os-memory-stats-reporting \
   --force-update-to-open \
   --ledger <ledger directory> \
   --snapshot-archive-path <snapshots directory> \
   --use-snapshot-archives-at-startup always
   ```

## Replay historical transactions

- Docs:
  - [Debugging Consensus Failures](https://github.com/solana-labs/solana/wiki/Debugging-Consensus-Failures)
  - [Restoring Missing Blocks](https://github.com/solana-labs/solana-bigtable#restoring-missing-blocks)

1. Optional for now: Obtain an access to the [Solana Bigtable](Solana-Bigtable).
1. [Access the Solana Bigtable bucket](Solana-Bigtable#access-the-solana-bigtable-bucket).
1. Use the current slot from [Solana Explorer](https://explorer.solana.com/?cluster=mainnet) to search for the most recent epoch archive containing rocksdb.tzr.zst.
1. Download the `rocksdb.tar.zst`. Example `nohup curl -C - -O https://storage.googleapis.com/mainnet-beta-ledger-us-ny5/278201635/rocksdb.tar.zst &`
1. Extract the `rocksdb.tar.zst` archive in the Ledger's `ledger` directory. Example `nohup tar --use-compress-program=unzstd -xvf rocksdb.tar.zst -C /mnt/ledger &` .
1. Download the first `snapshot-xxx.tar.zst` hourly snapshot archive that is within the slot range outlined in the `bounds.txt`file. Example: `curl -O https://storage.googleapis.com/mainnet-beta-ledger-us-ny5/261781166/hourly/snapshot-261835693-EdoRtXVBzbtMszs2vwcmTzFmQ1ACYj5oYPqDifFr7QE3.tar.zst
`
1. Place the downloaded snapshot in the Ledger's `snapshots` directory.
1. Run the [slt_replay.sh](../blob/main/bin/slt_replay.sh) script. It will restore Ledger's bank from the downloaded snapshot and replay shreds from the extracted rocksdb archive files residing in the `ledger` directory.

# CLI

- Current Ledger information: `solana-ledger-tool bounds --ledger <ledger direcotry>`
- Check the specific slot: `solana-ledger-tool -l /mnt/validator/ledger/ slot <slot>`
- Accounts:
  - Check the account balance: `solana balance <ACCOUNT_ADDRESS>`
