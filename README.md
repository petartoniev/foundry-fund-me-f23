Proper README

# FundMe Smart Contract

## Overview

The `FundMe` smart contract allows users to fund the contract with ETH and provides functions for withdrawing funds.
It also includes features to set a minimum funding value in USD, utilizing Chainlink oracles for price feeds.

## Features

- **Funding**: Users can send ETH to the contract.
- **Withdrawal**: The owner can withdraw the funds.
- **Minimum Funding Value**: Set in USD to ensure a minimum amount is met.
- **Price Feeds**: Uses Chainlink oracles for accurate ETH/USD conversion.

1. Clone the repository:
    ```sh
    git clone https://github.com/petartoniev/foundry-fund-me-f23
    cd foundry-fund-me-f23

    ```

3. Compile the contracts:
    ```sh
    forge build
    ```

## Usage

### Deployment

Deployment to a testnet or mainnet
Setup environment variables
You'll want to set your SEPOLIA_RPC_URL and PRIVATE_KEY as environment variables. You can add them to a .env file, similar to what you see in .env.example.

PRIVATE_KEY: The private key of your account (like from metamask). NOTE: FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
You can learn how to export it here.
SEPOLIA_RPC_URL: This is url of the sepolia testnet node you're working with. You can get setup with one for free from Alchemy
Optionally, add your ETHERSCAN_API_KEY if you want to verify your contract on Etherscan.

Get testnet ETH
Head over to faucets.chain.link and get some testnet ETH. You should see the ETH show up in your metamask.

Deploy
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY

Scripts
After deploying to a testnet or local net, you can run the scripts.

Using cast deployed locally example:

cast send <FUNDME_CONTRACT_ADDRESS> "fund()" --value 0.1ether --private-key <PRIVATE_KEY>

Withdraw
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()"  --private-key <PRIVATE_KEY>
Estimate gas
You can estimate how much gas things cost by running:

forge snapshot
And you'll see an output file called .gas-snapshot

Formatting
To run code formatting:

forge fmt

Coverage
Generate a coverage report to ensure your tests cover all possible scenarios:

sh
Copy code
forge coverage

## Test a specific function
forge test --match-test testWithDrawWithASingleFunder -vvv

Integration tests - Done.
Programatic verification - Done.
Push to Github