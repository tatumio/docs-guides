---
title: "estimateenergy"
slug: "rpc-tron-estimateenergy"
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

{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const res = await tatum.rpc.estimateEnergy(
  'TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g', 
  'TG3XXyExBkPp9nzdajDZsozEu4BkaSJozs', 
  'balanceOf(address)', 
  '000000000000000000000000a614f803b6fd780986a42c78ec9c7f77e6ded13c',
  { visible: true }
)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}

### Overview

The `estimateEnergy` method is used to estimate the energy required for the successful execution of smart contract transactions on the TRON blockchain. It can be used to get a more accurate estimation of the energy consumption for executing certain special contracts compared to the existing `wallet/triggerconstantcontract` API.

This method does not generate an on-chain transaction, nor does it change the status of the current node. The `energy_required` field in the returned value is the estimated energy amount.

### Parameters

- `ownerAddress` (string): The owner address that triggers the contract. If `visible=true`, use base58check format, otherwise use hex format. For a constant call, you can use the all-zero address.
- `contractAddress` (string): The smart contract address. If `visible=true`, use base58check format, otherwise use hex format.
- `functionSelector` (string): The function call. It must not be left blank.
- `parameter` (string): The parameter encoding needs to be in accordance with the ABI rules.
- `options` (object, optional): This is an optional parameter that can include:
  - `visible` (boolean, optional): Specifies whether the address is in base58 format.

### Return Object

- `result: object` - The run result.
  - `result` - Indicates if the estimate is successful.
  - `code` - The response code.
  - `message` - The result message.
- `energy_required` - The estimated energy to run the contract.

### HTTP Request Example

```json
{
  "owner_address": "TZ4UXDV5ZhNW7fb2AMSbgfAEZ7hWsnYS2g",
  "contract_address": "TG3XXyExBkPp9nzdajDZsozEu4BkaSJozs",
  "function_selector": "balanceOf(address)",
  "parameter": "000000000000000000000000a614f803b6fd780986a42c78ec9c7f77e6ded13c",
  "visible": true
}
```

### HTTP Response Example

```json
{
  "result": {
    "result": true
  },
  "energy_required": 1082
}
```
