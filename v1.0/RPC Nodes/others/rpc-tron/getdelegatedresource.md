---
title: "getdelegatedresource"
slug: "rpc-tron-getdelegatedresource"
excerpt: "Tron RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

{% code overflow="wrap" lineNumbers="true" %}
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network, VisibleOption } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const res = await tatum.rpc.getDelegatedResource('TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g', 'TPswDDCAWhJAZGdHPidFg5nEf8TkNToDX1', {
  visible: true,
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getDelegatedResource` method retrieves all resources delegations during the stake1.0 phase from one account to another. It is useful when you need to assess the resources that an address delegates to a target address. The `fromAddress` parameter can be retrieved from the GetDelegatedResourceAccountIndex API.

{% embed url="https://codepen.io/tatum-devrel/pen/ZEmZwRJ" %}

### Parameters

* `fromAddress` (string, required): The energy from address. Default is hexString.
* `toAddress` (string, required): The target address for the energy delegation information.
* `options` (object, optional): This optional parameter contains the following properties:
  * `visible` (boolean, optional): Defaults to false. Whether addresses are in base58 format.

### Return Object

The return object is a list of `DelegatedResource` objects. Each `DelegatedResource` object contains:

* `from` (string): Delegate account
* `to` (string): Resource receiving account
* `frozen_balance_for_bandwidth` (integer): Bandwidth delegate share
* `frozen_balance_for_energy` (integer): Energy delegate share
* `expire_time_for_bandwidth` (integer): Deadline of this delegate bandwidth's lock period
* `expire_time_for_energy` (integer): Deadline of this delegate energy's lock period

### HTTP Request Example

```json
{
  "fromAddress": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
  "toAddress": "TPswDDCAWhJAZGdHPidFg5nEf8TkNToDX1",
  "visible": true
}
```

### HTTP Response Example

```json
[
    {
      "from": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
      "to": "TPswDDCAWhJAZGdHPidFg5nEf8TkNToDX1",
      "frozen_balance_for_bandwidth": 2000,
      "frozen_balance_for_energy": 3000,
      "expire_time_for_bandwidth": 1672448400000,
      "expire_time_for_energy": 1675040400000
    }
]
```
