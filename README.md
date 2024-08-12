## RLUSD Foundry Template

## Documentation

https://book.getfoundry.sh/

## Setup

### Install Foundry

[Foundry Installation Guide](https://book.getfoundry.sh/getting-started/installation)

### Run Foundryup

```
foundryup
```

### Install dependencies

```
forge install
```

### Create a private key and fund it with testnet or real ETH

* You can generate keys with foundry or use an existing keypair
* [Foundry Create New Wallet Guide](https://book.getfoundry.sh/reference/cast/cast-wallet-new)
* **Note:** Refer to the foundry documentation for more information on how to pass the private via Keystore instead of the command line. For brevity, all examples after this secution will manually pass keys via the command line, but this is not recommended for production use. Keystore is the recommended method for passing private keys to the foundry CLI in production.

* Create a new keypair without saving it to a keystore:
```
cast wallet new
```

* Create a new keypair and save it in the keystore directory:
```
cast wallet new keystore
```


### Create a .env file

```
ETHERSCAN_MAINNET_KEY=PRIVATE_KEY_GOES_HERE
```


## Cli Commands

* **Note:** The following commands are passing private keys via the command line. This is not recommended for production use. Keystore is the recommended method for passing private keys to the foundry CLI in production.
* **Note:** Keystore has it's own flag. You can pass the keystore flag to any command that requires a private key. [Forge Create Keystore](https://book.getfoundry.sh/reference/forge/forge-create#wallet-options---keystore)

### Contract Deployment - Mainnet
```
forge create 
    --private-key <your_private_key> \
    src/<file-name>.sol:<contract-name>
```

### Contract Deployment - Sepolia
```
forge create --rpc-url https://ethereum-sepolia-rpc.publicnode.com \
    --chain-id 11155111 \
    --private-key <your_private_key> \
    src/<file-name>.sol:<contract-name>
```

### Verify Contract - Mainnet
```
forge verify-contract \
    --watch \
    --etherscan-api-key mainnet\
     --compiler-version v0.8.26+commit.8a97fa7a \
    <deployed-contract-address> \
     src/<file-name>.sol:<contract-name>
```    

### Verify Contract - Sepolia
```
forge verify-contract \
    --chain-id 11155111 \
    --watch \
    --etherscan-api-key mainnet\
     --compiler-version v0.8.26+commit.8a97fa7a \
    <deployed-contract-address> \
     src/<file-name>.sol:<contract-name>
```

---

## Example Commands

### Contract Deployment - Sepolia Example
```
forge create --rpc-url https://ethereum-sepolia-rpc.publicnode.com \
    --chain-id 11155111 \
    --private-key 1234567890123456789012345678901234567890123456789012345678901234567890 \
    src/RLUSD.sol:TestRLUSD
```

### Successfully Deployement Output - Sepolia Example
```
Deployer: 0xc55E1e8105837135553dba5c3eb05Fc1ae0704c4
Deployed to: 0x347F4bE5D32c9e36C90D1c019babe0614D0DFd6d
Transaction hash: 0x976bee9a36d2b6be8dd3f2e4c85969c1a88cc6136758a7f62b73723559470bd3
```

### Verify Contract After Deployment Example - Sepolia Example
* **Note:** The contract address is the address of the deployed contract.
```
forge verify-contract \
    --chain-id 11155111 \
    --watch \
    --etherscan-api-key mainnet\
     --compiler-version v0.8.26+commit.8a97fa7a \
    0x347F4bE5D32c9e36C90D1c019babe0614D0DFd6d \
    src/RLUSD.sol:TestRLUSD
```

### Resulting Verifed Contract - Sepolia
sepolia: 0x347F4bE5D32c9e36C90D1c019babe0614D0DFd6d
https://sepolia.etherscan.io/address/0x347F4bE5D32c9e36C90D1c019babe0614D0DFd6d#code