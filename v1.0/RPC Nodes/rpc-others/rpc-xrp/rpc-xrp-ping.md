---
title: "ping"
slug: "rpc-xrp-ping"
excerpt: "XRP RPC"
hidden: false
metadata: 
  description: "XRP RPC"
  image: []
  keywords: "xrp, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:43 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Xrp, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Xrp>({network: Network.XRP})

const res = await tatum.rpc.ping()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

### Overview

The `ping` method is a simple RPC method provided by the Ripple (XRP) blockchain, used primarily to check the connection status and latency to the XRP blockchain node. It's a useful tool in debugging and network troubleshooting scenarios, as it provides an easy way to verify the connection and round-trip time between the client and the server.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/oNQOJdw",
  "href": "https://codepen.io/tatum-devrel/pen/oNQOJdw",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `ping` method accepts no parameters.

### Return Object

The `ping` method returns a simple object with the following field:

- `status`: The status of the request, typically "success". The presence of this field in the response indicates a successful round trip.

The client can measure the round-trip time from the request to the response as latency.

### JSON-RPC Request Example

```json
{
    "method": "ping",
    "params": [
        {}
    ]
}
```

### JSON-RPC Response Example

```json
{
    "result": {
        "status": "success"
    }
}
```

This response signifies a successful connection to the XRP node. The time it takes to receive this response can be used to measure network latency.
