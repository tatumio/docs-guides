---
title: "eth_gettransactionbyhash"
slug: "rpc-cronos-eth_gettransactionbyhash"
excerpt: "Cronos RPC"
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:41 GMT+0000 (Coordinated Universal Time)"
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

const tx = await tatum.rpc.getTransactionByHash('0x068f00756843c4fa018771decb06767e0e6a57045eabcbce1125a56115f2742a')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

`eth_getTransactionByHash` is an JSON-RPC method that allows you to query transaction details based on its hash. This method is useful when you want to retrieve information about a specific transaction, such as its sender, receiver, value, and more. Common use cases include tracking transaction status, monitoring incoming transactions, or analyzing historical transaction data.

### Parameters

The `eth_getTransactionByHash` method takes one parameter:

- **`transactionHash`**: The hash of the transaction you want to retrieve. This should be a 32-byte hash string with a `0x` prefix.
  - Example: `"0x068f00756843c4fa018771decb06767e0e6a57045eabcbce1125a56115f2742a"`

### Return Object

The method returns a transaction object with the following fields:

- **`hash`**: The hash of the transaction (32 bytes).
- **`nonce`**: The number of transactions sent by the sender prior to this one (integer).
- **`blockHash`**: The hash of the block in which the transaction was included (32 bytes), or `null` if the transaction is not yet mined.
- **`blockNumber`**: The block number in which the transaction was included (integer), or `null` if the transaction is not yet mined.
- **`transactionIndex`**: The index of the transaction in the block (integer), or `null` if the transaction is not yet mined.
- **`from`**: The address of the sender (20 bytes).
- **`to`**: The address of the receiver (20 bytes), or `null` for contract creation transactions.
- **`value`**: The value transferred in the transaction, in wei.
- **`gasPrice`**: The price of gas for the transaction, in wei.
- **`maxFeePerGas`** - The maximum fee per gas set in the transaction.
- **`maxPriorityFeePerGas`** - The maximum priority gas fee set in the transaction.
- **`gas`**: The maximum amount of gas the transaction is allowed to consume.
- **`input`**: The data payload of the transaction (string), or `0x` for simple value transfers.
