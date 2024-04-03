---
title: "getStateSyncCommittees"
slug: "rpc-ethereum-getstatesynccommittees"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 16:49:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:52 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateSyncCommittees`** endpoint allows you to retrieve information about the sync committees of the Ethereum Beacon Chain for a specific state.

## Parameters

| Name          | Type     | Required | Description                                                                                                                                                            |
| :------------ | :------- | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`stateId`** | `string` | Yes      | The state identifier. It can be one of: head (canonical head in node's view), genesis, finalized, justified, slot and stateRoot (hex encoded stateRoot with 0x prefix) |
| **`epoch`**   | `string` | No       | To fetch sync committees for a specific epoch.                                                                                                                         |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object ): The `data` object ccontains the following properties:
  - **validators** (object array): An object array of validators participating in sync committees.
  - **validator_aggregates** (object array): An object array of aggregated data from validators in sync committees.

## Request Example

```Text cURL

```
```Text JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM });

// Specify request parameters as one object
const params = {
  stateId: 'your-state-id',
  epoch: 'your-epoch', // Optional: Replace with the desired epoch
};

// Retrieve sync committees for the specified state
const syncCommittees = await tatum.rpc.beacon.v1.getStateSyncCommittees(params);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```
