# Links

- [WebSite](https://www.anchor-lang.com/)
- [Anchor Book](https://book.anchor-lang.com/introduction/introduction.html)
- [Source Code](https://github.com/coral-xyz/anchor)

# Dev Resources

- [API](https://docs.rs/anchor-lang/latest/anchor_lang/index.html)
  - [Account Types Reference](https://docs.rs/anchor-lang/latest/anchor_lang/accounts/index.html)
  - [Accounts Reference](https://docs.rs/anchor-lang/latest/anchor_lang/accounts/account/struct.Account.html)
  - [Constraints Reference](https://docs.rs/anchor-lang/latest/anchor_lang/derive.Accounts.html#constraints)
  - Errors
    - [Rust Errors Reference](https://docs.rs/anchor-lang/latest/anchor_lang/error/struct.AnchorError.html)
    - [TypeScript Errors Reference](https://docs.rs/anchor-lang/latest/anchor_lang/error/struct.AnchorError.html)
  - [CPI](https://www.anchor-lang.com/docs/cross-program-invocations)
- [Sealevel Attacks and Mitigation examples](https://github.com/coral-xyz/sealevel-attacks/tree/master)
  - [Initialization](https://github.com/coral-xyz/sealevel-attacks/tree/master/programs/4-initialization)
- Anchor Clients
  - [Anchor Rust Client](https://docs.rs/anchor-client/latest/anchor_client/)
  - [Anchor TypeScript Client](https://coral-xyz.github.io/anchor/ts/index.html)
- [Anchor Types JavaScript](https://www.anchor-lang.com/docs/javascript-anchor-types)

# References

- [JavaScript BN library](https://github.com/indutny/bn.js/)

# [Installation](https://www.anchor-lang.com/docs/installation)

1. [Install Rust](../languages/Rust.md#install)
1. [Install Solana](Install-Solana.md)
1. Install Yarn, follow the [Solana Web3.js Client installation](Solana-web3.js-Client.md#installation) steps.
1. Install [Anchor Version Manager](https://www.anchor-lang.com/docs/avm) a.k.a. AVM: `cargo install --git https://github.com/coral-xyz/anchor avm --locked --force`.
   - Install additional dependencies in case if the AVM install fails: `sudo apt-get update && sudo apt-get upgrade && sudo apt-get install -y pkg-config build-essential libudev-dev libssl-dev`.
1. Confirm that AVM is installed successfully: `avm --version`.
1. Install Anchor:
   - the latest version: `avm install latest; avm use latest`.
   - or the specific version: `avm install 0.29.0; avm use 0.29.0`.

# [CLI](https://www.anchor-lang.com/docs/cli)
