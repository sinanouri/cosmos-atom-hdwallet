# cosmos-atom-hdwallet

`cosmos-atom-hdwallet` is a Node.js package that provides a DirectSecp256k1HdWallet implementation for Cosmos-SDK-based blockchains. It allows you to generate and manage hierarchical deterministic (HD) wallets.

## Installation

The package can be installed using `npm`:


`npm install cosmos-atom-hdwallet` 

## Usage

To use `cosmos-atom-hdwallet`, import `DirectSecp256k1HdWallet` from the package, and create an instance of the wallet using a mnemonic phrase and a derivation path. You can then use the wallet to sign transactions and retrieve the account address and private key.



    const { DirectSecp256k1HdWallet } = require('cosmos-atom-hdwallet')
    
    async function atom() {
      const derivationPath = "m/0'/0"
      const mnemonic = "profit oppose submit bunker faculty load alpha innocent umbrella boil cargo stomach";
      const wallet = await DirectSecp256k1HdWallet.fromMnemonicToWallet(mnemonic, derivationPath)
      const [account] = await wallet.getAccountsWithPrivkeys();
      const address = account.address
      const wif = Buffer.from(account.privkey).toString('hex')
      console.log({ address: address, privateKey: wif })
    }
    
    atom()

## API

### `DirectSecp256k1HdWallet`

This class represents a DirectSecp256k1HdWallet instance.

#### `fromMnemonicToWallet(mnemonic: string, derivationPath: string): Promise<DirectSecp256k1HdWallet>`

Creates a new `DirectSecp256k1HdWallet` instance from a mnemonic phrase and a derivation path.

#### `getAccounts(): Promise<Account[]>`

Retrieves an array of accounts associated with the wallet.

#### `getAccountsWithPrivkeys(): Promise<Account[]>`

Retrieves an array of accounts associated with the wallet, including the private keys.

## License

`cosmos-atom-hdwallet` is distributed under the MIT license. See [LICENSE](https://chat.openai.com/LICENSE) for more information.