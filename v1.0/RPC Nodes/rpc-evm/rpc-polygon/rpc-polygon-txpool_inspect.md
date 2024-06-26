---
title: "txpool_inspect"
slug: "rpc-polygon-txpool_inspect"
excerpt: "Polygon RPC"
hidden: false
metadata: 
  description: "Polygon RPC"
  image: []
  keywords: "polygon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Polygon, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Polygon>({network: Network.POLYGON})

const inspect = await tatum.rpc.txPoolInspect()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `txpool_inspect` method is a JSON-RPC method used to inspect the current transaction pool of a running Polygon node. The method allows you to view all pending transactions and their details, including transaction hashes, gas prices, and transaction data. This method is useful for developers who want to monitor the status of pending transactions or debug transaction-related issues.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/XWyOoQz",
  "href": "https://codepen.io/tatum-devrel/pen/XWyOoQz",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `txpool_inspect` method takes one optional parameter:

- **`include`**: A string specifying the type of transactions to include in the response. Possible values are **`pending`** (default) and **`queued`**.

### Return Object

The `txpool_inspect` method returns an object with the following fields:

- **`pending`**: An array of transaction objects, with textual data
- **`queued`**: An array of transaction objects, with textual data

## Example Request:

```json
{
  "jsonrpc": "2.0",
  "method": "txpool_inspect",
  "params": [
    "pending"
  ],
  "id": 1
}
```

## Example Response:

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "pending": {
            "0x01d3B93AaADE8A4066DAaBc8fd8482173A6aD120": {
                "197": "0x4f023eB8C6BC3116E35B67E03bf2C17f2e4f7e7e: 0 wei + 30000000 gas × 23918871 wei"
            }
        },
        "queued": {
            "0x03321406635a04D37Cf9211F2ea3AFc83a87e777": {
                "5096281": "0x77b1C86Ab0aa9066803eD567e1F00973976638F6: 49999988041886240 wei + 21000 gas × 53000000000 wei",
                "8308536": "0x77b1C86Ab0aa9066803eD567e1F00973976638F6: 100000000000000000 wei + 21000 gas × 53000000000 wei",
                "231211221": "0x77b1C86Ab0aa9066803eD567e1F00973976638F6: 1000000000000000 wei + 21000 gas × 11958113760 wei"
            }
        }
    }
}
```

\\
