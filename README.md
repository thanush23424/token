# AmazonShoppingContract

## Overview

The `AmazonShoppingContract` is a simple smart contract written in Solidity, designed to facilitate the addition and purchase of apples with a deferred payment option. The contract enforces specific rules for adding apples to a virtual basket and provides functionality for completing the purchase of these apples. This smart contract is designed to run on the Ethereum blockchain.

## Features

- **Add Apple to Basket**: Allows adding apples with a specified price to the basket. The price must be greater than 0 and should be a multiple of 100 to be eligible for the deferred payment option.
- **Complete Buy**: Facilitates the purchase of apples and updates the total number of buys. There are restrictions on the number of apples that can be bought in one transaction when using the deferred payment option.

## Contract Details

### State Variables

- `mapping(uint256 => uint256) public appleBasket`: A mapping that stores the price of each apple identified by its ID.
- `uint256 public totalBuys`: A counter that keeps track of the total number of apples bought.

### Functions

#### `addApple`

```solidity
function addApple(uint256 _appleId, uint256 _price) external
```

- **Description**: Adds an apple with a given ID and price to the basket.
- **Parameters**:
  - `_appleId`: The unique identifier for the apple.
  - `_price`: The price of the apple.
- **Requirements**:
  - The price must be greater than 0.
  - The price must be a multiple of 100 to be eligible for the deferred payment option.
- **Behavior**: If the requirements are met, the apple is added to the `appleBasket` mapping.

#### `completeBuy`

```solidity
function completeBuy(uint256 _applesBought) external
```

- **Description**: Completes the purchase of a specified number of apples.
- **Parameters**:
  - `_applesBought`: The number of apples being bought.
- **Requirements**:
  - The number of apples bought using the deferred payment option should not exceed 10. If more than 10 apples are bought, the transaction is reverted with a message "300 bonus credits credited to your account".
- **Behavior**: If the requirements are met, the `totalBuys` counter is updated by adding the number of apples bought.

## Error Handling

- **assert**: Used to ensure that the price of the apple being added is greater than 0.
- **require**: Ensures that the price of the apple is a multiple of 100.
- **revert**: If the number of apples bought exceeds 10, the transaction is reverted with a specific message.

## Deployment

To deploy this contract, you need an Ethereum wallet and a development environment such as Remix, Truffle, or Hardhat. Ensure that you have sufficient test ETH in your wallet for deploying the contract on a test network like Ropsten or Rinkeby.

1. Compile the contract using Solidity compiler version 0.8.0 or higher.
2. Deploy the contract to your desired Ethereum network.
3. Interact with the contract using the provided functions to add apples and complete purchases.

## License

This project is licensed under the MIT License. See the SPDX license identifier at the top of the contract for more details.
