---
title: "listnodes"
slug: "rpc-tron-listnodes"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:43 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

You can interact with the TRON blockchain by using the `listNodes` method in the Tatum SDK. Here's an example:

{% code overflow="wrap" lineNumbers="true" %}

```typescript
// Import necessary components from the SDK
import { TatumSDK, Tron, Network } from '@tatumio/tatum'

// Initialize the SDK for the TRON network
const tatum = await TatumSDK.init<Tron>({ network: Network.TRON })

// Use the RPC method
const nodeList = await tatum.rpc.listNodes()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `listNodes` method is an RPC method provided by the TRON blockchain. It returns a list of nodes connected to the TRON network, including their host addresses and ports. This information can be used for various purposes, such as network analysis, node performance assessment, or setting up a new node connection.

{% embed url="<https://codepen.io/tatum-devrel/pen/WNYWPWo"> %}

### Parameters

The `listNodes` method does not accept any parameters.

### Return Object

- `nodes` (array)
  - `address` (object)
    - `host` (string): The host address of the node.
    - `port` (integer): The port number of the node.

### HTTP Request Example

```bash
{}
```

### HTTP Response Example

```json
{
  "nodes": [
    {
      "address": {
        "host": "34372e38392e3138362e3334",
        "port": 16666
      }
    },
    {
      "address": {
        "host": "35322e31312e34322e3439",
        "port": 16666
      }
    },
    {
      "address": {
        "host": "34372e39302e3230372e323237",
        "port": 16666
      }
    },
    {
      "address": {
        "host": "34372e39302e3230362e313439",
        "port": 16666
      }
    }
  ]
}
```
