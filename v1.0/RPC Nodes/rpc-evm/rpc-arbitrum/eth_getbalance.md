---
title: "eth_getbalance"
slug: "rpc-arbitrum-eth_getbalance"
excerpt: "Arbitrum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Arbitrum RPC"
  image: []
  keywords: "arbitrum, rpc"
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

import { TatumSDK, ArbitrumOne, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<ArbitrumOne>({network: Network.ARBITRUM_ONE})

const balance = await tatum.rpc.getBalance('0xe4edb277e41dc89ab076a1f049f4a3efa700bce8')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `eth_getBalance` method is an JSON-RPC method that allows you to retrieve the balance of a specified address. This method can be used to query the balance of any address, whether it is a contract or an externally owned account (EOA). A common use case for this method is to display the current balance of a user's account in a wallet application or a decentralized application (DApp).

### Parameters

The method requires two parameters:

1. **`address`** (required): The address of the account or contract whose balance you want to query.
   * Example: `"0xe4edb277e41dc89ab076a1f049f4a3efa700bce8"`
2. **`blockParameter`** (optional): The block number or block identifier to specify the point in time for which you want to query the balance.
   * Example: `"latest"` or `"0x1"`

#### Transaction Details

For the purpose of this documentation, we'll also describe the `transactions` field of a full transaction object. The `eth_getBalance` method does not return transaction details, but we provide this information for completeness.

A full transaction object includes the following fields:

* **`hash`**: The transaction hash.
* **`nonce`**: The number of transactions made by the sender prior to this one.
* **`blockHash`**: The hash of the block in which the transaction was included.
* **`blockNumber`**: The block number in which the transaction was included.
* **`transactionIndex`**: The index of the transaction in the block.
* **`from`**: The sender's address.
* **`to`**: The recipient's address (or `null` for contract creation transactions).
* **`value`**: The value transferred, in wei.
* **`gasPrice`**: The gas price provided by the sender, in wei.
* **`gas`**: The maximum gas allowed for the transaction.
* **`input`**: The data sent with the transaction (typically for contract interaction).
* **`v`**, **`r`**, **`s`**: The raw signature values of the transaction.

### Return Object

The method returns a single field:

* `result`: The Flare balance of the specified address in wei, as a hexadecimal string.
  * Example: `"0x1a2e1a"`, which corresponds to `1,726,666` wei.

### JSON-RPC Request and Response Examples

#### Request

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getBalance",
  "params": [
    "0xe4edb277e41dc89ab076a1f049f4a3efa700bce8",
    "latest"
  ]
}
```

#### Response

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1a2e1a"
}
```
