---
title: "getaccountresource"
slug: "rpc-tron-getaccountresource"
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

import { TatumSDK, Tron, Network, VisibleOption } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const address = 'TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g'

const res = await tatum.rpc.getAccountResources(address, {
  visible: true,
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getAccountResources` method is used to query resource information (such as bandwidth, energy) of a specific account on the TRON network. This method can be useful for assessing an account's remaining computational and storage capacity.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/rNQbPvG",
  "href": "https://codepen.io/tatum-devrel/pen/rNQbPvG",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `address` (string): The address of the account whose resources are to be queried.
- `options` (object, optional): This optional parameter contains the following properties:
  - `visible` (boolean, optional): Optional parameter to specify whether the address is in base58 format.

### Return Object

- `freeNetUsed` (integer): Free bandwidth used.
- `freeNetLimit` (integer): Total free bandwidth.
- `NetUsed` (integer): Used amount of bandwidth obtained by staking.
- `NetLimit` (integer): Total bandwidth obtained by staking.
- `TotalNetLimit` (integer): Total bandwidth can be obtained by staking by the whole network.
- `TotalNetWeight` (integer): Total TRX staked for bandwidth by the whole network.
- `totalTronPowerWeight` (integer): The total amount of voting rights obtained by the whole network.
- `tronPowerLimit` (integer): TRON Power (vote).
- `tronPowerUsed` (integer): TRON Power (vote) used.
- `EnergyUsed` (integer): Energy used.
- `EnergyLimit` (integer): Total energy obtained by staking.
- `TotalEnergyLimit` (integer): Total energy can be obtained by staking by the whole network.
- `TotalEnergyWeight` (integer): Total TRX staked for energy by the whole network.
- `assetNetUsed` (map\<string, integer>): The amount of free bandwidth of each TRC10 asset used by the account.
- `assetNetLimit` (map\<string, integer>): The amount of free bandwidth for each TRC10 asset in the account.

### HTTP Request Example

```json
{
  "address": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
  "visible": true
}
```

### HTTP Response Example

```json
{
  "freeNetLimit": 1500,
  "TotalNetLimit": 43200000000,
  "TotalNetWeight": 84593524300,
  "TotalEnergyLimit": 50000000000000,
  "TotalEnergyWeight": 12189370443
}
```
