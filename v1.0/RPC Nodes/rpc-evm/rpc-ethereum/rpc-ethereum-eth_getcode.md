---
title: "eth_getCode"
slug: "rpc-ethereum-eth_getcode"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 07:29:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:36 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getCode` method is part of the Ethereum JSON-RPC API and is used to retrieve the contract code (bytecode) of an account at a specific block number. This method is particularly useful for developers who need to examine the bytecode of a deployed contract, verify the integrity of a deployed contract, analyze contract bytecode for security vulnerabilities, or debug a smart contract.

## Parameters

The `eth_getCode` method accepts two parameters:

1. **address**(string): The address of the contract whose bytecode you want to retrieve. This should be a 20-byte Ethereum address, formatted as a hex string with a 0x prefix.
   - Example: "0x742d35Cc6634C0532925a3b844Bc454e4438f44e"
2. **block**(string): The block number at which you want to retrieve the contract code. This can be specified as a hex string or one of the following special keywords:
   - `"earliest"`: The first block in the blockchain
   - `"latest"`: The most recent block in the blockchain
   - `"pending"`: The upcoming block that is being mined
     - Example: `"0x1"` or `"latest"`

## Returns

The `eth_getCode` method returns a string representing the contract bytecode. The returned value is a hex string with a 0x prefix.

- If the account has contract code, the returned string will contain the bytecode.
- If the account is not a contract or does not exist, the returned string will be `0x`.

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_getCode",
  "params": [
    "0x742d35Cc6634C0532925a3b844Bc454e4438f44e",
    "latest"
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const code = await tatum.rpc.getCode('0x742d35Cc6634C0532925a3b844Bc454e4438f44e')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
