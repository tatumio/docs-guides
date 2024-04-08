---
title: "eth_maxpriorityfeepergas"
slug: "rpc-tron-eth_maxpriorityfeepergas"
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

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

// Initialize the SDK for the TRON network
const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const gasPrice = await tatum.rpc.maxPriorityFeePerGas()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

The `eth_maxPriorityFeePerGas` RPC method is used to retrieve the maximum priority fee per gas set by the user for a transaction. This method can be used to determine the maximum fee that can be paid for a transaction to be included in a block quickly.

### Use case

This method is particularly useful when the user wants to ensure that a transaction is processed quickly, even in a congested network where transaction fees may fluctuate rapidly. By setting a high maximum priority fee per gas, the user can ensure that the transaction is processed as quickly as possible.

### Parameters

`None.`

## Return Object

- `maxPriorityFeePerGas` - The maximum priority fee per gas the user is willing to pay, in wei.

### JSON Examples

#### Request

```json
{
    "jsonrpc": "2.0",
    "method": "eth_maxPriorityFeePerGas",
    "params": [],
    "id": 1
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": "0x3b9aca00"
}
```

\\
