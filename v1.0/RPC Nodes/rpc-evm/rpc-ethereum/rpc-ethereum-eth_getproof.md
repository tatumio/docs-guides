---
title: "eth_getProof"
slug: "rpc-ethereum-eth_getproof"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 08:01:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 07:56:49 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getProof` is an Ethereum JSON-RPC method that retrieves the Merkle-Patricia proof for an account, storage key-value pairs, and account transaction count. It allows developers to verify the state of an account or storage value at a specific block without needing the entire Ethereum state trie. This method is particularly useful for light clients or off-chain applications that require proof of an account's state or specific storage values.

## Parameters

The` eth_getProof` requieres following parameters: :

- `address`: Data, 20 Bytes
  - The address of the account.
  - Example: "fromBlock": "0x1"
- `keys`: Array of Data
  - An array of storage keys for which the proof should be generated.
  - Example: ["0x0000000000000000000000000000000000000000000000000000000000000000"]
- `blockNumber`: Quantity or String
  - The block number for which the proof should be generated.
  - Example: "0x1" or "latest"

## Returns

TThe eth_getProof method returns an object, that contains the following fields:

[block:parameters]
{
  "data": {
    "h-0": "Name",
    "h-1": "Description",
    "h-2": "Type",
    "0-0": "accountProof",
    "0-1": "The serialized Merkle-Patricia proof for the account.",
    "0-2": "Array of Data",
    "1-0": "balance",
    "1-1": "The balance of the account at the specified block.",
    "1-2": "Quantity",
    "2-0": "codeHash",
    "2-1": "The hash of the code for the account at the specified block.",
    "2-2": "Data, 32 Bytes",
    "3-0": "nonce",
    "3-1": "The transaction count of the account at the specified block.",
    "3-2": "Quantity",
    "4-0": "storageProof",
    "4-1": "An array of storage proof objects, one for each requested key, containing the following fields:  \n`key` - Data, 32 Bytes: The storage key.  \n`value` - Quantity: The storage value.  \n`proof `- Array of Data: The serialized Merkle-Patricia proof for the key-value pair.",
    "4-2": "Array of Object"
  },
  "cols": 3,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getProof",
  "params": [
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
    [
      "0x0000000000000000000000000000000000000000000000000000000000000000"
    ],
    "latest"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.getProof("0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
    ["0x0000000000000000000000000000000000000000000000000000000000000000"],
    "latest")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
