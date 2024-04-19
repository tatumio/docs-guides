---
title: "blockchainTransactionBroadcast"
slug: "blockchainTransactionBroadcast"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, transaction broadcast, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.transaction.broadcast` method allows clients to broadcast a raw transaction to the network. This function is essential for applications that need to send transactions directly.

## Parameters

| Name    | Type   | Required | Description                                |
| ------- | ------ | -------- | ------------------------------------------ |
| raw_tx  | string | Yes      | The raw transaction as a hexadecimal string. |

## Returns

The method returns the transaction hash if the transaction is successfully broadcast to the network. In case of an error, the method returns a JSON RPC error in newer protocol versions or an error message directly in the result for protocol version 1.0.

| Field   | Description                                                                      |
| ------- | -------------------------------------------------------------------------------- |
| txid    | The transaction hash as a hexadecimal string, or an error message (protocol v1.0). |

## Example Result

```json
"a76242fce5753b4212f903ff33ac6fe66f2780f34bdb4b33b175a7815a11a98e"
```

Protocol version 1.0 error example:

```json
"258: txn-mempool-conflict"
```

## Request Example

```curl /cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.transaction.broadcast",
    "params": ["0100000001abcdef..."],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const transactionHash = await tatum.rpc.broadcastTransaction("0100000001abcdef...");

console.log('Transaction Hash:', transactionHash);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```