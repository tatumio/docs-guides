---
title: "eth_getproof"
slug: "rpc-flare-eth_getproof"
excerpt: "Flare  RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Flare RPC"
  image: []
  keywords: "flare, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

{% tabs %}
{% tab title="TypeScript/JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Flare, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Flare>({network: Network.FLARE})

const result = await tatum.rpc.getProof("0xa41d19F4258a388c639B7CcD938FCE3fb7D05e86",
    ["0x0000000000000000000000000000000000000000000000000000000000000000"],
    "latest")
    
await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `eth_getProof` is an JSON-RPC method that retrieves the Merkle-Patricia proof for an account, storage key-value pairs, and account transaction count. It allows developers to verify the state of an account or storage value at a specific block without needing the entire state trie. This method is particularly useful for light clients or off-chain applications that require proof of an account's state or specific storage values.

### Parameters

1. **`address`** - `Data`, 20 Bytes
   * The address of the account.
   * Example: `"0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
2. **`keys`** - `Array` of `Data`
   * An array of storage keys for which the proof should be generated.
   * Example: `["0x0000000000000000000000000000000000000000000000000000000000000000"]`
3. **`blockNumber`** - `Quantity` or `String`
   * The block number for which the proof should be generated.
   * Example: `"0x1"` or `"latest"`

### Return Object

The method returns an object containing the following fields:

1. **`accountProof`** - `Array` of `Data`
   * The serialized Merkle-Patricia proof for the account.
2. **`balance`** - `Quantity`
   * The balance of the account at the specified block.
3. **`codeHash`** - `Data`, 32 Bytes
   * The hash of the code for the account at the specified block.
4. **`nonce`** - `Quantity`
   * The transaction count of the account at the specified block.
5. **`storageProof`** - `Array` of `Object`
   * An array of storage proof objects, one for each requested key, containing the following fields:
     * `key` - `Data`, 32 Bytes: The storage key.
     * `value` - `Quantity`: The storage value.
     * `proof` - `Array` of `Data`: The serialized Merkle-Patricia proof for the key-value pair.

### JSON-RPC Request and Response Examples

_Request_:

```json
{
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
