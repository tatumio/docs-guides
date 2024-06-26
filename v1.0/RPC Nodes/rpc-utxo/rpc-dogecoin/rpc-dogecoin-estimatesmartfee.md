---
title: "estimatesmartfee"
slug: "rpc-dogecoin-estimatesmartfee"
excerpt: "Dogecoin RPC"
hidden: false
metadata: 
  description: "Dogecoin RPC"
  image: []
  keywords: "dogecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:01 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Dogecoin>({network: Network.DOGECOIN})

const result = await tatum.rpc.estimateSmartFee(20)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `estimatesmartfee` method provides an estimated fee rate (in DOGE/kB) for a transaction to be confirmed within a certain number of blocks. The estimation is based on recent transactions in the Dogecoin network.

This method can be useful for users or applications trying to decide on an appropriate fee for their transactions, based on the desired confirmation speed.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Martin-Zemanek/pen/MWzxpEK",
  "href": "https://codepen.io/Martin-Zemanek/pen/MWzxpEK",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `estimatesmartfee` method accepts the following parameters:

- `conf_target`: An integer representing the number of blocks within which the transaction should be confirmed.
- `estimate_mode` _(optional)_: A string that determines the estimation mode. Possible values are "UNSET", "ECONOMICAL", and "CONSERVATIVE". Default is "CONSERVATIVE".

### Return Object

The `estimatesmartfee` method returns an object containing the following fields:

- `feerate`: A decimal number representing the estimated fee rate in DOGE/kB.
- `blocks`: An integer representing the number of blocks within which the transaction is expected to be confirmed.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "method": "estimatesmartfee",
  "params": [20],
  "id": 1
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": {
        "feerate": 0.00017258,
        "blocks": 20
    },
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
