---
title: "blockchainAddressGetBalance"
slug: "rpc-rostrum-blockchainAddressGetBalance"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee9ea8e770036f3c937"
excerpt: "Rostrum Electrum for Bitcoin Cash"
hidden: false
metadata:
  image: []
  keywords: "Bitcoin Cash, get balance, address balance, Electrum"
  robots: "index"
createdAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 11 2024 10:00:00 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `blockchain.address.get_balance` method retrieves the confirmed and unconfirmed balances of a Bitcoin Cash address. This method provides crucial data for wallet applications and services that require up-to-date balance information.

## Parameters

| Name    | Type   | Required | Description                                                   |
| ------- | ------ | -------- | ------------------------------------------------------------- |
| address | string | Yes      | The Bitcoin Cash address in Cash Address or legacy format.    |
| filter  | string | No       | Determines which UTXOs are included in the balance calculation. Options are `include_tokens`, `tokens_only`, `exclude_token`. Default is `include_tokens`. |

## Returns

The response includes both confirmed and unconfirmed balances:

| Field            | Description                                                    |
| ---------------- | -------------------------------------------------------------- |
| confirmed        | The confirmed balance of the address in satoshis.              |
| unconfirmed      | The unconfirmed balance of the address in satoshis.            |

## Example Result

```json
{
  "confirmed": 450000000,
  "unconfirmed": 50000000
}

## Request Example

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/rostrum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "blockchain.address.get_balance",
    "params": ["bchtest:qp3hnqdkvqxfzvcj7xqm8sb4cs4mq856vsk5nx9h2w", "include_tokens"],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, RostrumElectrum, Network } from "@tatumio/tatum";

const rostrum = await TatumSDK.init<RostrumElectrum>({ network: Network.BITCOIN_CASH_MAINNET });

const balance = await tatum.rpc.getAddressBalance({
  address: "bchtest:qp3hnqdkvqxfzvcj7xqm8sb4cs4mq856vsk5nx9h2w",
  filter: "include_tokens"
});

console.log(balance);

await rostrum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
