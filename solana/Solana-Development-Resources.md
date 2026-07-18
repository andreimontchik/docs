# Docs

- [Solana Developer Resources](https://solana.com/developers)
- [Solana Cookbook](https://solanacookbook.com/#contributing)
- [Solana StackExchange](https://solana.stackexchange.com/users/9375/andrei-montchik?tab=following)
- [Solana CLI Reference](https://docs.solanalabs.com/cli/usage)
- [Solana RPC Infra and Providers](https://solana.com/rpc)
- [Solana RPC methods](https://solana.com/docs/rpc)
- [Solana Runtime](https://docs.solanalabs.com/validator/runtime)
- [Native Solana Programs](https://docs.solanalabs.com/runtime/programs)
- [Stake-weighted Quality of Service a.k.a SWQoS](https://solana.com/developers/guides/advanced/stake-weighted-qos)
- [SPL Tokens](../SPL-Tokens.md#docs)

# Source code

- [Anza](https://github.com/anza-xyz)
  - [Agave - forked Solana repo](https://github.com/anza-xyz/agave)
- [Old Solana Repos](https://github.com/solana-labs)
- [Solana Developers](https://github.com/solana-developers)
  - [Solana Tools](https://github.com/solana-developers/solana-tools)

# [Setup Local Dev Env-t](https://solana.com/developers/guides/getstarted/setup-local-development#dependencies-for-linux)

1. Install the Linux Dependencies:
   ```
   sudo apt install -y \
   build-essential \
   pkg-config \
   libudev-dev llvm libclang-dev \
   protobuf-compiler libssl-dev
   ```
1. Configure and run [Test Validator](Test-Validator.md)
1. Obtain the localnet wallet pubkey: `solana-keygen pubkey ~/.config/solana/wallet.localnet.json`.
1. Check the new pubkey balance: `solana balance <PUBKEY>`.
1. If needed, airdrop SOL to the localnet wallet pubkey: `solana airdrop 10 <PUBKEY>`.
1. Install and configure [VSCode](../../public/wiki/vscode)

# [Solana Transactions](Solana-Transactions.md)

# [Solana On-Chain Programs](Solana-On‐Chain-Programs.md)

- [Anchor](../Anchor.md)

# [Solana Wallet](Solana-Wallet.md)

# [SPL Tokens](../SPL-Tokens.md)

# Solana Clients

- [JavaScript Web3.js Client](Solana-web3.js-Client.md)
- [RPC Client](https://solana.com/docs/rpc)
  - [RPC HTTP Methods](https://solana.com/docs/rpc/http)
    - [Rust direct RPC HTTP calls tests and usage examples](https://github.com/anza-xyz/agave/blob/master/rpc-test/tests/rpc.rs#L58)
  - [Rust RPC Client](https://solana.com/docs/clients/rust)
    - [Source Code](https://github.com/anza-xyz/agave/blob/b9dd0cc6774755a56475a6910acabecad10a3c33/rpc-client/src/rpc_client.rs#L116)
- [Quic Client](https://github.com/anza-xyz/agave/tree/master/quic-client)
- [TPU Client](https://github.com/anza-xyz/agave/tree/master/tpu-client)
  - [Send transactions to Leader directly](https://docs.rs/solana-client/latest/solana_client/tpu_client/index.html)
- [Banks Client](https://github.com/anza-xyz/agave/blob/master/banks-client/src/lib.rs)

# [Geyser Plugin](Geyser-Plugin.md)

# CLI

## LUTs

1. Create LUT:
   ```solana address-lookup-table create \
   --authority <AUTHORITY KEYPAIR> \
   --payer <PAYER KEYPAIR>
   ```
1. Fund LUT with 0.01 SOL to cover the rent-exemption.
1. Add Addresses to newly created LUT:
   ```
   solana address-lookup-table extend <LUT ADDRESS> \
   --addresses <ADDRESS1>,<ADDRESS2> \
   --authority <AUTHORITY KEYPAIR> \
   --payer <PAYER KEYPAIR>
   ```
