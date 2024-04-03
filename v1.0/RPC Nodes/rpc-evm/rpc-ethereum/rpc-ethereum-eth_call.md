---
title: "eth_call"
slug: "rpc-ethereum-eth_call"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 06:56:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 09:01:00 GMT+0000 (Coordinated Universal Time)"
---
## Overview

`eth_call` method in Ethereum's JSON-RPC API is used to execute a new message call immediately without creating a transaction on the blockchain. This method is particularly useful for testing and debugging smart contracts, as it allows developers to simulate the execution of contract methods without actually sending transactions to the network. This can help in identifying issues or understanding the behavior of contracts without incurring any gas costs or affecting the blockchain state. Please check the common use cases:

- Testing Smart Contracts: Before deploying a smart contract, developers can use `eth_call` to test its functionality and ensure it behaves as expected.
- Debugging: It can be used to debug smart contracts by simulating transactions and observing the state changes or return values without affecting the live contract.
- Estimating Gas Costs: Although `eth_call` does not actually send a transaction, it can be used to estimate the gas costs of a transaction by simulating its execution.

## Parameters

`Object`: The transaction call object

- `from`: DATA, 20 Bytes - (optional) The address the transaction is sent from.
- `to`: DATA, 20 Bytes - The address the transaction is directed to.
- `gas`: QUANTITY - (optional) Integer of the gas provided for the transaction execution. eth_call consumes zero gas, but this parameter may be needed by some executions.
- `gasPrice`: QUANTITY - (optional) Integer of the gasPrice used for each paid gas
- `value`: QUANTITY - (optional) Integer of the value sent with this transaction
- `data`: DATA - (optional) Hash of the method signature and encoded parameters. For details see Ethereum Contract ABI in the Solidity documentation ([opens in a new tab](https://docs.soliditylang.org/en/latest/abi-spec.html))

`QUANTITY|TAG` : Integer block number, or the string "latest", "earliest" or "pending", see the default block parameter

## Returns

The response from the `eth_call` method is a JSON object containing the following fields:

| Name | Description                            |
| :--- | :------------------------------------- |
| DATA | The return value of executed contract. |

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/ethereum-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
    "jsonrpc": "2.0",
    "method": "eth_call",
    "params": [
        {
            "from": "0x47ac0Fb4F2D84898e4D9E7b4DaB3C24507a6D503",
            "to": "0xdAC17F958D2ee523a2206206994597C13D831ec7",
            "gas": "0x92c0",
            "gasPrice": "0x7896e72a000",
            "value": "0x0",
            "data": "0x70a0823100000000000000000000000047ac0fb4f2d84898e4d9e7b4dab3c24507a6d503"
        },
        "latest"
    ],
    "id": 1
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const result = await tatum.rpc.call({
  "to": "0xD31a59c85aE9D8edEFeC411D448f90841571b89c", // Replace with the ERC-20 token contract address, in this case wrapped SOL on Ethereum
  "data": "0x70a08231000000000000000000000000F22981C5bF0A717c98781Af04fdc8213fA789F1C" // The function signature for balanceOf(address), followed by the address (F22981C5bF0A717c98781Af04fdc8213fA789F1C) to query, in this case holder of wrapped SOL tokens
}, "latest")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
