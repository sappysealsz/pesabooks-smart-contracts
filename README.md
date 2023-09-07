# Pesabooks Smart Contracts

This repository contains the smart contracts for the early version of Pesabooks.com, a decentralized application that enables a group of people to save and invest together in the cryptocurrency market.

**Note:** Please note that this version of the smart contracts is no longer actively maintained or used by Pesabooks. Pesabooks is now powered by [Safe (formely Gnosis Safe)](https://safe.global/)

The project consists of the following contracts:

## Contracts

### PoolSafe.sol

The `PoolSafe` contract is responsible for securely holding and managing the funds in the Pesabooks platform. It provides basic functionality for depositing and withdrawing funds. Users do not interact directly with the `PoolSafe` contract; instead, they interact with the `Controller` contract. The `PoolSafe` contract always checks if the calling controller is authorized by verifying it through the `Registry` contract. 

For further details, please refer to the [PoolSafe.sol](src/PoolSafe.sol) file.

### Controller.sol

The `Controller` contract acts as an intermediary between users and the `PoolSafe` contract. It contains the business logic and handles user interactions such as depositing and withdrawing funds. The `Controller` contract calls the `PoolSafe` contract through a relay call, ensuring the upgradability of the platform. By separating the logic into the `Controller` contract, it becomes easier to update and add new features without compromising the security of the funds stored in the `PoolSafe`.

For more information, refer to the [Controller.sol](src/Controller.sol) file.

### Registry.sol

The `Registry` contract serves as a central registry for storing the addresses of authorized contracts (controllers). 

For more information, refer to the [Registry.sol](src/Registry.sol) file.


