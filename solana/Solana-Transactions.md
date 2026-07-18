# [Docs](https://solana.com/docs/core/transactions)

- [The transaction flow](https://solana.com/docs/core/transactions/retry#the-journey-of-a-transaction)
- [The transaction processing JITO blog](https://www.jito.wtf/blog/solana-validator-101-transaction-processing/)
- [Transaction Fees](https://solana.com/docs/intro/transaction_fees)
  - [More on transaction Fees](https://solana.com/docs/core/transactions/fees)
- [Compute Budget](https://solana.com/docs/core/runtime#compute-budget)
  - [How to Request Optimal Compute Budget](https://solana.com/developers/guides/advanced/how-to-request-optimal-compute)
  - [How to Optimize Compute Usage](https://solana.com/developers/guides/advanced/how-to-optimize-compute)
  - [Compute Budget Source Code](https://github.com/solana-labs/solana/blob/090e11210aa7222d8295610a6ccac4acda711bb9/program-runtime/src/compute_budget.rs#L26-L87)
  - [How to Use Priority Fees](https://solana.com/developers/guides/advanced/how-to-use-priority-fees)

# Info

- The [maximum size of a transaction](https://solana.com/docs/core/transactions#transaction-size) is 1232 bytes.
- A transaction signature size is 64 bytes. Max number of signatures is 19.
- An account size is 32 bytes. Max number of accounts is 35.
- Max age of a transaction is 150 blocks.

# Calculate [Transaction Fees](https://solana.com/docs/core/fees#transaction-fees) and Compute Units

- The static _Transaction Fee_ is 5_000 lamports (0.000_005 SOL) per a signature. That would be the only fee paid in case if the Prioritization Fee is not set.
- The [Transaction Prioritization Fee](https://solana.com/docs/core/fees#prioritization-fees-2) is measured in [Compute Units](https://solana.com/docs/terminology#compute-units) per instruction.
  - The CU limit is set for a transaction. If not set, the [Default CU limit](https://github.com/solana-labs/solana/blob/4293f11cf13fc1e83f1baa2ca3bb2f8ea8f9a000/program-runtime/src/compute_budget.rs#L13) is 200_000 per instruction.
  - Set CU limit, not actual number of consumed CUs, will be used to calculate [Prioritization Fee](https://solana.com/docs/core/fees#prioritization-fee).
  - CUs price is measured in micro-lamports (0.000_001 lamports).
- Setting CU price enables the Prioritization fee calculation, which is a product of CU limit and CU price.
- The [simulateTransaction](https://solana.com/docs/rpc/http/simulatetransaction) RPC call return number of required CUs.
- The [getSimulationComputeUnits](https://github.com/solana-developers/helpers?tab=readme-ov-file#get-simulated-compute-units-cus-for-transaction-instructions) does pretty much the same. It requires intalling the `solana-developers/helpers` NodeJS module though.
- The [getFeeForMessage](https://solana.com/docs/rpc/http/getfeeformessage) PRC method returns the message fees in lamports.
- Formula: FEE_SOL=<CU_LIMIT> \* <CU_PRICE> / 1_000_000_000_000_000 + 5_000 / 1_000_000_000

# CLI

- Transfer Tokens: `solana transfer --from <KEYPAIR> <RECIPIENT_ACCOUNT_ADDRESS> <AMOUNT> --fee-payer <KEYPAIR>`
- Check the transaction status: `solana confirm <TRANSACTION_SIGNATURE>`
- [Check out the latest prioritization fees](https://solana.com/docs/rpc/http/getrecentprioritizationfees):
  ```
  curl https://api.mainnet-beta.solana.com -X POST -H "Content-Type: application/json" -d '
    {
      "jsonrpc":"2.0", "id":1,
      "method": "getRecentPrioritizationFees"
    }
  '
  ```
- [Helius CLI](../defi/Helious.md#cli)
