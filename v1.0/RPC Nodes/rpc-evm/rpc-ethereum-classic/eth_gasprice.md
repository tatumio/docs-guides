---
title: "eth_gasprice"
slug: "rpc-ethereum-classic-eth_gasprice"
excerpt: "Ethereum Classic  RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Ethereum Classic  RPC"
  image: []
  keywords: "ethereum classic , rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

{% tabs %}
{% tab title="TypeScript/JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, EthereumClassic, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<EthereumClassic>({network: Network.ETHEREUM_CLASSIC})

const gasPrice = await tatum.rpc.gasPrice()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `eth_gasPrice` method is an Flare JSON-RPC method used to estimate the average gas price required for transactions in the Flare network. This method provides a suggestion for the gas price to be used in a transaction to increase the likelihood of it being mined and included in a block in a reasonable amount of time. The `eth_gasPrice` method is particularly useful for developers and users who want to create and send transactions, as it helps them estimate the appropriate gas price to ensure timely processing.

### Parameters

The `eth_gasPrice` method does not require any parameters.&#x20;

### Return Value

The `eth_gasPrice` method returns a single value as a hexadecimal string:

* `gasPrice`: The estimated average gas price in wei. Example: `"0x4a817c800"`

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_gasPrice",
  "params": []
}
```

#### Response

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": "0x4a817c800"
}
```

By using the `eth_gasPrice` method, developers and users can estimate the appropriate gas price for their transactions, improving the overall user experience and ensuring that their transactions are processed in a timely manner.