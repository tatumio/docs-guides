---
title: "eth_getunclecountbyblockhash"
slug: "rpc-haqq-eth_getunclecountbyblockhash"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:24:25 GMT+0000 (Coordinated Universal Time)"
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

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const result = await tatum.rpc.getUncleCountByBlockHash('0x300e4057498875ef62a7632c78077d9fa79265e484415d337d1f529ca4660ee6')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

The `eth_getUncleCountByBlockHash` method is an Haqq JSON-RPC method that returns the number of uncles in a specified block by its hash. This method can be useful for gathering information about the performance of the Haqq network and to analyze the security of the blockchain.

Uncles are blocks that are not included in the main blockchain but are still valid, and they contribute to the overall security and decentralization of the Haqq network. The inclusion of uncles helps prevent centralization and ensures the mining process remains competitive.

{% embed url="<https://codepen.io/Jan-Musil-the-lessful/pen/xxQMNxz?editors=1111"> %}

### Parameters

The `eth_getUncleCountByBlockHash` method takes one parameter:

- `blockHash`: The hash of the block for which you want to get the uncle count.
  - Example value: `"0x3a3e528dcd6e05a614c9241b0a9296db961fa6a92e05af9f6c0d7d2f6bc92f7a"`

### Return Object

The return object for this method is a hex-encoded integer representing the number of uncles in the specified block.

- Example value: `"0x1"` (1 uncle)

### JSON-RPC Request and Response Examples

Here is an example JSON-RPC request and response for the `eth_getUncleCountByBlockHash` method:

**Request:**

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getUncleCountByBlockHash",
  "params": [
    "0x3a3e528dcd6e05a614c9241b0a9296db961fa6a92e05af9f6c0d7d2f6bc92f7a"
  ]
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

In this example, the JSON-RPC request asks for the number of uncles in the block with the specified hash. The response indicates that there is one uncle in the block.
