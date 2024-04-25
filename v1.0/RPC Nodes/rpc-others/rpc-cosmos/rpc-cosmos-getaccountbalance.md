---
title: "getAccountBalance"
slug: "rpc-cosmos-getaccountbalance"
category: "6620f7e31ea673003624a8ce"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Fetches the balance of a Cosmos account at a specific block height."
  image: []
  keywords: "cosmos, rosetta, account balance, blockchain"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `getAccountBalance` endpoint in the Cosmos Rosetta API allows fetching the balance for a specified account identifier at a given block. This endpoint returns the balance only for the requested account and block, without aggregating sub-account balances unless explicitly requested.

## Parameters

| Name                   | Type                               | Required | Description                                                                   |
| ---------------------- | ---------------------------------- | -------- | ----------------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.                         |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                                |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.                    |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                                       |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                                    |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                                     |
| `accountIdentifier`    | object                             | Yes      | Contains information about the account.                                       |
| `address`              | string (from accountIdentifier)    | Yes      | The account address associated with the operation.                            |
| `sub_account`          | object (from accountIdentifier)    | No       | Optional sub-account information.                                             |
| `metadata`             | object (from accountIdentifier)    | No       | Optional metadata for the account, including public keys if relevant.         |
| `address`              | string (from sub_account)          | Yes      | The sub-account address.                                                      |
| `metadata`             | object (from sub_account)          | No       | Metadata for the sub-account.                                                 |
| `blockIdentifier`      | object                             | No       | Information about the specific block.                                         |
| `index`                | number (from blockIdentifier)      | No       | The index of the block (Type: number, Format: int64).                         |
| `hash`                 | string (from blockIdentifier)      | No       | The hash of the block.                                                        |
| `currency`             | object                             | Yes      | Specifies the currency details.                                               |
| `symbol`               | string (from currency)             | Yes      | The symbol or code of the currency.                                           |
| `decimals`             | number (from currency)             | Yes      | The number of decimal places for the currency.                                |
| `metadata`             | object (from currency)             | No       | Additional information related to the currency, such as the contract address. |

## Returns

| Field             | Type   | Description                                      |
| ----------------- | ------ | ------------------------------------------------ |
| `blockIdentifier` | object | The block at which the balance was fetched.      |
| `balances`        | array  | A list of balances found at the specified block. |

## Example Result

```json
{
  "blockIdentifier": {
    "index": 1000000,
    "hash": "C2F9D..."
  },
  "balances": [
    {
      "value": "100000000",
      "currency": {
        "symbol": "ATOM",
        "decimals": 6
      }
    }
  ]
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/account/balance' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "cosmos-mainnet"
    },
    "accountIdentifier": {
      "address": "{{address}}",
    }
}'
```
```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Cosmos
const cosmos = await TatumSDK.init<Cosmos>({
  network: Network.COSMOS_MAINNET,
});

// Define the input parameters with only required fields
const params = {
  networkIdentifier: {
    blockchain: "COSMOS",
    network: "COSMOS_MAINNET",
  },
  accountIdentifier: {
    address: "{{address}}",
  },
};

// Fetch the account balance
const accountBalance = await tatum.rpc.getAccountBalance(params);

// Log the account balance
console.log("Account Balance:", accountBalance);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```
