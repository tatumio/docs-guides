---
title: "getbalance"
slug: "rpc-solana-getbalance"
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


### How to use it

{% code overflow="wrap" lineNumbers="true" %}
```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Solana, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Solana>({ network: Network.SOLANA })

const res = await tatum.rpc.getBalance('8Ew6iQXcTRHAUNNu3X9VBn1g1bJkXEZJ9gFD2AGKtdPB')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}

### Overview

The `getBalance` RPC method is used to retrieve the current balance of a specified account on the Solana blockchain. It's a straightforward and efficient way to monitor and keep track of account balances.

This method is typically used in scenarios where you need to check the available balance before initiating a transaction or for accounting purposes in a wallet application.

### Parameters

The `getBalance` method requires one parameter:

* (string, required) Pubkey of account to query, as base-58 encoded string
  * Example: `"8Ew6iQXcTRHAUNNu3X9VBn1g1bJkXEZJ9gFD2AGKtdPB"`

### Return object

The `getBalance` method returns an object containing the following fields:

* `context`: An object containing details about the context in which the balance was fetched.
  * `slot`: The slot at which the data was fetched.
* `value`: The current balance of the account, in lamports.

### JSON-RPC Request Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "getBalance",
  "params": [
    "8Ew6iQXcTRHAUNNu3X9VBn1g1bJkXEZJ9gFD2AGKtdPB",
  ]
}
```

### JSON-RPC Response Example

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "context": {
      "slot": 194573649
    },
    "value": 2484257209
  }
}
```
