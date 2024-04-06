---
title: "web3_clientVersion"
slug: "rpc-ethereum-web3_clientversion"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 22:33:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:39 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`web3_clientVersion` method is part of the Ethereum JSON-RPC API, specifically designed to return the current version of the Ethereum client being used. This method is particularly useful for debugging or when you need to ensure compatibility with specific client versions.

## Parameters

This method does not accept any parameters. It is a simple request that does not require any input data to function.

## Returns

The response from the `web3_clientVersion `method will be a JSON object containing the result field, which holds the current client version in string format.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "jsonrpc": "2.0",
    "method": "web3_clientVersion",
    "params": [],
    "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const version = await tatum.rpc.clientVersion()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
