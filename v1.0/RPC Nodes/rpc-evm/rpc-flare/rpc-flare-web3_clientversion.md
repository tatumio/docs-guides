---
title: "web3_clientversion"
slug: "rpc-flare-web3_clientversion"
excerpt: "Flare  RPC"
hidden: false
metadata: 
  description: "Flare RPC"
  image: []
  keywords: "flare, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Flare, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Flare>({network: Network.FLARE})

const version = await tatum.rpc.clientVersion()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`web3_clientVersion` is a method of the JSON-RPC API that allows the client to retrieve the current version of the client software being used by the node.

This method is read-only and does not require authentication. The `web3_clientVersion` method can be used by developers to confirm the version of the client software they are using and ensure that it is compatible with their application.

### Parameters

This method has no parameters. It only retrieves the current version of the client software.

### Return Object

The `web3_clientVersion` method returns a string representing the version of the client software being used. The string includes the client name, version number, and build information.

- `String` - Version string of the client software being used.

### Example Request

#### JSON Request

```json
{
  "jsonrpc": "2.0",
  "method": "web3_clientVersion",
  "params": [],
  "id": 1
}
```

### Example Response

#### JSON Response

```json
{
    "jsonrpc": "2.0",
    "id": 67,
    "result": "v0.8.15"
}
```

In the above example, the client software being used is in version 0.8.18..
