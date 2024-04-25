---
title: "blockchainAddressGetHistory"
slug: "rpc-rostrum-blockchainAddressGetHistory"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, Nexa, address history, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.address.get_history` method retrieves the confirmed and unconfirmed transaction history of a Bitcoin Cash or Nexa address. This functionality is crucial for tracking transactions associated with specific addresses, providing a comprehensive view of an address's activity.

## Parameters

| Name     | Type   | Required | Description                                                                |
| -------- | ------ | -------- | -------------------------------------------------------------------------- |
| address  | string | Yes      | The Bitcoin Cash or Nexa address in Cash Address format or legacy format.  |
| filter   | string | No       | Determines which UTXOs are included. Valid options: 'include_tokens', 'tokens_only', 'exclude_token'. |

## Returns

The method returns an array of transaction histories, including both confirmed and unconfirmed transactions relevant to the specified address.

| Field       | Description                                                              |
| ----------- | ------------------------------------------------------------------------ |
| transactions| A list of transactions associated with the address, detailed by their inclusion status and transaction details. |

## Example Result

```json
{
  "transactions": [
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
    "method": "blockchain.address.get_history",
    "params": ["qpm2qsznhks23z7629mms6s4cwef74vcwvy22gdx6a", "include_tokens"],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Rostrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<Rostrum>({ network: Network.ROSTRUM_MAINNET });

const addressHistory = await tatum.rpc.getAddressHistory({
  address: "qpm2qsznhks23z7629mms6s4cwef74vcwvy22gdx6a",
  filter: "include_tokens"
});

console.log('Address History:', addressHistory);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs when done
```
