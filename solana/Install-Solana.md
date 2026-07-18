# Install and Configure Solana

- Installation location: `~/.local/share/solana/install/active_release/bin/solana`
- Key pairs: ` ~/.config/solana/`

1. [Install Solana](https://solana.com/developers/guides/getstarted/setup-local-development)
1. Update the Solana version to match with Mainnet:
   1. `solana cluster-version -um`
   1. `sh -c "$(curl -sSfL https://release.anza.xyz/v2.0.21/install)"`
1. Confirm that Solana version: `solana --version`
1. [Find The Rust version for Mainnet](https://github.com/anza-xyz/agave/blob/v2.0.21/rust-toolchain.toml)
1. [Install the Mainnet Rust version](https://github.com/andreimontchik/public/wiki/rust#install)
1. Generate the Solana keypair: `solana-keygen grind --starts-with amo:1`
1. Update the Solana config to use the generated keypair: `solana config set --keypair /home/andrei/.config/research/amo_keypair.json`
1. Confirm that the Solana config was updated: `solana config get`

# [Build from source](https://github.com/solana-labs/solana?tab=readme-ov-file#building)

- In case if the build fails `linker 'cc' not found` error, [install the missing libraries](Solana-Development-Resources.md#setup-local-dev-env-t).
- In case if build fails with the `linking with 'cc' failed: exit status: 1` error, [limit number of CPU to cut down on memory usage](https://solana.stackexchange.com/questions/9965/solana-cargo-build-error-linking-with-cc-failed-exit-status-1): `cargo build -j 2`

# Uninstall Solana

1. Make sure that the pubkeys are either backed up or not longer needed. They are usually located in the `.config/solana` directory.
1. Delete the ` .config/solana` directory.
1. Delete the `~/.local/share/solana` directory.
1. Remove references to solana directories from the PATH configuration in `.profile` file. Confirm that it is not presented in other dot files: `grep solana ~/.*`.
1. Re-open the SSH session.
