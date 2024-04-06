---
title: "debug_storagerangeat"
slug: "rpc-base-debug_storagerangeat"
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

const result = await tatum.rpc.debugStorageRangeAt(
  "0x567421db30d23df893f4a4258828c82baf37c2c9fc09d9321bd86f4b16e115ba",
  1,
  "0x20F2221084ae06926E8bD042CeEF5dF33486b0b5",
  "0x0000000000000000000000000000000000000000000000000000000000000000",
  0
);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

`debug_storageRangeAt` is an RPC method that allows you to retrieve the contract storage range for a given block and address. This can be useful for developers and auditors who want to inspect the storage state of a specific contract at a particular point in time. This method can also help in debugging and identifying potential issues with contract storage, as well as understanding how storage evolves as transactions are executed.

### Parameters

The `debug_storageRangeAt` method accepts the following parameters:

- `blockHash`: The block hash for which the storage range should be retrieved. Example: `"0x567421db30d23df893f4a4258828c82baf37c2c9fc09d9321bd86f4b16e115ba"`
- `txIndex`: The transaction index within the specified block. Example: 1
- `address`: The contract address for which the storage range should be retrieved. Example: `"0x20F2221084ae06926E8bD042CeEF5dF33486b0b5"`
- `begin`: The beginning of the storage range. Example: `"0x0000000000000000000000000000000000000000000000000000000000000000"`
- `end`: The end of the storage range. Example: `1` (inclusive)

### Return Object

The `debug_storageRangeAt` method returns an object with the following fields:

- `storage`: An object that contains key-value pairs representing the contract storage, where the key is the storage slot and the value is the stored data. Example: `"0x00..01": "0x00..01"`
- `nextKey`: A key indicating the next storage slot if the requested range is too large, otherwise `null`. Example: `"0x00..02"` or `null`

{% hint style="info" %}
This method is available only on the full archive node.
{% endhint %}

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "storage": {
      "0x0000000000000000000000000000000000000000000000000000000000000001": "0x0000000000000000000000000000000000000000000000000000000000000001",
      "0x0000000000000000000000000000000000000000000000000000000000000002": "0x0000000000000000000000000000000000000000000000000000000000000002"
    },
    "nextKey": "0x0000000000000000000000000000000000000000000000000000000000000065"
  }
}
```
