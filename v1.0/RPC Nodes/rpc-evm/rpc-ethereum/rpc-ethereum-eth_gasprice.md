---
title: "eth_gasPrice"
slug: "rpc-ethereum-eth_gasprice"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 07:29:43 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:37 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`eth_gasPrice` method is part of the Ethereum JSON-RPC API, which is used to interact with the Ethereum blockchain. This method specifically returns the current gas price on the Ethereum network in wei. Wei is the smallest denomination of ether, the cryptocurrency used on the Ethereum network. The gas price is a critical parameter for transactions on the Ethereum network, as it determines how much a transaction is willing to pay per unit of gas, which is a measure of computational effort.

## Parameters

The` eth_gasPrice` method does not accept any parameters. This means that when you call this method, you do not need to provide any additional information besides the method name itself.

## Returns

The response from the` eth_gasPrice` method will be a JSON object containing the result, which is the hexadecimal value of the current gas price in wei. This value is crucial for setting the gas price for transactions, as it directly influences how quickly a transaction is processed by the network.

## Request & Response Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/API_KEY/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_gasPrice",
  "params": []
}'

```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const gasPrice = await tatum.rpc.gasPrice()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
