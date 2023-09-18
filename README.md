# Pesabooks Smart Contracts

This repository contains the smart contracts for the early version of Pesabooks.com, a decentralized application that enables a group of people to save and invest together in the cryptocurrency market.

**Note:** Please note that this version of the smart contracts is no longer actively maintained or used by Pesabooks. Pesabooks is now powered by [Safe (formely Gnosis Safe)](https://safe.global/)

The project consists of the following contracts:

## Contracts

### PoolSafe.sol

The `PoolSafe` contract is responsible for securely holding and managing the funds of a pool. It provides functions to check the balance of tokens in the pool, manage admin roles, and execute delegate calls to the other contracts registered in the `Registry`  through the function `relayCall`.  

Only the authorized controller can invoke the `relayCall` function in the `PoolSafe` contract, adding an extra layer of safety and access control.

For further details, please refer to the [PoolSafe.sol](src/PoolSafe.sol) file.

### Controller.sol

The `Controller` contract acts as an intermediary and implements the business logic for interactions between users and the `PoolSafe` contract. Users can deposit and withdraw funds by calling the `Controller` contract, which then executes delegate calls to the `PoolSafe` contract.

By separating fund management from the core logic, the contract architecture allows for code upgradability. This means that the core logic of the pool can be updated without affecting the fund management functionalities. The delegation of functions from the `Controller` to the `PoolSafe` contract ensures that any future upgrades or changes to the core logic do not require modifying the fund management code.

For more information, refer to the [Controller.sol](src/Controller.sol) file.

### Registry.sol

The `Registry` contract serves as a central registry for storing the addresses of authorized contracts like the auhtorized controller that can make delegate call to the pools safe, and other contracts that can be called via the delegate call. 

For more information, refer to the [Registry.sol](src/Registry.sol) file.


