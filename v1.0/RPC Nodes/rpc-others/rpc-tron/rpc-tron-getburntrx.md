---
title: "getburntrx"
slug: "rpc-tron-getburntrx"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:45 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum';

const tatum = await TatumSDK.init<Tron>({network: Network.TRON});

const res = await tatum.rpc.getBurnTRX();

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `getBurnTRX()` RPC method allows to query the amount of TRX burned due to on-chain transaction fees since the No. 54 Committee Proposal took effect.

Before the No. 54 Committee Proposal takes effect, the destruction of transaction fees is completed by transferring to the black hole address TLsV52sRDL79HXGGm9yzwKibb6BeruhUzy. After the No. 54 committee proposal takes effect, it will no longer be transferred to the black hole address, but will be directly recorded in the node database.

Use cases of this method include monitoring the total amount of TRX burned due to transaction fees, which can be useful for data analysis and transparency purposes.

{% embed url="<https://codepen.io/tatum-devrel/pen/VwVNgOO"> %}

### Parameters

The `getBurnTRX()` RPC method does not require any parameters.

### Return Object

- `burnTrxAmount`: This is the amount of TRX burned due to on-chain transaction fees. The amount is returned in sun (1 TRX = 1,000,000 sun).

### HTTP Request Example

```bash
{}
```

### HTTP Response Example

```json
{
    "burnTrxAmount": 200
}
```

Note that the `burnTrxAmount` is returned as an integer in sun.

***
