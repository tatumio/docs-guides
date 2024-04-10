---
title: "getaccountbalance"
slug: "rpc-tron-getaccountbalance"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network, AccountIdentifier, BlockIdentifier, VisibleOption } from '@tatumio/tatum'
import BigNumber from "bignumber.js";

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const accountIdentifier: AccountIdentifier = {
  address: "TLLM21wteSPs4hKjbxgmH1L6poyMjeTbHm"
}

const blockIdentifier: BlockIdentifier = {
  hash: "0000000000010c4a732d1e215e87466271e425c86945783c3d3f122bfa5affd9",
  number: new BigNumber(68682)
}

const res = await tatum.rpc.getAccountBalance(accountIdentifier, blockIdentifier, {
  visible: true
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getAccountBalance` method is used to retrieve an account's balance at a specific block on the TRON network. This is particularly useful when you need to audit the state of an account at a particular point in time or to verify a transaction's execution result against the blockchain state at a given block.

### Parameters

- `accountIdentifier` (AccountIdentifier): An object that represents the account identifier which includes:
  - `address` (string): The account address.
- `blockIdentifier` (BlockIdentifier): An object that represents the block identifier which includes:
  - `hash` (string): The block hash.
  - `number` (number): The block number.
- `options` (object, optional): This optional parameter contains the following properties:
  - `visible` (boolean, optional): Optional parameter to specify whether the address is in base58 format.

### Return Object

The method returns a JSON object that contains the following properties:

- `balance` (integer): The balance of the account.
- `block_identifier.hash` (string): The block hash.
- `block_identifier.number` (integer): The block number.

### HTTP Request Example

```json
{
  "account_identifier": {
    "address": "TLLM21wteSPs4hKjbxgmH1L6poyMjeTbHm"
  },
  "block_identifier": {
    "hash": "0000000000010c4a732d1e215e87466271e425c86945783c3d3f122bfa5affd9",
    "number": 68682
  },
  "visible": true
}
```

### HTTP Response ExampleThe response will be a JSON object representing the balance and block information:

```json
{
  "balance": 100000,
  "block_identifier": {
    "hash": "0000000000010c4a732d1e215e87466271e425c86945783c3d3f122bfa5affd9",
    "number": 68682
  }
}
```
