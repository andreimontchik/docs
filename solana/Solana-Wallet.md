# Docs
* [Solana Wallet Guide](https://solana.com/docs/intro/wallets)
* [Command Line Wallets](https://docs.solanalabs.com/cli/wallets)
  * [File System Wallets](https://docs.solanalabs.com/cli/wallets/file-system)
* [Send and Receive Tokens](https://docs.solanalabs.com/cli/examples/transfer-tokens)

# CLI
  * Create wallet: `solana-keygen new --outfile <WALLET_KEYPAIR_FILE>`
  * Generate vanity keypair: `solana-keygen grind --starts-with amji:1`
  * Show the wallet pubkey a.k.a address: `solana-keygen pubkey <WALLET_KEYPAIR_FILE>`
  * Verify the wallet address: `solana-keygen verify <PUBKEY> <WALLET_KEYPAIR_FILE>`
  * Check the balance: `solana balance -um <PUBKEY>`
  * Transfer SOL: `solana transfer --from <WALLET_KEYPAIR_FILE> --fee-payer <PAYER_KEYPAIR_FILE> -um <RECIPIENT_ADDRESS> <SOL_AMOUNT>`
  * [SPL Tokens CLI](SPL-Tokens#spl-tokens-cli)