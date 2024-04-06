---
title: "txpool_content"
slug: "rpc-cronos-txpool_content"
excerpt: "Cronos RPC"
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:34 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
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

const content = await tatum.rpc.txPoolContent()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview

The `txpool_content` method provides information about the transactions currently pending in the transaction pool of the node. It can be helpful for developers and node operators to monitor and manage the transaction pool, especially in scenarios where it's necessary to analyze transaction congestion or prioritize specific transactions.

Use cases for the `txpool_content` method include:

- Analyzing network congestion by inspecting the transaction pool
- Prioritizing transactions by gas price
- Monitoring transactions from specific addresses
- Debugging and troubleshooting pending transactions

### Parameters

This method does not require any parameters.

### Return Object

The `txpool_content` method returns an object with two fields: `pending` and `queued`. Each field contains a nested object with addresses as keys and their respective transactions as values.

- **`pending`**: An object containing transactions that are currently pending for inclusion in the next block(s).
- **`queued`**: An object containing transactions that are currently queued (i.e., transactions that do not meet certain criteria for inclusion in the next block, like low gas price or nonce gaps).

Each transaction object includes the following information:

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
