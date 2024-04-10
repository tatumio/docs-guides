---
title: "eth_gasprice"
slug: "rpc-polygon-eth_gasprice"
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

const gasPrice = await tatum.rpc.gasPrice()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_gasPrice` method is a Polygon JSON-RPC method used to estimate the average gas price required for transactions in the Polygon network. This method provides a suggestion for the gas price to be used in a transaction to increase the likelihood of it being mined and included in a block in a reasonable amount of time. The `eth_gasPrice` method is particularly useful for developers and users who want to create and send transactions, as it helps them estimate the appropriate gas price to ensure timely processing.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/vYQbbBM",
  "href": "https://codepen.io/tatum-devrel/pen/vYQbbBM",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `eth_gasPrice` method does not require any parameters. However, the transaction object should include the following fields:

- **`from`** (optional): The sender's Polygon address. Example: `"0x742d35Cc6634C0532925a3b844Bc454e4438f44e"`
- **`to`** (optional): The recipient's Polygon address. Example: `"0x5aeda56215b167893e80b4fe645ba6d5bab767de"`
- **`gas`** (optional): The maximum amount of gas to be used for the transaction. Example: `"0x76c0"`
- **`gasPrice`** (optional): The gas price in wei for each unit of gas. Example: `"0x9184e72a000"`
- **`value`** (optional): The amount of ether to be sent in the transaction in wei. Example: `"0x9184e72a"`
- **`data`** (optional): The input data associated with the transaction, typically used for contract calls. Example: `"0xd46e8dd67c5d32be8058bb8eb970870f072445675"`
- `nonce` (optional): The transaction count for the sender's address. Example: `"0x1"`

### Return Value

The `eth_gasPrice` method returns a single value as a hexadecimal string:

- `gasPrice`: The estimated average gas price in wei. Example: `"0x4a817c800"`

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_gasPrice",
  "params": []
}
```

#### Response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x4a817c800"
}
```

By using the `eth_gasPrice` method, developers and users can estimate the appropriate gas price for their transactions, improving the overall user experience and ensuring that their transactions are processed in a timely manner.
