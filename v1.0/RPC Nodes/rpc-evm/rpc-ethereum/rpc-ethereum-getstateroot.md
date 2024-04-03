---
title: "getStateRoot"
slug: "rpc-ethereum-getstateroot"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 16:14:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:43 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateRoot`** endpoint allows you to retrieve the state root of a specific Ethereum Beacon Chain state.

## Example use cases:

1. **State Verification:** Developers can verify the state of the Ethereum Beacon Chain at a specific state ID.
2. **Custom Queries:** Network administrators and developers can use this data for custom queries and analysis of the Ethereum 2.0 network.

## Parameters

| Name          | Type     | Required | Description                                                                                  |
| :------------ | :------- | :------- | :------------------------------------------------------------------------------------------- |
| **`stateId`** | `string` | Yes      | The unique identifier for the Ethereum Beacon Chain state you want to retrieve the root for. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object ): The `data` object contains the following properties:
  - **root** (string, hex): The `root` is a hexadecimal string representing the HashTreeRoot of the BeaconState object. It follows the pattern:` ^0x[a-fA-F0-9]{64}$`.

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM })

// Specify the state ID
const StateId = 'your-state-id';

// Retrieve the state root using the getStateRoot method
const stateRoot = await tatum.rpc.beacon.v1.getStateRoot({stateId: StateId});

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy()
```
