# Ethereum Truffle Token Box

Truffle box configured to create an ERC20 token using Open Zeppelin smart contracts library and deploy on Görli Ethereum testnet network.

#### Tutorials 2020

- English:
[Using Truffle Sol token box](https://ethereum.solange.dev/#/en/truffle/box-token-2020)
- Español: 
[Usando Truffle Sol token box](https://ethereum.solange.dev/#/es/truffle/box-token-2020)
- Português:
[Usando Truffle Sol token box](https://ethereum.solange.dev/#/pt/truffle/box-token-2020)

#### Updated 2021
- Open Zeppelin smart contracts 4.0.0 
- Solidity 0.8.4

[Sol token box](https://github.com/solangegueiros/sol-token-box)

## Requirements

There are a few technical requirements before we start. 
To use `Truffle boxes`, you need to have installed in your computer:

- Git
- a POSIX compliant shell
- cURL
- Node.js and NPM
- a code editor


**Truffle framework**

Once you have those requirements installed, you only need one command to install `Truffle`.
It is better to do it globally:

```shell
npm install -g truffle
```

## Installation

1. Create a new folder. 
For example, create the folder `mytoken`.
Navigate to the folder in the terminal.

```shell
mkdir mytoken
cd mytoken
```

2. Run the unbox command. 
This also takes care of installing the necessary dependencies and it can take some time.

```shell
truffle unbox solangegueiros/eth-token-box-2020
```

This is the result using Windows OS:

![truffle unbox](/images/image-01.png)

## Development console

Truffle has an interactive console that also spawns a development blockchain. This is very useful for compiling, deploying and testing locally.

3. Run the development console. This command is successful if you see a list of 10 accounts, a mnemonic and the command prompt is now `truffle(develop)>`

```shell
truffle develop
```

You will now be in the truffle develop console with seeded accounts and their associated private keys listed.

```txt
C:\ETH\mytoken>truffle develop

Truffle Develop started at http://127.0.0.1:8545/

Accounts:
(0) 0x1056f747cf4bc7710e178b2aeed4eb8c8506c728
(1) 0x45a71c00382c2898b5d6fae69a6f7bfe6edab80c
(2) 0x1596384706dc9ac4cca7f50279a4abe591d6c3fe
(3) 0x9576d0a496b645baa64f22aceb2328e7468d4113
(4) 0xd431572eef7d77584d944c1809398a155e89f830
(5) 0x92c111839718fe0800fadccc67068b40b8524a0f
(6) 0x6da22b5a027146619bfe6704957f7f36ff029c48
(7) 0x2c3a82d8c3993f8c80dcaf91025437bd057df867
(8) 0xc43ae7a44f7deb759177b7093f06512a0a9ff5d7
(9) 0xe61bf00cd7dce248449cfe58f23a4ef7d542bc0b

Private Keys:
(0) f32f32839fe27ad906b63eafb326f26fed95c231e3c5e33c7cdd08f62db63167
(1) ebef990088f27f6ef13b5e52a77d5dcc5a76862a701908c586d01b6fe93562b3
(2) 598ccae5e4436fedeb0e798c0d254789c55a63401ebfc3ae8ddde29634ddfcde
(3) 09934b80f391e0024b8cb00cd73790fdf64c4d0509e144766414fee317cd3f4e
(4) ac745b84b6574b5738d364b43e0d471c9d5107504acc709c90f6f091b78c751b
(5) 449654cde095f2349113ef12a93e139b4302bc95adb3619d08adf53dde9b8847
(6) c217f12a89c352fc70b5f1bd5742314b4fb1bb1e35cb779fdb3c2390106355db
(7) 1d4c74dfa4e99e161130c18cc63938bb120a128cefbf1b9188efc678bf5722cb
(8) 0f44e0becf2e090db498a1b747d2a758fcc81fb0241f350d61117a9c6b1fa82e
(9) 85218c5eec657470dafeb09e6f7101f91d21bfe822fbeeecfc9275f798662a63

Mnemonic: virtual valve razor retreat either turn possible student grief engage attract fiber

⚠️  Important ⚠️  : This mnemonic was created for you by Truffle. It is not secure.
Ensure you do not use it on production blockchains, or else you risk losing funds.

truffle(develop)>
```

## Token.sol

Take a look at the smart contract `Token.sol`. You can check it out in folder `contracts`.

![Token.sol](/images/image-19.png)

> Token.sol has only 7 code lines!

This smart contract is a mintable [ERC20](https://eips.ethereum.org/EIPS/eip-20) token. This means that, in addition to the standard ERC20 specification, it has a function for issuing new tokens.

To create our ERC20 Token, we will import `ERC20Mintable` from Open Zeppelin. 
This library itself imports several other libraries such as `SafeMath.sol`, the standards for this kind of token, and the capability to mint tokens.

Inside the token, we define some basic information about the token: `name`, `symbol`, and number of `decimals` for the precision.

To inherit the library's attributes and functions, we simply define our contract as a `ERC20Mintable` using the `is` keyword in this way.

4. Compile the smart contract. 

Note inside the development console we don't preface commands with `truffle`.

> To make sure you're in the development console, the command prompt must be `truffle(develop)>`

```shell
compile
```

The `compile output` should be similar to:

![truffle compile](/images/image-02.png)

5. Deploy (migrate) the smart contract.

```shell
migrate
```

And the `migrate output` should be similar to:

![truffle migrate](/images/image-03.png)

6. Running contract tests.

This Truffle box also comes with the file `TestToken.js` which include some examples for testing the smart contract. 
You can check it out in the `test` folder.

There are many other tests which can be done to check an ERC20 token.

Run this command in the development console:

```shell
test
```

This `test output` should be similar to:

![truffle test](/images/image-04.png)

Note the command varies slightly if you're in or outside of the development console.

```javascript
// inside the development console.
test

// outside the development console.
truffle test
```

## Interact with the token using Truffle console 

1. Get your accounts in Truffle console.

In the Truffle console, enter:

```javascript
const accounts = await web3.eth.getAccounts()
```

Don’t worry about the `undefined` return, it is ok. See the addresses after it by entering the command below:

```javascript
accounts
```

And to view each account:

```javascript
accounts[0]
accounts[1]
```

Take a look in the results:

![accounts](/images/image-05.png)

2. Interact with the token using Truffle console.

First of all, connect with your token

```javascript
const token = await Token.deployed()
```

3. Confirm if our instance is OK.

Enter the instance’s name:  `token`, then `.`, without space hit the TAB button twice to trigger auto-complete as seen below. 
This will display the published address of the smart contract, and the transaction hash for its deployment, among other things, including all public variables and methods available.

```javascript
token. [TAB] [TAB]
```

![token tab tab](/images/image-06.png)

4. Check the total supply

To check if we have tokens already minted, call the `totalSupply` function:

```javascript
(await token.totalSupply()).toString()
```

The returned value is 0, which is expected, since we did not perform any initial mint when we deployed the token.

5. Check the token balance

To check the balance of an account, call the `balanceOf` function. For example, to check the balance of account 0:

```javascript
(await token.balanceOf(accounts[0])).toString()
```

Take a look in the results of total supply and balanceOf:

![total supply and balanceOf 0](/images/image-09.png)

The returned value is also 0, which is expected, since we did not make any initial mint when we deployed the token, and by definition no accounts can have any tokens yet.

6. Mint tokens

Run this command:

```javascript
token.mint(accounts[0], 10000)
```

This command sent a transaction to mint 100 tokens for account 0. 

![token.mint account 0](/images/image-10.png)

You can also mint to a specific address, `0xa52515946DAABe072f446Cc014a4eaA93fb9Fd79`:

```javascript
token.mint("0xa52515946DAABe072f446Cc014a4eaA93fb9Fd79", 10000)
```

![token.mint address](/images/image-11.png)

7. Reconfirm the token balance

Check the balance of account 0 again:

```javascript
(await token.balanceOf(accounts[0])).toString()
```

The returned value is 10000, which is 100 with 2 decimal places of precision. This is exactly what we expected, as we issued 100 tokens

Also, you can get the balance of a specific address, for example, `0xa52515946DAABe072f446Cc014a4eaA93fb9Fd79`:

```javascript
(await token.balanceOf("0xa52515946DAABe072f446Cc014a4eaA93fb9Fd79")).toString()
```

Take a look in the results:

![balanceOf account 0 and address with 10000](/images/image-13.png)

8. Check the total supply (again)

Check the total supply again:

```javascript
(await token.totalSupply()).toString()
```

![totalSupply 20000](/images/image-15.png)

The returned value is 20000, which is 200 with 2 decimal places of precision. 
After minting 100 tokens for 2 accounts, this is perfect!

9. Transfer tokens

To transfer 40 tokens from account 0 to account 2. 
This can be done by calling the `transfer` function.

```javascript
token.transfer(accounts[2], 4000, {from: accounts[0]})
```

![token.transfer](/images/image-16.png)

Account 2 had no tokens before the transfer, and now it should have 40. Account 1 must have 60 tokens. Also the total supply will be the same.

Let’s check the balance of each account and the total supply:

```javascript
(await token.balanceOf(accounts[2])).toString()
(await token.balanceOf(accounts[0])).toString()
(await token.totalSupply()).toString()
```

Take a look in the results:

![balances after transfer](/images/image-17.png)

Great! The balances of both accounts and the total supply are correct.

### Exit Truffle console

In the Truffle console, enter this command to exit the terminal:

```shell
.exit
```

## Deploy on Görli - Ethereum testnet network

[Görli Testnet](https://goerli.net/)

### Setup an account & get R-BTC

1. Create a wallet

The easy way to setup an account is using a web3 wallet injected in the browser.
Some options are:
- [Metamask](https://metamask.io/)
- [Nifty](https://www.poa.network/for-users/nifty-wallet)

Select the Goerli Network in the web wallet.

2. Update `.secret` file

After create your wallet, update your mnemonic in the file `.secret`, located in the folder project, and save it.

3. Get some ETHs - Faucets
- [goerli-faucet.slock.it](https://goerli-faucet.slock.it/)
- [faucet.goerli.mudit.blog](https://faucet.goerli.mudit.blog/)


### Connect to Görli

Run the Truffle development console 

```shell
truffle console --network goerli
```

### Test the connection to Görli network

Run this commands in the Truffle console:

#### Block number
Shows the last block number.

```javascript
(await web3.eth.getBlockNumber()).toString()
```
#### Network ID

To get the network ID, run this command:

```javascript
(await web3.eth.net.getId()).toString()
```

> The Görli network ID is 5.

Exit the Truffle console:

```shell
.exit
```

### Compile and migrate the smart contracts. 

We will do it running the below commands directly in the terminal, without using the truffle console, this is to show you an alternative.

On any of the networks, run this commands in a terminal (not in Truffle console).
To use Testnet or Mainnet, you need to specify this using the parameter `-- network`:

```shell
truffle migrate --network goerli
```

The migrate process in a real blockchain takes more time, because Truffle creates some transactions which need to be mined on the blockchain.

### Where to go from here

Interact with the token published on the network using Truffle console, doing the same steps which was done before:

- Get your accounts
- Connect with your token
- Check the total supply or the token balance
- Mint tokens
- Transfer tokens

### Add the token in your web wallet

