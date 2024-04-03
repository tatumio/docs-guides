---
title: "eth_maxPriorityFeePerGas"
slug: "rpc-ethereum-eth_maxpriorityfeepergas"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 07:57:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:04:30 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The`eth_maxPriorityFeePerGas` RPC method is  specifically designed to return the maximum priority fee per gas that is needed to be included in a block. This method is crucial for developers and users interacting with the Ethereum network, as it provides insights into the current gas fees required for transactions to be processed efficiently.

## Parameters:

This method does not accept any parameters. This simplicity allows for a straightforward query to obtain the current maximum priority fee per gas.

## Returns

The response from the `eth_maxPriorityFeePerGas` method is a string representing the maximum priority fee per gas in wei. Wei is the smallest denomination of ether, where 1 ether = 1e18 wei.

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/API_KEY/' \
--header 'Content-Type: application/json' \
--header 'x-api-key:{API_KEY}' \
--data '{
    "jsonrpc": "2.0",
    "method": "eth_maxPriorityFeePerGas",
    "params": [],
    "id": 1
}'

```
```javascript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const gasPrice = await tatum.rpc.maxPriorityFeePerGas()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
