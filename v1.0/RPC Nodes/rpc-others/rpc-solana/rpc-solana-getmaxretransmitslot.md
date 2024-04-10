---
title: "getmaxretransmitslot"
slug: "rpc-solana-getmaxretransmitslot"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It



```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getMaxRetransmitSlot()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getMaxRetransmitSlot` method returns the highest slot number seen from the retransmit stage. This can be useful for monitoring the progress of the network or for determining the highest slot number that has been processed by a specific node.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Night-Shift-Dev/pen/abQZJGR",
  "href": "https://codepen.io/Night-Shift-Dev/pen/abQZJGR",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

None

### Return Object

The method returns a value representing the highest slot number observed in the retransmit stage.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getMaxRetransmitSlot"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": 1234,
  "id": 1
}
```
