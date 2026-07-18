# Docs
* [Home Page](https://www.helius.dev/)
  * Exclusively Solana RPC.
  * Provides with Shared and Dedicated RPCs.
  * Accepts crypto payments.
* [Pricing & Rate Limits](https://docs.helius.dev/welcome/pricing-and-rate-limits)
  * The entry level shared RPC plans is $50/month - 50 requests or 10 transactions per second.

# Links
* [Status Page](https://helius.statuspage.io/#)
* [The Playground app to testdrive RPC calls](https://testdrive.helius.xyz/)

# Dev
* [Source code](https://github.com/helius-labs)
* [Dev Docs](https://docs.helius.dev/)
  * [Sending Transactions](https://docs.helius.dev/solana-rpc-nodes/sending-transactions-on-solana)
    * [Best Practices](https://docs.helius.dev/solana-rpc-nodes/sending-transactions-on-solana#best-practices)
  * [Priority Fee API](https://docs.helius.dev/solana-rpc-nodes/priority-fee-api)
* [SDKs](https://docs.helius.dev/resources/sdks)
  * [Rust SDK](https://github.com/helius-labs/helius-rust-sdk)
  * [Example of sending a transaction in Rust](https://docs.helius.dev/solana-rpc-nodes/sending-transactions-on-solana#rust-sdk)

# CLI
* Check recent priority fees for the `Raydium AMM` program in micro-lamports.
  ```
  curl https://mainnet.helius-rpc.com?api-key=640bbf81-f665-4d01-84a8-180f1438a255 -X POST -H "Content-Type: application/json" -d '
  {
      "jsonrpc": "2.0",
      "id": "1",
      "method": "getPriorityFeeEstimate",
      "params": [{
          "accountKeys": ["675kPX9MHTjS2zt1qfr1NYHuzeLXfQM9H24wFSUt1Mp8"],
          "options": {
              "includeAllPriorityFeeLevels": true
          }
      }]
  }'
  ```
* Get the currently recommended priority fee for the `Raydium APP LP` program in micro-lamports.
  ```
   curl https://mainnet.helius-rpc.com/?api-key=640bbf81-f665-4d01-84a8-180f1438a255 -X POST -H "Content-Type: application/json" -d '
   {
       "jsonrpc": "2.0",
       "id": "1",
       "method": "getPriorityFeeEstimate",
       "params": [{
           "accountKeys": ["675kPX9MHTjS2zt1qfr1NYHuzeLXfQM9H24wFSUt1Mp8"],
           "options": {
               "recommended": true
           }
       }]
   }'
  ```
* [Solana Transactions](../solana/Solana-Transactions.md#cli)