---
title: "getblock"
slug: "rpc-dogecoin-getblock"
excerpt: "Dogecoin RPC"
hidden: false
metadata: 
  description: "Dogecoin RPC"
  image: []
  keywords: "dogecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---



### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Dogecoin>({network: Network.DOGECOIN})

const result = await tatum.rpc.getBlock('000000000000000000013d0a85b72c591500abe074a7f9175c596a194f67b82d')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

`getblock` is a Dogecoin RPC method that returns information about a specified block. This method is useful for obtaining block details such as the hash, height, transactions, and other metadata. It can be used for various purposes, including validating transactions, monitoring the blockchain, and analyzing the network.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/Martin-Zemanek/pen/QWJopve",
  "href": "https://codepen.io/Martin-Zemanek/pen/QWJopve",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `hashOrHeight` (required): The hash or height of the block to be retrieved.
  - Example: `"0000000000000000000ef0e1f703b56f2b0d6724e4eeccf00e4f8d55b9c3c3f6e"`
- `verbose` - (boolean, optional, default=true) true for a json object, false for the hex encoded data

### Return Object

The returned object varies depending on the `verbosity` parameter:

- If `verbose` is `false`, the return object is a hex-encoded string of the serialized block.
- If `verbose` is `true`, the return object is a JSON object containing the following fields:
  - `hash`: The block hash.
  - `confirmations`: The number of confirmations for the block.
  - `strippedsize`: The block size without witness data.
  - `size`: The block size.
  - `weight`: The block weight.
  - `height`: The block height.
  - `version`: The block version.
  - `versionHex`: The block version as a hex string.
  - `merkleroot`: The Merkle root of the transactions in the block.
  - `tx`: An array of transaction identifiers (if `verbosity` is `1`) or detailed transaction objects (if `verbosity` is `2`).
  - `time`: The block time in UNIX timestamp format.
  - `mediantime`: The median block time of the previous 11 blocks.
  - `nonce`: The block nonce.
  - `bits`: The block difficulty target as a hex string.
  - `difficulty`: The block difficulty.
  - `chainwork`: The total work in the blockchain up to this block.
  - `nTx`: The number of transactions in the block.
  - `previousblockhash`: The hash of the previous block.
  - `nextblockhash`: The hash of the next block (if available).

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "getblock",
  "params": [
    "000000000000000000013d0a85b72c591500abe074a7f9175c596a194f67b82d",
    1
  ]
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
    "result": {
        "hash": "000000000000000000013d0a85b72c591500abe074a7f9175c596a194f67b82d",
        "confirmations": 1,
        "height": 787065,
        "version": 536895488,
        "versionHex": "20006000",
        "merkleroot": "f4d9edf4e50ed243778b553ae0043683a2a9be84c0996f15b30e2e282e6bd2d8",
        "time": 1682499730,
        "mediantime": 1682496628,
        "nonce": 1195457913,
        "bits": "1705c739",
        "difficulty": 48712405953118.43,
        "chainwork": "000000000000000000000000000000000000000046b01da204f6db69fc714174",
        "nTx": 4114,
        "previousblockhash": "000000000000000000041dd53066beb0577142582ec56573b5260d915311c773",
        "strippedsize": 770704,
        "size": 1680952,
        "weight": 3993064,
        "tx": [
            "63b36961bd94b217382409ceb8ec2f3da3d35a24e962e66089946d333f1af82b"
        ]
    },
    "error": null,
    "id": 1
}
```

{% endcode %}

\\
