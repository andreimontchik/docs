# Node.js
[Website](https://nodejs.org/en)

## Installation
1. Obtain an info about the latest stable version on the [Node.js website](https://nodejs.org/en/download).
1. Install the latest stable [nvm](https://github.com/nvm-sh/nvm): `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash`
1. Restart terminal and check the nvm installation: `nvm --version`
1. Install the desired NodeJS version: 
   * `nvm install 24`
   * or create the `.nvmrc` file and specify the required NodeJS version in it: `nvm use; nvm install`
1. Check the NodeJS: `node --version`

## Upgrade Dependencies
1. `npm outdated`
1. `rm -rf node_modules`
1. `rm package-lock.json`
1. `npm install`
1. `rm -rf dist`
1. `npm run build`

## TypeScript
### Installation
1. Install TypeScript: `npm install -D typescript tsx`
1. Verify the TypeScript installation: `npx tsc -v`