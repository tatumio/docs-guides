---
title: "blockchainAddressGetMempool"
slug: "rpc-rostrum-blockchainAddressGetMempool"
category: "6620f7e31ea673003624a8ce"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, Nexa, mempool, unconfirmed transactions, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.address.get_mempool` method retrieves the unconfirmed transactions associated with a Bitcoin Cash or Nexa address. This allows users to view pending transactions that have not yet been included in a block, providing insights into upcoming transactions.

## Parameters

| Name     | Type   | Required | Description                                                                |
| -------- | ------ | -------- | -------------------------------------------------------------------------- |
| address  | string | Yes      | The Bitcoin Cash or Nexa address in Cash Address format or legacy format.  |
| filter   | string | No       | Specifies which UTXOs are included. Options: 'include_tokens', 'tokens_only', 'exclude_token'. |

## Returns

The method returns an array of unconfirmed transactions for the specified address.

| Field             | Description                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| unconfirmed_txs   | List of unconfirmed transactions with details such as transaction hash, inputs, and outputs. |

## Example Result

```json
{
  "unconfirmed_txs": [
    {
      "tx_hash": "b6f6998abc08195f5b..."
    },
    {
      "tx_hash": "a2c8579bfcc32e..."
    }
  ]
}
```

## Request Example

```curl /cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.address.get_mempool",
    "params": ["qpm2qsznhks23z7629mms6s4cwef74vcwvy22gdx6a", "include_tokens"],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const mempoolTransactions = await tatum.rpc.getMempoolTransactions({
  address: "qpm2qsznhks23z7629mms6s4cwef74vcwvy22gdx6a",
  filter: "include_tokens"
});

console.log('Mempool Transactions:', mempoolTransactions);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```
