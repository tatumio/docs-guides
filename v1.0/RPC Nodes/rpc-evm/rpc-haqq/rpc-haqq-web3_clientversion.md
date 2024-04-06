---
title: "web3_clientversion"
slug: "rpc-haqq-web3_clientversion"
excerpt: "Haqq  RPC"
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const version = await tatum.rpc.clientVersion()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`web3_clientVersion` is a method of the Haqq JSON-RPC API that allows the client to retrieve the current version of the Haqq client software being used by the node.

This method is read-only and does not require authentication. The `web3_clientVersion` method can be used by developers to confirm the version of the Haqq client software they are using and ensure that it is compatible with their application.

{% embed url="<https://codepen.io/tatum-devrel/pen/eYQqajp"> %}

### Parameters

This method has no parameters. It only retrieves the current version of the Haqq client software.

### Return Object

The `web3_clientVersion` method returns a string representing the version of the Haqq client software being used. The string includes the client name, version number, and build information.

- `String` - Version string of the Haqq client software being used.

### Example Request

#### JSON Request

```json
{
  "jsonrpc": "2.0",
  "method": "web3_clientVersion",
  "params": [],
  "id": 67
}
```

### Example Response

#### JSON Response

```json
{
    "jsonrpc": "2.0",
    "id": 67,
    "result": "Version dev ()\nCompiled at  using Go go1.20.6 (amd64)"
}
```
