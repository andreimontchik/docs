# Docs
* [Web site](https://v1.orca.so/about)
* [ORCA Docs](https://docs.orca.so/)
* [Developer Portal](https://orca-so.gitbook.io/orca-developer-portal/orca/welcome)
* [ORCA Forums](https://forums.orca.so/)
* [Dev Resources Discord channel](https://discord.com/channels/798712664590254081/1049775881008193716)
* [Uniswap V3 Dev book](https://uniswapv3book.com/index.html)
  * [Liquidity Calculation](https://uniswapv3book.com/milestone_1/calculating-liquidity.html)
  * [Calculation Token Amounts](https://uniswapv3book.com/milestone_1/calculating-liquidity.html#token-amounts-calculation-again)
* [Architecture Overview](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/architecture-overview)
  * [Trading aka Performing Swaps](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/interacting-with-the-protocol/performing-swaps)
* [Fees](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/architecture-overview/understanding-whirlpool-fees)
  * [Trading Fees](https://docs.orca.so/reference/trading-fees)
  * [Pool network fees](https://docs.orca.so/reference/pool-network-fees)
  * [LP rewards table](https://airtable.com/appWk7Z00vzM7snno/shr5kldROuTw036OR/tbltKNeXyG15rabcf/viw9Soj9w6KhHj2Dr)
* Liquidity:
  * [How Tick Array works to maintain Global Liquidity](https://github.com/everlastingsong/solsandbox/blob/main/docs/How_TickArray_works_to_maintain_GlobalLiquidity.pdf)
  * [Discord discussion](https://discord.com/channels/798712664590254081/838660851178274866/1202290932972519425)

# Links
* [Liquidity Pools Web page](https://v1.orca.so/liquidity)
* [Whirlpools list](https://api.mainnet.orca.so/v1/whirlpool/list)
  * [from account microscope](https://everlastingsong.github.io/account-microscope/#/whirlpool/list)
    * [SOL/USDC (8)](https://everlastingsong.github.io/account-microscope/#/whirlpool/whirlpool/7qbRF6YsyGuLUVs6Y1q64bdVrfe4ZcUUz1JRdoVNUJnm)
* [Supported Token List](https://api.mainnet.orca.so/v1/token/list)
* [Supported Wallets](https://docs.orca.so/reference/wallets)
* [WhirlpoolConfig and Program accounts on Devnet and Mainnent](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/interacting-with-the-protocol/orca-whirlpools-parameters)

# Source Code
* [ORCA](https://github.com/orca-so)
  * [Common TypeScript SDK](https://github.com/orca-so/orca-sdks/tree/main/packages/common-sdk)
    * [Math util](https://github.com/orca-so/orca-sdks/blob/main/packages/common-sdk/src/math/math-util.ts)
    * [Decimal util](https://github.com/orca-so/orca-sdks/blob/main/packages/common-sdk/src/math/decimal-util.ts)
  * [Whirlpools TypeScript SDK](https://github.com/orca-so/whirlpools/tree/main/sdk)
    * [Price math](https://github.com/orca-so/whirlpools/blob/main/sdk/src/utils/public/price-math.ts): 
    * [Pool Utils](https://github.com/orca-so/whirlpools/blob/main/sdk/src/utils/public/pool-utils.ts)
    * [Tick Utils](https://github.com/orca-so/whirlpools/blob/main/sdk/src/utils/public/tick-utils.ts) 
  * [Whirlpool Rust](https://github.com/orca-so/whirlpools/tree/main)
    * [The Tick math util](https://github.com/orca-so/whirlpools/tree/main/programs/whirlpool/src/math/tick_math.rs)
    * [Whirlpool Rust CPI](https://github.com/orca-so/whirlpool-cpi)
  * [Account Microscope](https://github.com/everlastingsong/account-microscope)
    * [The Whirlpool page](https://github.com/everlastingsong/account-microscope/blob/main/src/pages/whirlpool/Whirlpool.svelte)
  * [Whirlpool IDL](https://github.com/orca-so/whirlpools/blob/main/sdk/src/artifacts/whirlpool.json)
    * [On-chain IDL](https://explorer.solana.com/address/whirLbMiicVdio4qvUfM5KAg6Ct8VwpYzGff3uctyCc/anchor-program)
    * [Rust structs generated from IDL](https://github.com/orca-so/whirlpools/blob/main/programs/whirlpool/src/lib.rs)
* [ORCA Sandbox](https://github.com/everlastingsong/solsandbox/tree/main)
  * [Example of Rust Whirlpool client](https://github.com/everlastingsong/solsandbox/blob/main/orca/whirlpool/rust_client/get_swap_quote/src/main.rs)
  * [Calculate token amounts from liquidity Rust](https://github.com/everlastingsong/solsandbox/blob/fda653d2f9e6045ee79679a8c0ddc8095155d772/orca/whirlpool/rust_client/with_anchor_client/src/whirlpool_essential/liquidity_math.rs#L11)
  * [Calculate liquidity distribution across the Whirlpool TS](https://github.com/everlastingsong/solsandbox/blob/main/orca/whirlpool/whirlpools_sdk/86d_print_liquidity_distribution_all_with_gpa_with_amount.ts)
  * [Decode Whirlpool transactions TS](https://github.com/everlastingsong/solsandbox/blob/main/orca/whirlpool/whirlpools_sdk/84d_parse_whirlpool_tx_with_decoder.ts)
  * [Utils](https://github.com/everlastingsong/solsandbox/tree/main/orca/whirlpool/rust_client/with_anchor_client/src/whirlpool_essential)
    * [The price math util Rust](https://github.com/everlastingsong/solsandbox/blob/main/orca/whirlpool/rust_client/with_anchor_client/src/whirlpool_essential/price_math.rs)
    * [The Liquidity math util Rust](https://github.com/everlastingsong/solsandbox/blob/main/orca/whirlpool/rust_client/with_anchor_client/src/whirlpool_essential/liquidity_math.rs)
* [The BN JavaScript Library](https://github.com/indutny/bn.js/blob/master/lib/bn.js)

# Dev
* [Devnet Whirlpools](https://everlastingsong.github.io/nebula/)
  * [devUSDC / devUSDT 1](https://explorer.solana.com/address/63cMwvN8eoaD39os9bKP8brmA7Xtov9VxahnPufWCSdg?cluster=devnet)
* Calculations:
  * [price](https://github.com/orca-so/whirlpools/blob/6f7277c2f728be18a09be1b57b0b600579753365/sdk/src/utils/public/price-math.ts#L22) = `(sqrt_x64_price >> 64)^2 * 10^(decimals_a - decimals_b)`
  * [sqrt_price](https://github.com/orca-so/whirlpools/blob/6f7277c2f728be18a09be1b57b0b600579753365/sdk/src/utils/public/price-math.ts#L18) = `(price / 10^(decimals_a - decimals_b)) << 64`
  * [Token amounts](https://github.com/orca-so/whirlpools/blob/3da6b8937f432dcdae75a85a57c59ede5588ebf3/sdk/src/utils/public/pool-utils.ts#L78): 
    * Token A: `(liquidity << 64) * (upper_sqrt_x64_price - lower_sqrt_x64_price) / (upper_sqrt_x64_price * lower_sqrt_x64_price)`
    * Token B: `(liquidity * (upper_sqrt_x64_price - lower_sqrt_x64_price)) >> 64`
  * [Liquidity](https://github.com/orca-so/whirlpools/blob/3da6b8937f432dcdae75a85a57c59ede5588ebf3/sdk/src/utils/public/pool-utils.ts#L135):
  * [Total Fee](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/architecture-overview/understanding-whirlpool-fees#total-fee) = ` swap_amount * ( fee_rate / 1_000_000 )`
   
# [Tools](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/interacting-with-the-protocol/tools)
* [whirlpool-tx-replayer](https://github.com/orca-so/whirlpool-tx-replayer)
* [Account microscope](https://everlastingsong.github.io/account-microscope/)
* [TypeScript Utils](https://orca-so.gitbook.io/orca-developer-portal/whirlpools/interacting-with-the-protocol/basic-usage/important-util-helpers)
