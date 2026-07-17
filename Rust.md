# Docs
* [The Book](https://doc.rust-lang.org/book/title-page.html)
* [Rust Reference](https://doc.rust-lang.org/reference/introduction.html)
* [Rust by Example](https://doc.rust-lang.org/rust-by-example/index.html)
* [The Rustonomicon - the Dark Arts of Unsafe Rust](https://doc.rust-lang.org/nomicon/intro.html)
* [The Little Book of Rust Macros](https://veykril.github.io/tlborm/introduction.html)
* [Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021)

# How To

## [Install](https://www.rust-lang.org/tools/install) 
* Install the Rust toolchain installer __Rustup__: `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
* Show the current Rust version: `rustc --version`
* Review the installed toochains: `rustup show`
* Install different toolchains:
  * Stable version: `rustup toolchain install stable`
  * Specific version: `rustup toolchain install <version>`
  * Nightly version: `rustup toolchain install nightly`
* Setup the default toolchain version: `rustup default <version>`
* Confirm the toolchain version: `rustup --version`

## Review installed Cargo bins 
* `cargo install --list`

## Build
* Run `cargo build`
* [To avoid CPU targeting optimization compiler flags](https://discord.com/channels/428295358100013066/560174212967432193/1172575251289342023)
* Show dependencies: `cargo tree`

## Format    
1. [Configure formatting in the `rustfmt.toml`](vscode#support-rust)
1. Run `cargo +nightly fmt --all`

## [Test](https://doc.rust-lang.org/book/ch11-00-testing.html)
* Run in single thread: `cargo test -- --test-threads=1`
* Show system out: `cargo test -- --show-output`

## Clean
### Compiled binaries
* Manual: rm -r `target`.
### Cargo Cache
* Using cargo: `cargo clean`.
* Manual: `rm -r ~/.cargo/registry/cache`.

## Uninstall
1. Run `rustup self uninstall`.
1. Remove the  `~/.cargo` directory, if exists.
1. Remove the RUSTUP_HOME or CARGO_HOME setting from dot files, if any.
1. Re-logon.

## Review coredumps
* Refer to Validator -> Where is it? -> Core dumps for the core dump config 
* the binary location is  `target/debug` 

# Third Party libraries
## [Cadence - Statsd client](https://docs.rs/cadence/latest/cadence/)
* [GitHub Repo](https://github.com/56quarters/cadence)
* [API](https://docs.rs/cadence/1.4.0/cadence/all.html)