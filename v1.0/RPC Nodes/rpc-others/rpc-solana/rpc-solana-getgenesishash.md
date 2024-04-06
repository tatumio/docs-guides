---
title: "getgenesishash"
slug: "rpc-solana-getgenesishash"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

{% code overflow="wrap" lineNumbers="true" %}

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getGenesisHash()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `getGenesisHash` method returns the genesis hash of the Solana network. The genesis hash is an important piece of information in the blockchain world. It is the initial block or the very first block in a blockchain. The genesis hash can be used for various use cases such as to verify the integrity of data, as a reference point in the blockchain, and for debugging purposes.

{% embed url="<https://codepen.io/tatum-devrel/pen/qBQvaVV"> %}

### Parameters

None

### Return Object

- Returns a string, which is a Hash as base-58 encoded string.

### JSON-RPC Request Example

```json
{
  "jsonrpc":"2.0",
  "id":1, 
  "method":"getGenesisHash"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": "GH7ome3EiwEr7tu9JuTh2dpYWBJK3z69Xm1ZE3MEE6JC",
  "id": 1
}
```
