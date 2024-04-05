---
title: "getStateFork"
slug: "rpc-arbitrum-getstatefork"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 17:59:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:34 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateFork`** endpoint allows you to retrieve information about the fork associated with a specific Ethereum Beacon Chain state.

## Example use cases:

1. **Fork Analysis:** Developers can analyze and track forks in the Ethereum Beacon Chain to make informed decisions.
2. **Network Monitoring:** Network administrators and developers use this data to monitor the Ethereum 2.0 network and its forks.

## Parameters

| Name          | Type     | Required | Description                                                                                                |
| :------------ | :------- | :------- | :--------------------------------------------------------------------------------------------------------- |
| **`stateId`** | `string` | Yes      | The unique identifier for the Ethereum Beacon Chain state for which you want to retrieve fork information. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object ): The `data` object contains the following properties:
  - **`previous_version`** (string, hex): Previous fork version number
  - **`current_version`** (string, hex): Current fork version number
  - **`epoch`** (string): The epoch number

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

// Retrieve the state fork using the getStateFork method
const stateFork = await tatum.rpc.beacon.v1.getStateFork({stateId: StateId});

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy()
```
