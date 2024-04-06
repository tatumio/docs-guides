---
title: "eth_getStorageAt"
slug: "rpc-ethereum-eth_getstorageat"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 08:28:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:41 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getStorageAt` is an Ethereum JSON-RPC method that allows you to query the storage value of a contract at a given position. It can be used to inspect the internal state of a smart contract. This method is particularly useful for developers, auditors, and analysts who want to examine contract storage values for various purposes, such as debugging, verifying contract behavior, or analyzing data.

## Parameters

The` eth_getStorageAt` accepts following parameters: :

- `address`: The address of the contract you want to query.
  - Example: "0x742d35Cc6634C0532925a3b844Bc454e4438f44e"
- `position`: The storage position (slot) you want to query.
  - Example: "0x0"
- `blockParameter`: The block number, block hash, or one of the string literals (`"earliest"`,`"latest"`or `"pending"`), representing the point in the blockchain to query the storage value.
  - Example: `"latest"`

## Returns

The return object is a single string value, representing the storage value at the given position in the contract.

| Name   | Description                                                       |
| :----- | :---------------------------------------------------------------- |
| result | The storage value in a 32-byte (64 character) hexadecimal format. |

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getStorageAt",
  "params": [
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
    "0x0",
    "latest"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const response = await tatum.rpc.getStorageAt('0x742d35Cc6634C0532925a3b844Bc454e4438f44e', '0x0')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
