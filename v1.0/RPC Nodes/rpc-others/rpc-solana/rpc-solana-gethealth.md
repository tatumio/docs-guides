---
title: "gethealth"
slug: "rpc-solana-gethealth"
excerpt: "Solana RPC"
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.getHealth()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getHealth` method is used to monitor the current health of the node. This method can be beneficial for maintenance and troubleshooting purposes. For instance, you may use this method to check the health status of your node periodically or to validate if a newly set up node is functioning correctly.

Please note that if one or more `--known-validator` arguments are provided to `solana-validator`, "ok" is returned when the node is within `HEALTH_CHECK_SLOT_DISTANCE` slots of the highest known validator; otherwise, an error is returned. If no known validators are provided, "ok" is always returned.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/QWJoKVb",
  "href": "https://codepen.io/tatum-devrel/pen/QWJoKVb",
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

If the node is healthy, it returns "ok". If the node is unhealthy, a JSON RPC error response is returned. The specifics of the error response are unstable and may change in the future.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getHealth"
}
```

### JSON-RPC Response Examples

- Healthy node response:

  ```json
  { "jsonrpc": "2.0", "result": "ok", "id": 1 }
  ```
- Unhealthy node response (generic):

  ```json
  {
    "jsonrpc": "2.0",
    "error": {
      "code": -32005,
      "message": "Node is unhealthy",
      "data": {}
    },
    "id": 1
  }
  ```
- Unhealthy node response (if additional information is available):

  ```json
  {
    "jsonrpc": "2.0",
    "error": {
      "code": -32005,
      "message": "Node is behind by 42 slots",
      "data": {
        "numSlotsBehind": 42
      }
    },
    "id": 1
  }
  ```
