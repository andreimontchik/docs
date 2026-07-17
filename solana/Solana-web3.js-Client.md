# Docs
* [The client page](https://solana.com/docs/clients/javascript)
* [API](https://solana-labs.github.io/solana-web3.js/)
* [V1 Source Code](https://github.com/solana-labs/solana-web3.js/tree/master/packages/library-legacy)
* [V2 Source Code and the API review](https://github.com/solana-labs/solana-web3.js/tree/master/packages/library)
  * [V2 Codecs Source Code](https://github.com/solana-labs/solana-web3.js/tree/master/packages/codecs-core)
* [Examples](https://solana.com/docs/clients/javascript-reference)

# [Installation](https://solana.com/docs/clients/javascript#installation)
1. [Install NodeJS](../../public/wiki/nodejs#installation)
1. Enable [Corepack](https://nodejs.org/api/corepack.html#corepack): `corepack enable`
1. Enable Corepack, that will make Yarn available: `corepack enable`
1. Install the Solana Web3.js client: ` yarn add @solana/web3.js`
1. Install Typescript: `npm install -g typescript`
1. Install the BN JavaScript library and it's Typescript definitions: `npm install bn.js @types/bn.js --save`
1. Run the `tsc --init` command in the scripts directory to generate the default TypeScript configuration file. It will setup some helpful flags. Consider commenting out the `"strict": true` to disable strict type checking.

# Usage Examples
  * [From the Cookbook](https://solanacookbook.com/#contributing)
    * [Data Serialization](https://solanacookbook.com/guides/serialization.html#setting-up-for-borsh-serialization)
  * [From the Docs](https://solana.com/docs/clients/javascript-reference)
    * [Retrieve the most recent block](https://solana.com/docs/advanced/versions#how-to-set-max-supported-version)
    * [Create and send a transaction](https://solana.com/docs/clients/javascript#creating-and-sending-transactions)
    * [Interacting with Custom Programs](https://solana.com/docs/clients/javascript#interacting-with-custom-programs)
  * [From the V1 Source Code](https://github.com/solana-labs/solana-web3.js/tree/master/packages/library-legacy/test)
  * [Experimental from the V2 Source Code](https://github.com/solana-labs/solana-web3.js/tree/master/packages/library)
    * [V2 Transactions](https://github.com/solana-labs/solana-web3.js/tree/master/packages/library#transactions)
    * [V2 Codecs](https://github.com/solana-labs/solana-web3.js/tree/master/packages/library#codecs)

# Build and Run
1. To generate the JavaScript file, run `tsc` in the scripts directory. It will pick up the TypeScript compiler configuration from the `tsconfig.json` file and compile all TypeScript files.
1. Run the JavaScript file: `node <SCRIPT_NAME.js>`

# CLI
* List of NodeJS modules: `npm ls`.
