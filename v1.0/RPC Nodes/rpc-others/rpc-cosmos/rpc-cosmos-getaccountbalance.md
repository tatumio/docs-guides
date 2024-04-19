
---
title: "accountBalance"
slug: "accountBalance"
category: "6620f7e31ea673003624a8cc"
excerpt: "Rosetta API for Cosmos"
hidden: false
metadata:
  image: []
  keywords: "Cosmos, account balance, Rosetta API"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `/account/balance` method retrieves the balance of an account on the Cosmos network using the Rosetta API. It provides detailed information about the available and current spending balance of an account, including sub-accounts if specified.

## Parameters

| Name                | Type          | Required | Description                                                   |
| ------------------- | ------------- | -------- | ------------------------------------------------------------- |
| network_identifier  | object        | Yes      | Identifies the blockchain and network.                        |
| account_identifier  | object        | Yes      | Identifies the account for which the balance is requested.    |

## Returns

The method returns the current balance of the specified account and sub-account (if provided):

| Field           | Description                                                             |
| --------------- | ----------------------------------------------------------------------- |
| account_balance | The total balance of the account in the smallest unit of the currency.  |
| sub_account_balance | (Optional) The balance of the sub-account, if applicable.           |

## Example Result

```json
{
  "block_identifier": {
    "index": 123456,
    "hash": "b10a8db164e0754105b7a99be72e3fe5"
  },
  "balances": [
    {
      "value": "100000000",
      "currency": {
        "symbol": "ATOM",
        "decimals": 6
      }
    }
  ],
  "metadata": {}
}
```

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "network_identifier": {
        "blockchain": "cosmos",
        "network": "mainnet"
    },
    "account_identifier": {
        "address": "cosmos1l0znsvddllw9knha3yx2svnlxny676d8ns7uys",
        "sub_account": {
            "address": "cosmos1dq72ndqvcfnfgptud5puvys46y0zma5pvt37gz"
        }
    }
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

const accountBalance = await tatum.rpc.getAccountBalance({
  network_identifier: {
    blockchain: "cosmos",
    network: "mainnet"
  },
  account_identifier: {
    address: "cosmos1l0znsvddllw9knha3yx2svnlxny676d8ns7uys",
    sub_account: {
      address: "cosmos1dq72ndqvcfnfgptud5puvys46y0zma5pvt37gz"
    }
  }
});

console.log(accountBalance);

await cosmos.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
