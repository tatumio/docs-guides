---
title: "getblockcommitment"
slug: "rpc-solana-getblockcommitment"
excerpt: "Solana RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Solana RPC"
  image: []
  keywords: "solana, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]


### How to Use It

{% code overflow="wrap" lineNumbers="true" %}
```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getBlockCommitment(5)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getBlockCommitment` method returns the commitment for a particular block. Commitment in Solana refers to the amount of cluster stake in lamports that has voted on the block at each depth from 0 to `MAX_LOCKOUT_HISTORY` + 1.

This method is crucial for understanding the level of consensus or agreement about a block in the network, as it indicates how much of the network's total stake has confirmed the block. It can be used by blockchain explorers to show the confirmation status of transactions and by network monitors to track the progress of the blockchain.

{% embed url="https://codepen.io/tatum-devrel/pen/QWJoKEX" %}

### Parameters

This method takes the following parameter:

* `number` (required): The block number, identified by Slot.

### Return Object

The method returns a JSON object that includes detailed information about the block's commitment and the total active stake in the current epoch. If the specified block is not known, the `commitment` field will be `null`.

The returned JSON object includes the following fields:

* `commitment`: Commitment, comprising either:
  * `<null>` - Unknown block.
  * `<array>` - Commitment, an array of integers logging the amount of cluster stake in lamports that has voted on the block at each depth from 0 to `MAX_LOCKOUT_HISTORY` + 1.
* `totalStake`: The total active stake, in lamports, of the current epoch.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getBlockCommitment",
  "params": [5]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "result": {
    "commitment": [
      0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
      0, 0, 0, 0, 0, 10, 32
    ],
    "totalStake": 42
  },
  "id": 1
}
```
