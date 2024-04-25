---
title: "blockchainTransactionGet"
slug: "rpc-rostrum-blockchainTransactionGet"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash and Nexa"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, Nexa, transaction, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.transaction.get` method retrieves a raw transaction from Bitcoin Cash or Nexa blockchains using the transaction hash. It can return a simple hexadecimal string or a detailed, decoded transaction object.

## Parameters

| Name     | Type    | Required | Description                                        |
| -------- | ------- | -------- | -------------------------------------------------- |
| tx_hash  | string  | Yes      | The transaction hash as a hexadecimal string.      |
| verbose  | boolean | No       | Specifies whether to return a decoded transaction. |

## Returns

If `verbose` is false, the raw transaction is returned as a hexadecimal string. If `verbose` is true, a detailed dictionary of the transaction is returned.

| Field         | Description                                              |
| ------------- | -------------------------------------------------------- |
| hex           | The raw transaction as a hexadecimal string.             |
| txid          | The transaction ID.                                      |
| size          | The transaction size in bytes.                           |
| version       | The version number of the transaction format.            |
| locktime      | The transaction's lock time.                             |
| vin           | An array of transaction inputs.                          |
| vout          | An array of transaction outputs.                         |
| blockhash     | The block hash containing this transaction (if confirmed).|
| confirmations | The number of confirmations of the block containing this transaction. |
| time          | Transaction timestamp from the block.                    |
| blocktime     | Block timestamp as seen by the network.                  |
| fee           | Transaction fee (if available).                          |

### Example Result for Verbose = false

```json
"0100000001abcdef..."
```

### Example Result for Verbose = true

```json
{
  "hex": "0100000001abcdef...",
  "txid": "exampletxid",
  "size": 225,
  "version": 1,
  "locktime": 0,
  "vin": [
    {
      "txid": "sometxid",
      "vout": 0,
      "scriptSig": {
        "asm": "asm code",
        "hex": "hex code"
      },
      "sequence": 4294967295
    }
  ],
  "vout": [
    {
      "value": 0.0001,
      "n": 0,
      "scriptPubKey": {
        "asm": "asm code",
        "hex": "hex code",
        "addresses": [
          "bitcoincash:address"
        ]
      }
    }
  ],
  "blockhash": "someblockhash",
  "confirmations": 10,
  "time": 1510000000,
  "blocktime": 1510000000,
  "fee": "0.00001"
}
```

## Request Example

```curl /cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.transaction.get",
    "params": ["exampletxid", true],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const transaction = await tatum.rpc.getTransaction("exampletxid", true);

console.log('Transaction Details:', transaction);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```