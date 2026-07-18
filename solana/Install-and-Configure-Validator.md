# Docs

- [Setup a Solana Validator](https://docs.solanalabs.com/operations/setup-a-validator)
  - [System Tuning](https://docs.solanalabs.com/operations/setup-a-validator#system-tuning)

# Where is it?

- Validator Configuration, including keypairs: `~/.config/solana`
- Ledger: `/mnt/ledger`
- Snapshots: `/mnt/snapshots`
- Accounts: `/mnt/accounts`
- [Startup configuration parameters source code](https://github.com/solana-labs/solana/blob/master/validator/src/cli.rs)

# Instructions

## [Provision the Server](../Provisioning.md#server)

## Tune up the Server

- Configure the [memory swap](../linux/Memory.md).
- [Increase the memory mapped files limit](../linux/Memory.md)
- [Increase UDP buffers size](../linux/Network.md)
- [Increase number of allowed open file descriptors](../linux/Disk.md#increase-number-of-allowed-open-file-descriptors)
- [Optimize CPU utilization](../linux/CPU.md)
- [Create Disk Mounts](../linux/Disk.md) for Ledger, Accounts and Snapshots.

## Configure [firewall](../linux/Network.md) according to [Solana recomendations](https://docs.solanalabs.com/operations/requirements#optional)

1. Allow TCP/UDP connections for the port range 8000-10000: `sudo ufw allow 8000:10000/tcp; sudo ufw allow 8000:10000/udp`
1. Deny TPC/UDP connections for the port 8899: `sudo ufw deny 8899/tcp; sudo ufw deny 8899/udp`
1. Deny TPC/UDP connections for the port 8900: `sudo ufw deny 8900/tcp; sudo ufw deny 8900/udp`
1. Enable ufw: `sudo ufw enable`
1. Confirm that the configuration was applied: `sudo ufw status`

## [Install Rust](../languages/Rust.md#install)

## [Install Solana](Install-Solana.md)

## Create Validator Keypairs

- the keypairs directory is `~/config/solana`, keep the passphrase empty.
  - Validator Identify: `solana-keygen new -o validator-keypair.devnet.json`
  - Voter Keypair:
  - Authorized Withdrawer:

## Create the Validator startup script

- Known Validators and the endpoints can be found on the [Solana Clusters](https://docs.solanalabs.com/clusters/available) page.
- Example for Mainnet:

```
TBD
```
