# Docs

- [The DeFI concepts and participants Guide](https://calblockchain.mirror.xyz/c56CHOu-Wow_50qPp2Wlg0rhUvdz1HLbGSUWlB_KX9o)
- [What is DeFI](https://www.coindesk.com/learn/what-is-defi/)
- [MEV Explanation from Ethereum](https://ethereum.org/en/developers/docs/mev/)
- [What is AMM](https://www.coindesk.com/learn/what-is-an-automated-market-maker/)
- [What is CLMM](https://docs.raydium.io/raydium/~/changes/RaVY5reeE9b0iaInst59/liquidity-providers/providing-concentrated-liquidity-clmm/intro-on-concentrated-liquidity)
  - [Uniswap v3](https://blog.uniswap.org/uniswap-v3)
- [What is Yield Farming](https://www.gemini.com/cryptopedia/what-is-yield-farming-crypto-defi-liquidity-mining#section-what-is-yield-farming)
- [What is MEV](https://ethereum.org/en/developers/docs/mev)
- [What is Flashbot](https://academy.binance.com/en/glossary/flashbots)
- [Crypto Arbitrage Trading](https://www.coindesk.com/learn/crypto-arbitrage-trading-how-to-make-low-risk-gains/)

# Crypto News & Data

- [CoinMarketCap](https://coinmarketcap.com/)
- [CoinGecko](https://www.coingecko.com/)

# Wallets

- [Solflare](https://solflare.com/)
  - Solana native.
- Torus
- WalletConnect
  - A protocol for wallet connectivity.
- [Phantom](https://phantom.app/)
  - Not supported by Raydium by default

# Liquidity Providers

- [ORCA](defi/Orca.md)
- [Raydium](defi/Raydium.md)
- [Jupiter](defi/Jupiter.md)
- [Saber](https://app.saber.so/)
  - Mostly stable coins and bridged assets.
  - [Docs](https://docs.saber.so/)
  - [Rust SDK](https://docs.saber.so/developing/sdks/stable-swap#rust-crates)

# DEX Order Books

- [Serum](https://docs.projectserum.com/introduction/overview)
- [Open Book](https://github.com/openbook-dex)

# Lenders

- [marginfi](https://www.marginfi.com/)
  - [Rust CLI](https://github.com/mrgnlabs/marginfi-v2/tree/main/clients/rust/marginfi-cli)

# RPC Providers

- [Helius](defi/Helious.md)
- [Triton](https://triton.one/)
  - Support multiple blockchains.
  - Claim to land a transaction within 400ms.
  - They accept payments with USDC on Solana.
  - Offer shared pools and dedicated nodes.
    - Advise to use dedicated nodes for algo trading.
  - [Pricing](https://triton.one/triton-rpc/#pricing-section)
    - Starting from $500/month for front end only and $2000/month min for algo trading.
- [QuickNode](https://www.quicknode.com)
  - Support multiple blockchains.
  - Have the free starter plan.
  - [Offer MEV protection](https://marketplace.quicknode.com/add-on/merkle-2)
  - Offers the $50/month plan for 10 RPC request per second, 10M requests per month and 500M API credits.
    - Requires 50 API credits for sending transactions.
- [Alchemy](https://www.alchemy.com)
  - Multichain.
  - [Pricing](https://www.alchemy.com/pricing)
  - Offers the $50/month plan that looks suitable.
  - The support of [Solana API](https://docs.alchemy.com/reference/solana-api-quickstart) looks straightforward.
    - Do not see CU price support.
- [BlockDaemon](https://www.blockdaemon.com/get-started/nodes)
- [HelloMoon](https://www.hellomoon.io/developers)
- [Shyft](https://docs.shyft.to/solana-rpcs-das-api/shyft-rpcs)
  - allows to [query Solana accounts](https://docs.shyft.to/solana-indexers/case-studies/orca-whirlpool) by using GraphQL, like [Hasura](https://hasura.io/)
  - has the [Translator](https://translator.shyft.to/) tool that allows to review LP swaps
- [Syndica](https://syndica.io/)

# Market data

- [Birdeye - trading activity and stats](https://birdeye.so/?chain=solana)
- [Arcana - market activity](https://app.arcana.markets/)

# Tools

- [Impermanent Loss Calculator](https://dailydefi.org/tools/impermanent-loss-calculator/)
- [Shyft Translator](https://translator.shyft.to/) to review LP swaps information.
