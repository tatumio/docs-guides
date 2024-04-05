---
title: "eth_getBlockByHash"
slug: "rpc-arbitrum-eth_getblockbyhash"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 07:05:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:01:20 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `eth_getBlockByHash` is an Ethereum JSON-RPC method that allows developers to query a specific block in the Ethereum blockchain by its block hash. This method can be used in various scenarios, such as analysing historical transactions, validating the state of the blockchain, or monitoring the progress of mining activities.

## Parameters

The `eth_getBlockByHash` method accepts two parameters:

1. **blockHash**: The hash of the block you want to retrieve information about.
   - Type: String
   - Example: "0x75e58e08a9f3a23bac9788d5077a9365abb5c29ec1aab70891264051624720af"
2. **fullTransactionDetails**: A boolean value indicating whether to return full transaction details or just transaction hashes. 
   - Type: Boolean
   - Example: True

## Returns

The response from the `eth_getBlockByHash` method is a JSON object containing the following fields:

| Name             | Description                                                                                                       |
| :--------------- | :---------------------------------------------------------------------------------------------------------------- |
| number           | The block number (hexadecimal string).                                                                            |
| hash             | The block hash (32-byte string).                                                                                  |
| parentHash       | The hash of the parent block (32-byte string).                                                                    |
| nonce            | The nonce used to generate the block (8-byte string).                                                             |
| sha3Uncles       | The SHA3 hash of the uncles in the block (32-byte string).                                                        |
| logsBloom        | The logs bloom filter of the block (256-byte string).                                                             |
| transactionsRoot | The root of the transaction trie (32-byte string).                                                                |
| stateRoot        | The root of the state trie (32-byte string).                                                                      |
| miner            | The address of the miner who mined the block (20-byte string).                                                    |
| difficulty       | The difficulty of the block (hexadecimal string).                                                                 |
| totalDifficulty  | The total difficulty of the chain up to this block (hexadecimal string).                                          |
| extraData        | Extra data included by the miner in the block (byte string).                                                      |
| size             | The block size in bytes (hexadecimal string).                                                                     |
| gasLimit         | The gas limit for the block (hexadecimal string).                                                                 |
| gasUsed          | The total gas used by all transactions in the block (hexadecimal string).                                         |
| timestamp        | The block timestamp (hexadecimal string).                                                                         |
| transactions     | An array of transaction objects or transaction hashes, depending on the `returnFullTransactionObjects` parameter. |
| uncles           | An array of uncle block hashes (32-byte strings).                                                                 |

If `returnFullTransactionObjects `is true, the transactions field contains transaction objects with the following fields:

| Name             | Description                                                                         |
| :--------------- | :---------------------------------------------------------------------------------- |
| hash             | The block hash (32-byte string).                                                    |
| nonce            | The nonce used to generate the block (8-byte string).                               |
| blockHash        | The block hash where the transaction is included (32-byte string).                  |
| blockNumber      | The block number where the transaction is included (hexadecimal string).            |
| transactionIndex | The index of the transaction in the block (hexadecimal string).                     |
| from             | The sender address (20-byte string).                                                |
| to               | The recipient address, or null for contract creation transactions (20-byte string). |
| value            | The value being transferred (hexadecimal string).                                   |
| gasPrice         | The gas price in wei (hexadecimal string).                                          |
| gas              | The gas provided for the transaction (hexadecimal string)..                         |
| input            | The input data for the transaction (byte string).                                   |

## Request

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "method": "eth_getBlockByHash",
  "params": ["0x75e58e08a9f3a23bac9788d5077a9365abb5c29ec1aab70891264051624720af", true],
  "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const block = await tatum.rpc.getBlockByHash('0x75e58e08a9f3a23bac9788d5077a9365abb5c29ec1aab70891264051624720af', true)

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
