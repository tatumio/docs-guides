---
title: "getblockcount"
slug: "rpc-bch-getblockcount"
excerpt: "BCH RPC"
hidden: false
metadata: 
  description: "BCH RPC"
  image: []
  keywords: "bch, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:02 GMT+0000 (Coordinated Universal Time)"
---



### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, BitcoinCash, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<BitcoinCash>({network: Network.BITCOIN_CASH})

const result = await tatum.rpc.getBlockCount()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getblockcount` is a method that returns the number of blocks in the local best blockchain. This method is useful for obtaining the current height of the blockchain, which can be used for various purposes, such as monitoring the blockchain, determining the number of confirmations for a transaction, or assessing the progress of the blockchain's growth.

### Parameters

This method does not have any parameters.

### Return Object

The returned object is an integer representing the number of blocks in the local best blockchain.

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getblockcount"
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": 787067,
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
