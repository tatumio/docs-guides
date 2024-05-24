---
title: "submitTransaction"
slug: "rpc-cosmos-submittransaction"
category: "6620f7e31ea673003624a8ce"
parentDoc: "662a3ee8730164006e9b0cd5"
excerpt: "Cosmos RPC"
hidden: false
metadata: 
  description: "Submit transactions to the Cosmos network."
  image: []
  keywords: "cosmos, rpc, submit transaction"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---

## Overview

The `submitTransaction` method allows you to submit a signed transaction to the Cosmos network for processing. This is essential for pushing transactions to the blockchain, enabling transfers, smart contract interactions, and other blockchain activities.

## Parameters

| Name                  | Type   | Required | Description                                                      |
| --------------------- | ------ | -------- | ---------------------------------------------------------------- |
| `networkIdentifier`     | object                              | Yes      | Identifies the Cosmos blockchain and network details.           |
| `blockchain`            | string (from networkIdentifier)     | Yes      | The blockchain identifier, typically "Cosmos".                  |
| `network`               | string (from networkIdentifier)     | Yes      | The network name on which the transaction is taking place.      |
| `subNetworkIdentifier`  | object (from networkIdentifier)     | No       | Optional sub-network identifier object.                         |
| `network`               | string (from subNetworkIdentifier)  | Yes      | The name of the sub-network within Cosmos.                      |
| `metadata`              | object (from subNetworkIdentifier)  | No       | Metadata associated with the sub-network.                       |
| `signedTransaction`     | string | Yes      | The signed transaction data in hexadecimal format.               |

## Returns

The method returns a response from the Cosmos network that typically includes the transaction hash, indicating successful submission.

| Field                | Description                                         |
| -------------------- | --------------------------------------------------- |
| `transactionHash`      | The hash of the transaction as accepted by the network. |

## Example Result

```json
{
  "transactionHash": "CBA1234ABCD5678EFGH91011IJ"
}
```

## Request Example

```curl
curl --location 'https://api.tatum.io/v3/blockchain/node/cosmos-mainnet/construction/submit' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data-raw '{
    "networkIdentifier": {
        "blockchain": "cosmos",
        "network": "mainnet"
    },
    "signedTransaction": "7f2b...f123"
}'
```

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Cosmos, Network } from "@tatumio/tatum";

const cosmos = await TatumSDK.init<Cosmos>({ network: Network.COSMOS_MAINNET });

const submitResponse = await tatum.rpc.submitTransaction({
  networkIdentifier: {
    blockchain: "cosmos",
    network: "mainnet",
  },
  signedTransaction: "7f2b...f123"
});

console.log('Transaction Response:', submitResponse);

await tatum.destroy(); // Destroy Tatum SDK - needed for stopping background jobs
```
