---
title: "getbandwidthprices"
slug: "rpc-tron-getbandwidthprices"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const res = await tatum.rpc.getBandwidthPrices()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `getBandwidthPrices()` method is used to retrieve historical bandwidth unit prices on the TRON blockchain. Bandwidth is an essential resource in the TRON network used for performing transactions. This method will return all historical prices, where each unit price change is separated by a comma.

{% embed url="<https://codepen.io/tatum-devrel/pen/xxQeMNy"> %}

### Parameters

This method doesn't require any parameters.

### Return Object

- `prices`: A string that represents all historical bandwidth unit price information. Each unit price change is separated by a comma. Before the colon is the millisecond timestamp, and after the colon is the bandwidth unit price in sun.

### HTTP Request Example

```shell
{}
```

### HTTP Response Example

```json
{
  "prices": "1613713487000:100,1613799887000:200,1613886287000:150"
}
```

In this example, the first bandwidth unit price change was at timestamp `1613713487000` with a price of `100` sun, the second at timestamp `1613799887000` with a price of `200` sun, and so on.
