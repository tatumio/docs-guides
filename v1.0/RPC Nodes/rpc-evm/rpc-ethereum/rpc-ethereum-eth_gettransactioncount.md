---
title: "eth_getTransactionCount"
slug: "rpc-ethereum-eth_gettransactioncount"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 08:50:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:39 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getTransactionCount` method is an Ethereum JSON-RPC method that retrieves the number of transactions sent from a given address. It is a useful method for developers who need to keep track of an account's nonce value to avoid transaction collisions or incorrect order of execution. The nonce value is essential for ensuring transaction uniqueness and preventing replay attacks.

## Usecase

Use cases for this method include:

- Determining the nonce value for a new transaction to be sent from a specific address
- Monitoring the number of transactions sent by an address to observe its activity
- Troubleshooting transaction issues and verifying if a transaction was submitted successfully

## Parameters

The `eth_getTransactionCount` method accepts two parameters:

- `address`:  The address whose transaction count will be retrieved.
  - Example: 0x742d35Cc6634C0532925a3b844Bc454e4438f44e
- `blockParameter `: A string indicating the block number or block state to consider when retrieving the transaction count.
  - Possible values: `"earliest"`, `"latest"`, `"pending"`, or a specific block number in hexadecimal format
  - Example: "latest"

## Returns

The method returns a single value:

| Name             | Description                                                                                 |
| :--------------- | :------------------------------------------------------------------------------------------ |
| transactionCount | A hexadecimal representation of the number of transactions sent from the specified address. |

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getTransactionCount",
  "params": [
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
    "latest"
  ]
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.getTransactionCount('0x742d35Cc6634C0532925a3b844Bc454e4438f44e', 'latest')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
