---
title: "getavailableunfreezecount"
slug: "rpc-tron-getavailableunfreezecount"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:44 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const res = await tatum.rpc.getAvailableUnfreezeCount('TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g', {
  visible: true,
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getAvailableUnfreezeCount` method is used to retrieve the remaining times of executing the unstake operation in Stake 2.0 on the TRON blockchain. Stake 2.0 supports unstaking in batches, but it imposes a limit of 32 unstake operations that can be executed simultaneously. This means that when a user initiates the first unstake operation, they can only initiate another 31 unstake operations until the TRX of the first unstaking arrives and is ready to be withdrawn to their account. This limitation is in place to prevent malicious attacks.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/JjeVxBB",
  "href": "https://codepen.io/tatum-devrel/pen/JjeVxBB",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `ownerAddress` (string): The owner address for which to retrieve the remaining times of available unstaking. Default is in hexadecimal format.
- `options` (object, optional): This optional parameter contains the following properties:
  - `visible` (boolean, optional): Whether the address is in base58 format.

### Return Object

- `count`: The remaining times of available unstaking.

### HTTP Request Example

```json
{
  "owner_address": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
  "visible": true
}
```

### HTTP Response Example

```json
{
  "count": 32
}
```
