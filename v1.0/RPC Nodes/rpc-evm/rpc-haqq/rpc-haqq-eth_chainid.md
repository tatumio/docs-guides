---
title: "eth_chainid"
slug: "rpc-haqq-eth_chainid"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:00 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const id = await tatum.rpc.chainId()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `eth_chainId` method is an Haqq JSON-RPC method that allows developers to retrieve the currently configured chain ID of the Haqq network they are connected to. The chain ID is a unique identifier for different Haqq networks, such as Haqq Mainnet or various testnets.

This method is particularly useful when building applications that interact with multiple Haqq networks or need to verify the network to prevent replay attacks. By checking the chain ID, an application can ensure it is interacting with the intended network.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/NWEQVzo",
  "href": "https://codepen.io/tatum-devrel/pen/NWEQVzo",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `eth_chainId` method does not have any input parameters.

### Return Object

The return object contains a single field:

- **`chainId`**: The hexadecimal string representation of the chain ID.

### Example Request and Response

JSON-RPC request:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_chainId",
  "params": []
}
```

JSON-RPC response:

````json
```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x2be3"
}
```
````

In this example, the returned chain ID is `0x2be3`, which corresponds to the Haqq Mainnet.
