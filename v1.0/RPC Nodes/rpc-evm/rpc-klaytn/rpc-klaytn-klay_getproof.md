---
title: "klay_getproof"
slug: "rpc-klaytn-klay_getproof"
excerpt: "Klaytn RPC"
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const result = await tatum.rpc.getProof("0x898f2afc07924f5a4f9612449e4c4f8eca527515",
["0x0000000000000000000000000000000000000000000000000000000000000000"],
"latest")
    
await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `klay_getProof` is a JSON-RPC method that retrieves the Merkle-Patricia proof for an account, storage key-value pairs, and account transaction count. It allows developers to verify the state of an account or storage value at a specific block without needing the entire state trie. This method is particularly useful for light clients or off-chain applications that require proof of an account's state or specific storage values.

### Parameters

1. **`address`** - `Data`, 20 Bytes
   - The address of the account.
   - Example: `"0xBB52B2B91488d60eFb6848bBadd000005A511E5C"`
2. **`keys`** - `Array` of `Data`
   - An array of storage keys for which the proof should be generated.
   - Example: `["0x0000000000000000000000000000000000000000000000000000000000000000"]`
3. **`blockNumber`** - `Quantity` or `String`
   - The block number for which the proof should be generated.
   - Example: `"0x1"` or `"latest"`

### Return Object

The method returns an object containing the following fields:

1. **`accountProof`** - `Array` of `Data`
   - The serialized Merkle-Patricia proof for the account.
2. **`balance`** - `Quantity`
   - The balance of the account at the specified block.
3. **`codeHash`** - `Data`, 32 Bytes
   - The hash of the code for the account at the specified block.
4. **`nonce`** - `Quantity`
   - The transaction count of the account at the specified block.
5. **`storageProof`** - `Array` of `Object`
   - An array of storage proof objects, one for each requested key, containing the following fields:
     - `key` - `Data`, 32 Bytes: The storage key.
     - `value` - `Quantity`: The storage value.
     - `proof` - `Array` of `Data`: The serialized Merkle-Patricia proof for the key-value pair.

### JSON-RPC Request and Response Examples

_Request_:

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "klay_getProof",
  "params": [
    "0xBB52B2B91488d60eFb6848bBadd000005A511E5C",
    [
      "0x0000000000000000000000000000000000000000000000000000000000000000"
    ],
    "latest"
  ]
}
```

_Response_:

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "accountProof": [
      "0x...",
      "0x...",
      "0x..."
    ],
    "balance": "0xde0b6b3a7640000",
    "codeHash": "0x...",
    "nonce": "0x1",
    "storageProof": [
      {
        "key": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "value": "0xde0b6b3a7640000",
        "proof": [
          "0x...",
          "0x...",
          "0x..."
        ]
      }
    ]
  }
}
```
