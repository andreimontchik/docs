# Docs
* [Setup an RPC Node](https://docs.solanalabs.com/operations/setup-an-rpc-node)
* [Monitoring Best Practices](https://docs.solanalabs.com/operations/best-practices/monitoring)

# Instructions
1. Follow the [Install and Configure Validator](install-and-configure-validator) instructions until the `Create Validator Keys` step.
1. Create RPC kepair in the `~/.keys` directory: `solana-keygen grind --starts-with mr1:1`
1. Update the Solana CLI config to use the RPC key: `solana config set -k ~/.keys/rpc1.json`. This command should also create the `~/.config/sol/cli/config.yml` file, if it was not created before.
1. Confirm that the Solana CLI config was updated: `solana config get`.
1. Create the RPC startup script. Example: [rpc.sh](https://github.com/andreimontchik/research/blob/main/bin/rpc.sh)

## Configure RPC to run as Service
tbd
