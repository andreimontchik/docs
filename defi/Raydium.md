# Docs
* [Website](https://raydium.io/)
* [Docs](https://docs.raydium.io/raydium/)
  * [Info for Devs](https://docs.raydium.io/raydium/protocol/developers)
  * [The Raydium protocol](https://docs.raydium.io/raydium/protocol/untitled-1)
    * [Protocol Fees](https://docs.raydium.io/raydium/protocol/protocol-fees)
* [Explanation of AMM and CLMM](https://github.com/raydium-io/raydium-docs/tree/master/dev-resources)

# Links
* [Supported Wallets](https://docs.raydium.io/raydium/getting-started/spl-wallets)
* [On-chain Addresses](https://docs.raydium.io/raydium/~/changes/RaVY5reeE9b0iaInst59/protocol/developers/addresses)
* [Web API](https://docs.raydium.io/raydium/protocol/developers/apis)
  * [API v3](https://api-v3.raydium.io/docs/#/)
  * [Token List](https://api.raydium.io/v2/sdk/token/raydium.mainnet.json)
  * [Supported pairs for AMM pools, contains volumes](https://api.raydium.io/v2/main/pairs)
  * [AMM pools configuration](https://api.raydium.io/v2/sdk/liquidity/mainnet.json)
  * [CLMM (AMM v3) pools](https://api.raydium.io/v2/ammV3/ammPools)

# Source Code
* [GitHub repo](https://github.com/orgs/raydium-io/repositories?type=all)
* [SDK on TS](https://github.com/raydium-io/raydium-sdk)
  * [SDK Demos on TS](https://github.com/raydium-io/raydium-sdk-V1-demo/tree/master/src)
* [AMM on Rust](https://github.com/raydium-io/raydium-amm/tree/master)
* [Updated AMM program](https://github.com/raydium-io/raydium-cp-swap)
* [CLMM Client in Rust](https://github.com/raydium-io/raydium-clmm/blob/master/client/src/main.rs)

# Dev
* AMM
  * [IDL](https://github.com/raydium-io/raydium-idl/blob/master/raydium_amm/idl.json)
    * Instructions are outdated! but it seems AMM accounts are still Ok.
    * The AMM pool account type name is [AmmInfo](https://github.com/raydium-io/raydium-idl/blob/ebf065933508ed0736992489a1aab421b7173b1f/raydium_amm/idl.json#L1637)
      * **token_coin** - base token AMM vault
      * **token_pc** - quote (particular coin) token AMM vault
      * **lp_mint** - Raydium specific LP token mint, like Raydium LP Token SOL-USDC
      * **lp_amount** - LP token amount
  * [Calculations](https://docs.raydium.io/raydium/protocol/untitled-1#the-raydium-protocol-an-ecosystem-sustaining-amm)
    * base_token_amount = `(raydium_amm_interface::AmmInfo.token_coin -> spl_token::state::Account.amount) / 10^AmmInfo.coin_decimals`
    * quote_token_amount = `(raydium_amm_interface::AmmInfo.token_pc -> spl_token::state::Account.amount) / 10^AmmInfo.pc_decimals`
    * qoute_token_amount_to_buy_from_amm = `quote_token_amount * base_token_amount / (base_token_amount - base_token_amount_to_buy) - quote_token_amount`
    * quote_token_fee_to_buy_from_amm = `qoute_token_amount_to_buy_from_amm / 1 - fee_ratio`
    * base_token_fee_for_selling_to_amm = `base_token_amount_to_sell * (1 - fee_ratio)`
    * quote_token_amount_for_selling_to_amm = `quote_token_amount - (quote_token_amount * base_token_amount / (base_token_amount + base_token_amount_to_sell - base_token_fee_for_selling_to_amm))`
    * [swap fee](https://github.com/raydium-io/raydium-amm/blob/18bed23de5a29b038a93db493fafd5ff4ee5386b/program/src/processor.rs#L2414) = `AmmInfo.Fees.swap_fee_numerator / AmmInfo.Fees.swap_fee_denominator`
  * [Instructions](https://github.com/raydium-io/raydium-amm/blob/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e/program/src/instruction.rs)
    * [Buy Base token aka swap_base_out](https://github.com/raydium-io/raydium-amm/blob/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e/program/src/instruction.rs#L1064)
    * [Sell Base token aka swap_base_in](https://github.com/raydium-io/raydium-amm/blob/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e/program/src/instruction.rs#L1064)
    * [Accounts info for swap instruction](https://github.com/raydium-io/raydium-amm/blob/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e/program/src/instruction.rs#L331)
    * [The Rust library with util to help with swaps etc. Outdated! Uses Solana <1.17](https://github.com/raydium-io/raydium-library/blob/master/libraries/src/amm/instructions.rs#L117)
  * [Program](https://github.com/raydium-io/raydium-amm/tree/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e)
    * [Entry point](https://github.com/raydium-io/raydium-amm/blob/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e/program/src/entrypoint.rs#L12)
    * [Process Swap](https://github.com/raydium-io/raydium-amm/blob/ae039d21cd49ef670d76b3a1cf5485ae0213dc5e/program/src/processor.rs#L2191)

* CLMM
  * IDL
    * [On chain for the CLMM Program](https://explorer.solana.com/address/CAMMCzo5YL8w4VFF8KVHrK22GGUsp5VTaW7grrKgrWqK/anchor-program?cluster=mainnet)
    * [In Git](https://github.com/raydium-io/raydium-idl/blob/master/raydium_clmm/amm_v3.json)
    * The CLMM pool account type name is [PoolState](https://github.com/raydium-io/raydium-idl/blob/ebf065933508ed0736992489a1aab421b7173b1f/raydium_clmm/amm_v3.json#L2491)

# Tools
* [Hasura GraphQL endpoint for Shyft API](https://cloud.hasura.io/public/graphiql?endpoint=+https%3A%2F%2Fprograms.shyft.to%2Fv0%2Fgraphql%2F%3Fapi_key%3DPjnsMufcmuJVt3E9)
  * [Usage example](https://docs.shyft.to/solana-indexers/case-studies/raydium)
