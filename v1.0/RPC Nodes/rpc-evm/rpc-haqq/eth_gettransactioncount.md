---
title: "eth_gettransactioncount"
slug: "rpc-haqq-eth_gettransactioncount"
excerpt: "Haqq  RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Haqq RPC"
  image: []
  keywords: "haqq, rpc"
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

import { TatumSDK, Haqq, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Haqq>({network: Network.HAQQ})

const result = await tatum.rpc.getTransactionCount('0x2eAd3B147fc20fB03fd25C71c1677E81714A9Eb5', 'latest')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

The `eth_getTransactionCount` method is an Haqq JSON-RPC method that retrieves the number of transactions sent from a given address. It is a useful method for developers who need to keep track of an account's nonce value to avoid transaction collisions or incorrect order of execution. The nonce value is essential for ensuring transaction uniqueness and preventing replay attacks.

Use cases for this method include:

* Determining the nonce value for a new transaction to be sent from a specific address
* Monitoring the number of transactions sent by an address to observe its activity
* Troubleshooting transaction issues and verifying if a transaction was submitted successfully

{% embed url="https://codepen.io/Jan-Musil-the-lessful/pen/RwqvOmO?editors=1111" %}

### Parameters

The `eth_getTransactionCount` method accepts two parameters:

1. **`address`** - The Haqq address whose transaction count will be retrieved.
   * Example: `"0x2eAd3B147fc20fB03fd25C71c1677E81714A9Eb5"`
2. **`blockParameter`** - A string indicating the block number or block state to consider when retrieving the transaction count.
   * Possible values: `"earliest"`, `"latest"`, `"pending"`, or a specific block number in hexadecimal format
   * Example: `"latest"`

### Return Object

The method returns a single value:

* **`transactionCount`** - A hexadecimal representation of the number of transactions sent from the specified address.
  * Example: `"0x1e"`

### JSON-RPC Request and Response Examples

_Request_:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_getTransactionCount",
  "params": [
    "0x2eAd3B147fc20fB03fd25C71c1677E81714A9Eb5",
    "latest"
  ]
}
```

_Response_:

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": "0x1e"
}
```
