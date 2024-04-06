---
title: "eth_getstorageat"
slug: "rpc-base-eth_getstorageat"
excerpt: "Base RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
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

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const response = await tatum.rpc.getStorageAt(
  "0x833589fcd6edb6e08f4c7c32d4f71b54bda02913",
  "0x0"
);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

`eth_getStorageAt` is an method that allows you to query the storage value of a contract at a given position. It can be used to inspect the internal state of a smart contract. This method is particularly useful for developers, auditors, and analysts who want to examine contract storage values for various purposes, such as debugging, verifying contract behavior, or analyzing data.

### Parameters

`eth_getStorageAt` accepts three parameters:

1. **`address`**: The address of the contract you want to query.
   - Example: `"0x833589fcd6edb6e08f4c7c32d4f71b54bda02913"`
2. **`position`**: The storage position (slot) you want to query.
   - Example: `"0x0"`
3. **`blockParameter`**: The block number, block hash, or one of the string literals (`"earliest"`, `"latest"` or `"pending"`), representing the point in the blockchain to query the storage value.
   - Example: `"latest"`

### Return Object

The return object is a single string value, representing the storage value at the given position in the contract.

- `result`: The storage value in a 32-byte (64 character) hexadecimal format.

#### Response Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x0000000000000000000000003abd6f64a422225e61e435bae41db12096106df7"
}
```
