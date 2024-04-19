---
title: "accountCoins"
slug: "accountCoins"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rosetta API for {{blockchain}}"
hidden: false
metadata:
  image: []
  keywords: "{{blockchain}}, account coins, Rosetta API"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/account/coins` method retrieves information about the coins stored at a specific account address on the {{blockchain}} network, using the Rosetta API. This includes detailed data on each coin or token associated with the account, which is crucial for tracking asset distributions and understanding the account's composition on the blockchain.

## Parameters

| Name                | Type          | Required | Description                                                   |
| ------------------- | ------------- | -------- | ------------------------------------------------------------- |
| network_identifier  | object        | Yes      | Identifies the blockchain and network.                        |
| account_identifier  | object        | Yes      | Identifies the account for which the coin details are requested. Includes primary and sub-account details. |

## Returns

The response includes details about each coin held in the specified account and sub-account (if provided):

| Field           | Description                                                             |
| --------------- | ----------------------------------------------------------------------- |
| coins           | A list of coin objects representing each asset held by the account.     |
| block_identifier| The block identifier where the latest balance snapshot was taken.        |

## Example Result

```json
{
  "block_identifier": {
    "index": 1234567,
    "hash": "a1b2c3d4..."
  },
  "coins": [
    {
      "coin_identifier": {
        "identifier": "coin1"
      },
      "amount": {
        "value": "100000000",
        "currency": {
          "symbol": "ATOM",
          "decimals": 6
        }
      }
    }
  ]
}
```

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/{{blockchain}}-{{network}}/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "network_identifier": {
        "blockchain": "{{blockchain}}",
        "network": "{{network}}"
    },
    "account_identifier": {
        "address": "{{address}}",
        "sub_account": {
            "address": "{{addressto}}"
        }
    }
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, {{BlockchainModule}}, Network } from "@tatumio/tatum";

const {{blockchain}} = await TatumSDK.init<{{BlockchainModule}}>({ network: Network.{{BLOCKCHAIN_NETWORK}} });

const accountCoins = await tatum.rpc.getAccountCoins({
  network_identifier: {
    blockchain: "{{blockchain}}",
    network: "{{network}}"
  },
  account_identifier: {
    address: "{{address}}",
    sub_account: {
      address: "{{addressto}}"
    }
  }
});

console.log(accountCoins);

await {{blockchain}}.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
