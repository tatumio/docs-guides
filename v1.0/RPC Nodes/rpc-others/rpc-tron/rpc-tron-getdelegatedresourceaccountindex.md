---
title: "getdelegatedresourceaccountindex"
slug: "rpc-tron-getdelegatedresourceaccountindex"
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

const res = await tatum.rpc.getDelegatedResourceAccountIndex('TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g', {
  visible: true,
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getDelegatedResourceAccountIndex` is a method provided by TRON RPC allowing you to query the resource delegation by an account during stake1.0 phase. Essentially, this allows you to list all addresses that have delegated resources to a specific account.

{% embed url="<https://codepen.io/tatum-devrel/pen/vYQMbrM"> %}

### Parameters

- `value` (string):  Address, default hexString.
- `options` (object, optional): This optional parameter contains the following properties:
  - `visible` (boolean, optional) - Whether the address is in base58 format. 

### Return Object

- `account` (string) - account address.
- `fromAccounts` (string\[]) - A list of account addresses which delegate resource to this account.
- `toAccounts` (string\[]) - A list of account addresses which receive resources delegated by this account.

### HTTP Request Example

```json
{
  "value": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
  "visible": true
}
```

### HTTP Response Example

```json
{
  "account": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g"
}
```

Please note that the addresses in `fromAccounts` and `toAccounts` will vary based on the resources delegated to and from the account.
