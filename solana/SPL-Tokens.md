# Docs
* [Tokens on Solana](https://solana.com/docs/core/tokens)
  * [Token Account](https://solana.com/docs/core/tokens#token-account)
* [SPL Token Program](https://spl.solana.com/)

# Links
* [SPL Source Code](https://github.com/solana-program/)
  * [SPL Token Account](https://github.com/solana-program/token/blob/main/interface/src/state.rs#L87)
  * [SPL Mint Account](https://github.com/solana-program/token/blob/main/interface/src/state.rs#L16)
* [Old SPL Rust Examples](https://github.com/solana-labs/solana-program-library/tree/master/examples/rust)
  * [Old Create and submit transaction](https://github.com/solana-labs/solana-program-library/blob/48499ec0bd621afd11d4321c9430f62dcf6fd973/examples/rust/transfer-tokens/tests/functional.rs#L17)
  * [Old Transfer Tokens](https://github.com/solana-labs/solana-program-library/blob/master/examples/rust/transfer-tokens/tests/functional.rs#L17)

# [SPL Tokens CLI](https://docs.solanalabs.com/cli)
  * [Example of creating, minting and transferring SPL token by using CLI](https://solana.com/docs/core/tokens#token-examples)
* Review Token accounts: `spl-token accounts -um --owner <WALLET_ADDRESS>`
* Create new Token account: `spl-token create-account -um <TOKEN_MINT_ADDRESS> <WALLET_KEYPAIR>`
* Transfer Tokens: `spl-token transfer -um --owner <SENDER_WALLET_KEYPAIR> --from <SENDER_TOKEN_ACCOUNT> <TOKEN_MINT_ADDRESS> <TOKEN_AMOUNT> <RECIPIENT_WALLET_ADDRESS or RECIPIENT_TOKEN_ACCOUNT>`
* Wrap Tokens: `spl-token wrap -um --fee-payer <WALLET_KEYPAIR> <AMOUNT> -- <WALLET_KEYPAIR>`
* Unwrap Tokens: `spl-token unwrap -um --owner <WALLET_KEYPAIR>`
* [Solana Wallet CLI](Solana-Wallet)
