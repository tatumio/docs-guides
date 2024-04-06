---
title: "validateaddress"
slug: "rpc-btc-validateaddress"
excerpt: "Bitcoin RPC"
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 07:09:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `validateaddress` is a Bitcoin RPC method that enables users to verify if a given Bitcoin address is valid. This method provides important information about the address, such as its type and whether it's a spendable or watch-only address. It can be particularly useful in applications where address validation is necessary before performing transactions or when dealing with user-generated addresses to ensure their validity.

## Parameters

The `validateaddress` method accepts one required parameter:

`address` : The Bitcoin address to be validated.

## Returns

The validateaddress method returns an object with the following fields:

| Name            | Description                                                                                 |
| :-------------- | :------------------------------------------------------------------------------------------ |
| isvalid         | Indicates if the supplied address is valid.                                                 |
| address         | The validated Bitcoin address.                                                              |
| scriptPubKey    | The hex-encoded scriptPubKey generated by the address.                                      |
| isscript        | Indicates if the address is a script address (P2SH).                                        |
| iswitness       | Indicates if the address is a witness address (P2WPKH or P2WSH).                            |
| witness_version | The version number of the witness program, if applicable.                                   |
| witness_program | The hex value of the witness program, if applicable.                                        |
| isspendable     | Indicates if the address is spendable (has the private key).                                |
| iswatchonly     | Indicates if the address is watch-only (wallet has the public key but not the private key). |
| iscompressed    | Indicates if the associated public key is compressed.                                       |
| account         | DEPRECATED. The account associated with the address, if any.                                |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "validateaddress",
  "params": [
    "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.validateAddress("1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```