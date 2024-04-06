---
title: "eth_blockNumber"
slug: "rpc-ethereum-eth_blocknumber"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 06:52:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Apr 04 2024 07:56:50 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`eth_blockNumber` method is part of the Ethereum JSON-RPC API, which is used to interact with the Ethereum blockchain. 

This method is particularly useful for various use cases within the blockchain ecosystem, including but not limited to:

- Monitoring Blockchain Health: By regularly checking the latest block number, developers can monitor the health and activity of the Ethereum blockchain. This can be crucial for applications that rely on the blockchain for their operations, as it helps in identifying any potential issues or delays in block production.
- Synchronization Checks: For applications that interact with the Ethereum blockchain, knowing the latest block number can be essential for synchronization purposes. It helps in ensuring that the application's data is up-to-date with the blockchain's state.
- Transaction Verification: When submitting transactions to the blockchain, knowing the current block number can be useful for setting appropriate gas prices and for verifying transaction confirmations.

## Parameters

 `eth_blockNumber` method does not accept any parameters, which simplifies its usage. This is because the method is designed to return the most recent block number without needing any additional input from the user.

## Returns

The response from the `eth_blockNumber` method is a JSON object containing the following fields:

| Name        | Description                                                                                                    |
| :---------- | :------------------------------------------------------------------------------------------------------------- |
| blockNumber | The number of the most recent block on the Ethereum blockchain. The value is returned as a hexadecimal string. |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "eth_blockNumber",
  "params": []
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const latestBlock = await tatum.rpc.blockNumber()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
