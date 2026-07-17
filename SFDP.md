# Docs
* [Official Solana Delegation Program Page](https://solana.org/delegation-program)
* [Delegation Criteria](https://solana.org/delegation-criteria) 
* [Upcoming SFDP Changes](https://forum.solana.com/t/upcoming-sfdp-changes/772/1)

# Notes
* [SF matches self stake first](https://solana.org/delegation-criteria#mainnet-matching-criteria).
* [SF recalculates residual stake every epoch](https://solana.org/faq#residual-amount). The residial stake amount is left over after matching is applied.
  * [SF goal is 10,000 SOL of residual stake](https://discord.com/channels/428295358100013066/849749936916267029/1207311727121932368)
* [SF covers vote cost for the first year](https://solana.org/faq#vote_cost_coverage). The coverage is 100% for first 3 months and decreases 25% every three months.
* [Vote cost coverage calculation](https://solana.org/faq#vcc_vote_cost_calc). 
* The Mainnet onboarding process might take up to 6 months! According to the [How To Become a Validator on Solana](https://medium.com/@Cogent_Crypto/how-to-become-a-validator-on-solana-9dc4288107b7) article. the "Delegation Program Timelines" section.
* [It might take up to 6 epochs for the stake delegation on Mainnet](https://solana.org/faq#when_staked), presumably after onboarding is successfully completed.
* According to [Validator Calculator](https://cogentcrypto.io/ValidatorProfitCalculator) the __5%__ commission, __110 SOL__ price, 10,000 residual stake, vote cost reimbursement and stake matching would require __8,000 SOL__ self stake to break even.

**Mainnet requirements:**
* [Healthy Testnet and Mainnet validators](https://solana.org/delegation-criteria#mainnet-residual-criteria)
* Mainnet max commission is 7%
* Should self stake at least 100 SOL
* Skip rate <= 5% + cluster avg skip rate
* Vote credits 97%

# Tools
* [Validator Delegation Dashboard](https://solana.org/validators-search?o=&d=&q=&f=)
* [Validator Profit Calculator](https://cogentcrypto.io/ValidatorProfitCalculator)
* [Validator Profit Estimator](https://docs.google.com/spreadsheets/d/1HPU_uG3iJ_ns27CItdWGllW0c-Pn07J0_LEDZs1otQY/edit#gid=0)

## How to
### [Set up Devnet Validator](https://github.com/agjell/sol-tutorials/blob/master/setting-up-a-solana-devnet-validator.md)