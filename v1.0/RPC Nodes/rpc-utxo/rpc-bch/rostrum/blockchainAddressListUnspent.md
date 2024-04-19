---
title: "blockchainAddressListUnspent"
slug: "blockchainAddressListUnspent"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, Nexa, list unspent, UTXOs, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.address.listunspent` method retrieves a detailed list of unspent transaction outputs (UTXOs) for a specified Bitcoin Cash or Nexa address. This method is crucial for applications that require knowledge of available UTXOs for constructing new transactions.

## Parameters

| Name     | Type   | Required | Description                                                                |
| -------- | ------ | -------- | -------------------------------------------------------------------------- |
| address  | string | Yes      | The Bitcoin Cash or Nexa address in Cash Address format or legacy format.  |
| filter   | string | No       | Specifies which UTXOs are included. Options: 'include_tokens', 'tokens_only', 'exclude_token'. |

## Returns

The method returns a sorted array of UTXOs for the address specified.

| Field             | Description                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| utxos             | An ordered list of UTXOs including details like txid, vout, script, amount, and confirmations. |

## Example Result

```json
{
  "utxos": [
    {
      "txid": "b6f6998abc08195f5b...",
      "vout": 0,
      "script": "76a914...",
      "amount": 0.015,
      "confirmations": 10
    },
    {
      "txid": "a2c8579bfcc32e...",
      "vout": 1,
      "script": "76a914...",
      "amount": 0.033,
      "confirmations": 5
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
    "method": "blockchain.address.listunspent",
    "params": ["qpm2qsznhks23z7629mms6s4cwef74vcwvy22gdx6a", "include_tokens"],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const utxos = await tatum.rpc.listUnspent({
  address: "qpm2qsznhks23z7629mms6s4cwef74vcwvy22gdx6a",
  filter: "include_tokens"
});

console.log('List of UTXOs:', utxos);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```
