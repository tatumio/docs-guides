---
title: "eth_chainId"
slug: "rpc-ethereum-eth_chainid"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 22:23:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:34 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`eth_chainId` method is part of the Ethereum JSON-RPC API, specifically designed to return the current network or chain ID. This method is crucial for ensuring the uniqueness of transactions across different Ethereum networks, as it helps in preventing replay attacks by distinguishing between transactions intended for different networks. The chain ID was introduced as part of EIP-155 to address the issue of transaction replay attacks across different Ethereum networks.

## Parameters

`eth_chainId` method does not accept any parameters. This simplicity in its request format allows for a straightforward query to retrieve the current chain ID of the Ethereum network you are interacting with.

## Returns

The response to the `eth_chainId` method will be the current chain ID of the Ethereum network you are connected to. This ID is a hexadecimal number that uniquely identifies the network.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "method": "eth_chainId",
    "params": [],
    "id": 1,
    "jsonrpc": "2.0"
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const id = await tatum.rpc.chainId()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
