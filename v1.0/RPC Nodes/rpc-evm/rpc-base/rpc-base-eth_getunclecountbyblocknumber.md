---
title: "eth_getunclecountbyblocknumber"
slug: "rpc-base-eth_getunclecountbyblocknumber"
excerpt: "Base RPC"
hidden: false
metadata: 
  description: "Base RPC"
  image: []
  keywords: "base, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Base, Network } from "@tatumio/tatum";

const tatum = await TatumSDK.init<Base>({ network: Network.BASE });

const result = await tatum.rpc.getUncleCountByBlockNumber(15537345);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

The `eth_getUncleCountByBlockHash` method returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the network and to analyse the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralisation of the network. The inclusion of uncles helps prevent centralisation and ensures the mining process remains competitive.

{% embed url="<https://codepen.io/Jan-Musil-the-lessful/pen/vYQPXer"> %}

### Parameters

The `eth_getUncleCountByBlockHash` method takes one parameter:

- `blockNumber`: The number of the block for which you want to get the uncle count.
  - Example value: 15537345

### Return Object

The return object for this method is a hex-encoded integer representing the number of uncles in the specified block.

- Example value: `"0x1"` (1 uncle)

### Request and Response Examples

Here is an example request and response for the `eth_getUncleCountByBlockNumber` method:

**Request:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getUncleCountByBlockNumber",
  "params": ["0xED14C1"]
}
```

**Response:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x1"
}
```

In this example, the request asks for the number of uncles in the block with the specified hash. The response indicates that there is one uncle in the block.

\\
