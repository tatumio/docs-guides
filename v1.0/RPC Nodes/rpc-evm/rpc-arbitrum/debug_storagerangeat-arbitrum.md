---
title: "debug_storageRangeAt (Arbitrum)"
slug: "debug_storagerangeat-arbitrum"
excerpt: "Arbitrum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "arbitrum, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 15:06:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 27 2024 15:12:11 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

## Overview

`debug_storageRangeAt` is an RPC method any change that allows you to retrieve the contract storage range for a given block and address. This can be useful for developers and auditors who want to inspect the storage state of a specific contract at a particular point in time. This method can also help in debugging and identifying potential issues with contract storage, as well as understanding how storage evolves as transactions are executed.

## Parameters

| Name                  | Type          | Required | Description                                                                         |
| :-------------------- | :------------ | :------- | :---------------------------------------------------------------------------------- |
| blockHash/blockNumber | string/object | yes      | The block hash in string format or block number as hexadecimal in the object format |
| txIndex               | integer       | yes      | The transaction index for the point in which we want the list of accounts           |
| address               | string        | yes      | The contract address                                                                |
| startKey              | string        | yes      | The offset (hash of storage key)                                                    |
| limit                 | string        | yes      | The number of storage entries to return                                             |

## Returns

- **Storage** - An object with hash values, and for each of them the key and value it represents.
  - **hash** - The hash value.
    - **key** - The key associated with the hash.
    - **value** - The value associated with the hash.
- **nextkey** - The hash of next key if further storage in range. Otherwise, not included.

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "jsonrpc":"2.0",
    "method":"debug_storageRangeAt",
    "params":[
        "0xe9793319714333112d41473d33bc06556b6d32d347517b782eb1cdaec296a20b",
        5,
        "0xdAC17F958D2ee523a2206206994597C13D831ec7",
        "0x00000000000000000000000000000000",
        2
    ],
    "id":1
}'
```
```javascript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.debugStorageRangeAt(
'0x48dfcf43404dffdb3b93a0b0d9982b642b221187bc3ed5c023bdab6c0e863e3d',
1, '0xa41d19F4258a388c639B7CcD938FCE3fb7D05e86', "0x0000000000000000000000000000000000000000000000000000000000000000", 1)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
