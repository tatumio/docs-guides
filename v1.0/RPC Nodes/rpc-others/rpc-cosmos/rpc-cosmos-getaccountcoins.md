---
title: "accountCoins"
slug: "accountCoins"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Rosetta API for {{blockchain}}"
hidden: false
metadata:
  image: []
  keywords: "{{blockchain}}, account coins, Rosetta API"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `accountCoins` method retrieves information about the coins stored at a specific account address on the {{blockchain}} network, using the Rosetta API. This includes detailed data on each coin or token associated with the account, which is crucial for tracking asset distributions and understanding the account's composition on the blockchain.

## Parameters

| Name                   | Type                               | Required | Description                                                                                                                                    |
| ---------------------- | ---------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `networkIdentifier`    | object                             | Yes      | Identifies the Cosmos blockchain and network details.                                                                                          |
| `blockchain`           | string (from networkIdentifier)    | Yes      | The blockchain identifier, typically "Cosmos".                                                                                                 |
| `network`              | string (from networkIdentifier)    | Yes      | The network name on which the transaction is taking place.                                                                                     |
| `subNetworkIdentifier` | object (from networkIdentifier)    | No       | Optional sub-network identifier object.                                                                                                        |
| `network`              | string (from subNetworkIdentifier) | Yes      | The name of the sub-network within Cosmos.                                                                                                     |
| `metadata`             | object (from subNetworkIdentifier) | No       | Metadata associated with the sub-network.                                                                                                      |
| `accountIdentifier`    | object                             | Yes      | Contains information about the account.                                                                                                        |
| `address`              | string (from accountIdentifier)    | Yes      | The account address associated with the operation.                                                                                             |
| `sub_account`          | object (from accountIdentifier)    | No       | Optional sub-account information.                                                                                                              |
| `metadata`             | object (from accountIdentifier)    | No       | Optional metadata for the account, including public keys if relevant.                                                                          |
| `address`              | string (from sub_account)          | Yes      | The sub-account address.                                                                                                                       |
| `metadata`             | object (from sub_account)          | No       | Metadata for the sub-account.                                                                                                                  |
| `includeMempool`       | boolean                            | Yes      | Include state from the mempool when looking up an account's unspent coins. Note, using this functionality breaks any guarantee of idempotency. |
| `currency`             | object                             | No      | Specifies the currency details.                                                                                                                |
| `symbol`               | string (from currency)             | Yes      | The symbol or code of the currency.                                                                                                            |
| `decimals`             | number (from currency)             | Yes      | The number of decimal places for the currency.                                                                                                 |
| `metadata`             | object (from currency)             | No       | Additional information related to the currency, such as the contract address.                                                                  |

## Returns

The response includes details about each coin held in the specified account and sub-account (if provided):

| Field           | Description                                                         |
| --------------- | ------------------------------------------------------------------- |
| `coins`           | A list of coin objects representing each asset held by the account. |
| `blockIdentifier` | The block identifier where the latest balance snapshot was taken.   |

## Example Result

```json
{
  "blockIdentifier": {
    "index": 1234567,
    "hash": "a1b2c3d4..."
  },
  "coins": [
    {
      "coin_identifier": {
        "identifier": "coin1"
      },
      "amount": {
        "value": "100000000",
        "currency": {
          "symbol": "ATOM",
          "decimals": 6
        }
      }
    }
  ]
}
```

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/account/coins' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "networkIdentifier": {
        "blockchain": "{{blockchain}}",
        "network": "{{network}}"
    },
    "accountIdentifier": {
        "address": "{{address}}",
    },
    "include_mempool": true
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const {{blockchain}} = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

const accountCoins = await tatum.rpc.getAccountCoins({
  networkIdentifier: {
    blockchain: "{{blockchain}}",
    network: "{{network}}"
  },
  accountIdentifier: {
    address: "{{address}}",
  },
  include_mempool: true
});

console.log(accountCoins);

await {{blockchain}}.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
