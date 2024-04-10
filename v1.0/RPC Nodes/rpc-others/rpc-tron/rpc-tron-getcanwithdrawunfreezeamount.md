---
title: "getcanwithdrawunfreezeamount"
slug: "rpc-tron-getcanwithdrawunfreezeamount"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:46 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
import { TatumSDK, Tron, Network } from '@tatumcom/js';

const tatum = await TatumSDK.init<Tron>({ network: Network.TRON });

const res = await tatum.rpc.getCanWithdrawUnfreezeAmount('TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g', {
  timestamp: 1667977444000,
  visible: true,
});

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getCanWithdrawUnfreezeAmount` method allows you to retrieve the withdrawable balance for a specified owner address at a specific timestamp. This method is primarily used in the Stake 2.0 protocol on the TRON blockchain.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/BaGEMON",
  "href": "https://codepen.io/tatum-devrel/pen/BaGEMON",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

Use Cases:

- Calculating the available balance that can be withdrawn by an owner address in the Stake 2.0 protocol.
- Providing real-time balance information to users or applications.

### Parameters

- `ownerAddress` (string): The owner address for which the withdrawable balance needs to be retrieved. (Default: hexString)
- `options` (object, optional): This optional parameter contains the following properties:
  - `timestamp` (integer, optional): The query cutoff timestamp in milliseconds.
  - `visible` (boolean, optional):  parameter to indicate whether the address is in base58 format.

### Return Object

The `getCanWithdrawUnfreezeAmount` method returns the following object:

- `amount`: The withdrawable balance in TRX, where the unit is sun.

### HTTP Request Example

```json
{
  "owner_address": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
  "timestamp": 1667977444000,
  "visible": true
}
```

### HTTP Response Example

```json
{
  "amount": 1000000
}
```
