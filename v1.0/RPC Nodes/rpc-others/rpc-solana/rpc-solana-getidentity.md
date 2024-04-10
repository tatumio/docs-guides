---
title: "getidentity"
slug: "rpc-solana-getidentity"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getIdentity()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getIdentity` method is used to retrieve the identity pubkey for the current node. This pubkey represents a unique identifier for the node in the Solana network.

Use cases for this method might include retrieving the identity of a node for tracking or monitoring purposes, or validating the identity of a node in scenarios where only certain nodes are trusted for certain operations.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/PoxLGdg",
  "href": "https://codepen.io/tatum-devrel/pen/PoxLGdg",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

This method does not require any parameters.

### Return Object

The result field will be a JSON object with the following fields:

- `identity`: The identity pubkey of the current node as a base-58 encoded string.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getIdentity"
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "identity": "2r1F4iWqVcb8M1DbAjQuFpebkQHY9hcVU4WuW2DJBppN"
  },
  "id": 1
}
```
