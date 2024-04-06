---
title: "eth_chainid"
slug: "rpc-haqq-eth_chainid"
excerpt: "Haqq  RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
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

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const id = await tatum.rpc.chainId()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `eth_chainId` method is an Haqq JSON-RPC method that allows developers to retrieve the currently configured chain ID of the Haqq network they are connected to. The chain ID is a unique identifier for different Haqq networks, such as Haqq Mainnet or various testnets.

This method is particularly useful when building applications that interact with multiple Haqq networks or need to verify the network to prevent replay attacks. By checking the chain ID, an application can ensure it is interacting with the intended network.

{% embed url="https://codepen.io/tatum-devrel/pen/NWEQVzo" %}

### Parameters

The `eth_chainId` method does not have any input parameters.

### Return Object

The return object contains a single field:

* **`chainId`**: The hexadecimal string representation of the chain ID.

### Example Request and Response

JSON-RPC request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_chainId",
  "params": []
}
```

JSON-RPC response:

````json
```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x2be3"
}
```
````

In this example, the returned chain ID is `0x2be3`, which corresponds to the Haqq Mainnet.
