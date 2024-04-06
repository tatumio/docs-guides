---
title: "eth_getblockbynumber"
slug: "rpc-cronos-eth_getblockbynumber"
excerpt: "Cronos RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Cronos RPC"
  image: []
  keywords: "cronos, rpc"
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

import { TatumSDK, Cronos, Network } from '@tatumio/tatum'
  
const tatum = await TatumSDK.init<Cronos>({network: Network.CRONOS})

const block = await tatum.rpc.getBlockByNumber('latest', true)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

`eth_getBlockByNumber` is an JSON-RPC method that allows developers to query a specific block in the blockchain by its block number. This method can be used in various scenarios, such as analyzing historical transactions, validating the state of the blockchain, or monitoring the progress of mining activities.

### Parameters

There are two required parameters for this method:

1.  **`blockNumber`** - The block number of the block to be retrieved. This can be a hexadecimal string or one of the predefined aliases: `"earliest"`, `"latest"`, or `"pending"`.

    Example: `"0x1b4"`
2.  **`returnFullTransactionObjects`** - A boolean value that determines whether the returned block contains complete transaction objects (`true`) or only transaction hashes (`false`).

    Example: `true`

### Return Object

The returned block object includes the following fields:

* **`number`** - The block number (hexadecimal string).
* **`hash`** - The block hash (32-byte string).
* **`parentHash`** - The hash of the parent block (32-byte string).
* **`nonce`** - The nonce used to generate the block (8-byte string).
* **`sha3Uncles`** - The SHA3 hash of the uncles in the block (32-byte string).
* **`logsBloom`** - The logs bloom filter of the block (256-byte string).
* **`transactionsRoot`** - The root of the transaction trie (32-byte string).
* **`stateRoot`** - The root of the state trie (32-byte string).
* **`miner`** - The address of the miner who mined the block (20-byte string).
* **`difficulty`** - The difficulty of the block (hexadecimal string).
* **`totalDifficulty`** - The total difficulty of the chain up to this block (hexadecimal string).
* **`extraData`** - Extra data included by the miner in the block (byte string).
* **`size`** - The block size in bytes (hexadecimal string).
* **`gasLimit`** - The gas limit for the block (hexadecimal string).
* **`gasUsed`** - The total gas used by all transactions in the block (hexadecimal string).
* **`timestamp`** - The block timestamp (hexadecimal string).
* **`transactions`** - An array of transaction objects or transaction hashes, depending on the `returnFullTransactionObjects` parameter.
* **`uncles`** - An array of uncle block hashes (32-byte strings).

If `returnFullTransactionObjects` is `true`, the `transactions` field contains transaction objects with the following fields:

* **`hash`** - The transaction hash (32-byte string).
* **`nonce`** - The number of transactions sent by the sender before this transaction (hexadecimal string).
* **`blockHash`** - The block hash where the transaction is included (32-byte string).
* **`blockNumber`** - The block number where the transaction is included (hexadecimal string).
* **`transactionIndex`** - The index of the transaction in the block (hexadecimal string).
* **`from`** - The sender address (20-byte string).
* **`to`** - The recipient address, or `null` for contract creation transactions (20-byte string).
* **`value`** - The value being transferred (hexadecimal string).
* **`gasPrice`** - The gas price in wei (hexadecimal string).
* **`gas`** - The gas provided for the transaction (hexadecimal string).
* **`input`** - The input data for the transaction (byte string).