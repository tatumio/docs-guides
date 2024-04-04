---
title: "eth_getBlockTransactionCountByHash"
slug: "rpc-ethereum-eth_getblocktransactioncountbyhash"
excerpt: "Ethereum RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 07:23:14 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:01:56 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getBlockTransactionCountByHash` is an Ethereum RPC method used to fetch the number of transactions in a block by the block's hash. It is useful when you want to know the total number of transactions included in a specific block and don't want to retrieve the entire block data. This method can be used in various scenarios, such as monitoring the network activity or estimating transaction confirmation times.

## Parameters

This method requires a single parameter:

**blockHash**: The hash of the target block for which the transaction count will be retrieved. It should be a valid 32-byte hex string.

- Example: `blockHash` :"0x2907402477167193008a0cbbaa8073278c48e8b97bf9ed1a2101f6ad2130dbaf"

## Returns

The method returns a single value:

| Name             | Description                                                                                              |
| :--------------- | :------------------------------------------------------------------------------------------------------- |
| transactionCount | The total number of transactions included in the specified block. It is returned as a hexadecimal value. |

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
	"id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getBlockTransactionCountByHash",
  "params": [
    "0x2907402477167193008a0cbbaa8073278c48e8b97bf9ed1a2101f6ad2130dbaf"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const response = await tatum.rpc.getBlockTransactionCountByHash('0x2907402477167193008a0cbbaa8073278c48e8b97bf9ed1a2101f6ad2130dbaf')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
