---
title: "klay_getblocktransactioncountbynumber"
slug: "rpc-klaytn-klay_getblocktransactioncountbynumber"
excerpt: "Klaytn RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Klaytn RPC"
  image: []
  keywords: "klaytn, rpc"
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

import { TatumSDK, Klaytn, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Klaytn>({network: Network.KLAYTN})

const response = await tatum.rpc.getBlockTransactionCountByNumber('0x80F8C7A')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `klay_getBlockTransactionCountByNumber` JSON-RPC method allows you to retrieve the number of transactions in a specified block. This method is particularly useful when you need to analyze the transaction activity of a specific block. You can use it to gain insights into network usage, analyze the impact of specific events on the network, or monitor transaction congestion in certain blocks.

### Parameters

1. **`blockNumber`**: The block number for which the transaction count should be retrieved. It should be a hex-encoded value representing the block number.
   * Example: 371156

### Return Object

The return object is a hex-encoded value representing the number of transactions in the specified block.

* Example: `"0x1"` (1 transactions)

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "klay_getBlockTransactionCountByNumber",
  "params": [371156]
}
```

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1"
}
```



\