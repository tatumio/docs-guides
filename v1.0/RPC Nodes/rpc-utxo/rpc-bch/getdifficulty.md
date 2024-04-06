---
title: "getdifficulty"
slug: "rpc-bch-getdifficulty"
excerpt: "BCH RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "BCH RPC"
  image: []
  keywords: "bch, rpc"
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

import { TatumSDK, BitcoinCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BitcoinCash>({network: Network.BITCOIN_CASH})

const result = await tatum.rpc.getDifficulty()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview

`getdifficulty` is a method that returns the current mining difficulty. The mining difficulty is a measure of how difficult it is to find a new block compared to the easiest it can ever be. This method can be used to monitor the mining difficulty, which adjusts every 2016 blocks to maintain a consistent block creation rate of approximately 10 minutes per block.

### Parameters

This method does not require any parameters.

### Return Object

A return object is a floating-point number that represents the current mining difficulty.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "jsonrpc": "2.0",
  "method": "getdifficulty",
  "id": 1
}
```
{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "result": 48712405953118.43,
    "error": null,
    "id": 1
}
```
{% endcode %}

\
