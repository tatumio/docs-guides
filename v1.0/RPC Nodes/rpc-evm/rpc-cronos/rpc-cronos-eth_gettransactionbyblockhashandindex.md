---
title: "eth_gettransactionbyblockhashandindex"
slug: "rpc-cronos-eth_gettransactionbyblockhashandindex"
excerpt: "Cronos RPC"
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:35 GMT+0000 (Coordinated Universal Time)"
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

import { TatumSDK, Cronos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Cronos>({network: Network.CRONOS})

const tx = await tatum.rpc.getTransactionByBlockHashAndIndex('0x6565fd5921f93655e77d8cfeab8aa6caaf7155aeae24e91cdca33eedc66e6c5a', 0)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`eth_getTransactionByBlockHashAndIndex` is an JSON-RPC method that allows you to fetch the transaction details based on the block hash and the index of the transaction within that block. This method can be useful when you want to retrieve transaction details for a specific transaction without knowing its transaction hash.

Use cases for this method may include:

- Inspecting transaction details for debugging purposes
- Gathering data for transaction analysis
- Fetching transaction information for specific blocks in a block explorer application

### Parameters

The `eth_getTransactionByBlockHashAndIndex` method accepts two parameters:

1. `blockHash` (required): The hash of the block containing the transaction.
   - Example: `"0x6565fd5921f93655e77d8cfeab8aa6caaf7155aeae24e91cdca33eedc66e6c5a"`
2. `transactionIndex` (required): The index of the transaction within the specified block. The index is a hexadecimal value.
   - Example: `"0x0"`

### Return Object

The method returns a JSON object containing the following fields:

1. `hash`: The transaction hash as a 32-byte hex string.
2. `nonce`: The number of transactions made by the sender prior to this one.
3. `blockHash`: The hash of the block in which this transaction is included.
4. `blockNumber`: The block number in which this transaction is included.
5. `transactionIndex`: The index of the transaction within the block.
6. `from`: The address of the sender.
7. `to`: The address of the recipient. `null` if the transaction is a contract creation transaction.
8. `value`: The value transferred in wei.
9. `gasPrice`: The gas price provided by the sender in wei.
10. `gas`: The gas limit provided by the sender.
11. `input`: The data sent along with the transaction.
