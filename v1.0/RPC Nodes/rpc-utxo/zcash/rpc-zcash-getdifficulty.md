---
title: "getdifficulty"
slug: "rpc-zcash-getdifficulty"
excerpt: "Zcash RPC"
hidden: false
metadata: 
  description: "Zcash RPC"
  image: []
  keywords: "zcash, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---



### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, ZCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<ZCash>({network: Network.ZCASH})

const result = await tatum.rpc.getDifficulty()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`getdifficulty` is a method that returns the current mining difficulty. The mining difficulty is a measure of how difficult it is to find a new block compared to the easiest it can ever be. This method can be used to monitor the mining difficulty, which adjusts every 2016 blocks to maintain a consistent block creation rate of approximately 10 minutes per block.

### Parameters

This method does not require any parameters.

### Return Object

A return object is a floating-point number that represents the current mining difficulty.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "getdifficulty",
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": 48712405953118.43,
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
