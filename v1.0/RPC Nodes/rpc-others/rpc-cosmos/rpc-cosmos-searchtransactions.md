---
title: "searchTransactions"
slug: "rpc-cosmos-searchtransactions"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Cosmos RPC"
hidden: false
metadata:
  description: "Search for transactions in the Cosmos blockchain based on various criteria."
  image: []
  keywords: "cosmos, rpc, search, transactions"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `searchTransactions` method allows you to search for transactions matching a set of provided conditions in canonical blocks. This can be useful for querying transaction data based on various criteria.

## Parameters

| Name                    | Type                                | Required | Description                                                     |
| ----------------------- | ----------------------------------- | -------- | --------------------------------------------------------------- |
| `networkIdentifier`     | object                              | Yes      | Identifies the Cosmos blockchain and network details.           |
| `blockchain`            | string (from networkIdentifier)     | Yes      | The blockchain identifier, typically "Cosmos".                  |
| `network`               | string (from networkIdentifier)     | Yes      | The network name on which the transaction is taking place.      |
| `subNetworkIdentifier`  | object (from networkIdentifier)     | No       | Optional sub-network identifier object.                         |
| `network`               | string (from subNetworkIdentifier)  | Yes      | The name of the sub-network within Cosmos.                      |
| `metadata`              | object (from subNetworkIdentifier)  | No       | Metadata associated with the sub-network.                       |
| `operator`              | enum                                | No       | Conditions `or` and `and` for complex queries.                  |
| `max_block`             | number                              | No       | The largest block index to consider.                            |
| `offset`                | number                              | No       | The offset into the result set to start returning transactions. |
| `limit`                 | number                              | No       | The maximum number of transactions to return.                   |
| `transactionIdentifier` | object                              | No       | Identifies the transaction by hash.                             |
| `hash`                  | string (from transactionIdentifier) | Yes      | The hash of the transaction.                                    |
| `accountIdentifier`     | object                              | No       | Information about the account involved.                         |
| `address`               | string (from accountIdentifier)     | Yes      | The Cosmos account address associated with the operation.       |
| `sub_account`           | object (from accountIdentifier)     | No       | Optional sub-account object.                                    |
| `metadata`              | object (from accountIdentifier)     | No       | Metadata for the account.                                       |
| `coinIdentifier`        | object                              | No       | Conditions for coin identifier.                                 |
| `identifier`            | string (from coinIdentifier)        | Yes      | A globally unique identifier of a Coin.                         |
| `currency`              | object                              | No       | Specifies the currency details.                                 |
| `symbol`                | string (from currency)              | Yes      | The symbol or code of the currency.                             |
| `decimals`              | number (from currency)              | Yes      | The number of decimal places for the currency.                  |
| `status`                | string                              | No       | The network-specific operation status type.                     |
| `type`                  | string                              | No       | The network-specific operation type.                            |
| `address`               | string                              | No       | Account address for transaction search.                         |
| `success`               | boolean                             | No       | A synthetic condition indicating success.                       |

## Returns

| Field          | Description                                            |
| -------------- | ------------------------------------------------------ |
| `transactions` | A list of transactions that match the search criteria. |

## Example Result

```json
{
  "transactions": [
    {
      "transaction_identifier": {
        "hash": "TRANSACTION_HASH"
      },
      "operations": [
        {
          "operation_identifier": {
            "index": 0
          },
          "type": "TRANSFER",
          "status": "SUCCESS",
          "account": {
            "address": "cosmos1..."
          },
          "amount": {
            "value": "-1000",
            "currency": {
              "symbol": "ATOM",
              "decimals": 6
            }
          }
        }
      ]
    }
  ],
  "total_count": 5,
  "next_offset": 5
}
```

## Request Example

```json
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/search/transactions' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "network_identifier": {
    "blockchain": "cosmos",
    "network": "mainnet"
  }
}'
```

```typescript
import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({
  network: Network.COSMOS_MAINNET,
});

const transactions = await cosmos.rpc.searchTransactions({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
});

// Log the retrieved transactions
console.log("Transactions:", transactions);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```
