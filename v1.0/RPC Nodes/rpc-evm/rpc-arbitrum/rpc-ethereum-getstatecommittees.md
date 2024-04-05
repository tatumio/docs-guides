---
title: "getStateCommittees"
slug: "rpc-arbitrum-getstatecommittees"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 17:32:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:16 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateCommittees`** endpoint allows you to retrieve information about committees associated with a specific Ethereum 2.0 Beacon Chain state.

## Example use cases:

1. **Committee Analysis: **Researchers and validators can use this endpoint to analyze committees for a specific state, including validator indices and shard assignments.
2. **Validator Operations:** Validators may need to retrieve committee information to participate in shard or crosslink proposals.

## Parameters

| Name           | Type     | Required | Description                                                                                                                                                            |
| :------------- | :------- | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`state_id`** | `string` | Yes      | The state identifier. It can be one of: head (canonical head in node's view), genesis, finalized, justified, slot and stateRoot (hex encoded stateRoot with 0x prefix) |
| **`epoch`**    | `string` | No       | Fetch committees for the given epoch. If not present, the committees for the epoch of the state will be obtained.                                                      |
| **`index`**    | `string` | No       | Restrict returned values to those matching the supplied committee index.                                                                                               |
| **`slot`**     | string   | No       | Restrict returned values to those matching the supplied slot.                                                                                                          |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array): The `data` array contains information about committees. Each committee object in the array includes details related to the committee index, slot, and an array of validators assigned to attest at a specific slot with the same committee index.
  - **index** (string): The committee index at a slot
  - **`slot`** (string): The slot
  - **`validators`** (object array): The list of validator indices assigned to this committee

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM })

// Define the parameters object
const params = {
  stateId: 'your-state-id', // Replace with the actual state ID you want to use
  epoch: '1',   // Optional: Fetch committees for a specific epoch
  index: '1',   // Optional: Restrict returned values to a specific committee index
  slot: '1',    // Optional: Restrict returned values to a specific slot
};

// Retrieve committees information using the getStateCommittees method
const committees = await tatum.rpc.beacon.v1.getStateCommittees(params);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy()
```
