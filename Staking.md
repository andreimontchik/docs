# Docs
* [Staking in Solana](https://solana.com/docs/economics/staking)
* [Staking FAQ](https://solana.com/staking)
* [Stake Accounts](https://solana.com/docs/economics/staking/stake-accounts)
* [Stake Pool Docs](https://solana.com/docs/economics/staking/stake-programming#stake-pools)
* [SF Stake Pools](https://solana.org/stake-pools)

# Notes
* [The delegation "warming up" or "cooling down" period lasts until the end of current Epoch.](https://solana.com/staking#overview/delegation-timing-considerations)
* Only up to 25% of global stake can change state per an Epoch.
* Staking reward percentage is derived by inflation rate, Validator uptime and total staked number by the inflation rate. As of 02/10/24 is was 5.49% for Epoch 572.
* [Liquid Staking](https://www.jito.network/blog/solana-liquid-staking-101/) allows to use the Liquid Stake Tokens(LST) received for staked SOL for investing or trading and keep earning rewards on staked SOL. 

## Stake Accounts
The [Stake Account](https://solana.com/docs/economics/staking/stake-accounts) info:
* [Stake account types](https://solana.com/docs/economics/staking/stake-accounts#understanding-account-authorities):
  * Account address - identifies an account
  * Stake authority - delegating stake, managing stake accounts
  * Withdraw authority - withdrawing undelegated stake, managing stake authority
* Lookup authority - manages the stake account [lookups](https://solana.com/docs/economics/staking/stake-accounts#lockups)
* Stake and withdraw authority could be the same and can be assigned to multiple stake accounts.
* Stake account is destroyed when it's balanced becomes 0 SOL.
* The SF stake delegation is managed by the ??? bot.

## Stake pools
The [Stake pools](https://solana.com/docs/economics/staking/stake-programming#stake-pools) info:
* Allow to deposit SOL in exchange of staking SPL tokens and earn rewards w/o managing stakes directly.
* [Stake pools operation](https://spl.solana.com/stake-pool/overview#operation)
* It takes around 1 SOL to create stake account on a validator.
* The [Stake pool fees](https://spl.solana.com/stake-pool/fees):
  * There are stake and SOL deposit/withdraw fees paid by users.
* It is possible to run the [Single Validator stake pool](https://spl.solana.com/single-pool).

# Tools
* [SolFlare](https://solflare.com/) - Solana recommended wallet that supports staking.
* To see the latest inflation rate: `solana inflation`
* Current Epoch info: `solana epoch-info`