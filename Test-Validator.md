# Docs
* [Test Validator Doc](https://docs.solanalabs.com/cli/examples/test-validator)

# Install and  configure
* [Install Rust and Solana CLI](https://docs.solana.com/getstarted/local)
* [Setup Localnet Cluster](https://solana.com/developers/guides/getstarted/setup-local-development#setup-a-localhost-blockchain-cluster)
  * Create new wallet for Localnet: `solana-keygen new --outfile ~/.config/solana/wallet.localnet.json`
  * Configure Solana CLI to work with Localnet cluster: `solana config set --url localhost`
  * Set the new wallet default for Solana CLI: `solana config set -k ~/.config/solana/wallet.localnet.json`
  * Confirm the configuration change: `solana config get`

# Run
1. `cd ~/work`
1. ```
   export RUST_LOG=solana=warn,solana_core=warn,solana_runtime=warn,solana_runtime::message_processor=debug,solana_streamer=warn,solana_poh=warn,solana_gossip=warn,plugin=debug,common=info; solana-test-validator --geyser-plugin-config <PLUGIN_CONFIG_FILE>
   ```
