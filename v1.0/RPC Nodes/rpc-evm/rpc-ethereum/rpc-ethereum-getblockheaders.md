---
title: "getBlockHeaders"
slug: "rpc-ethereum-getblockheaders"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 17:00:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:38 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getBlockHeaders`** endpoint allows you to retrieve beacon block headers from the Ethereum 2.0 Beacon Chain. These headers contain important information about the chain's progress and state.

## Example use cases:

1. **Chain Monitoring:** Developers and network administrators can use this endpoint to monitor the progress and health of the Ethereum 2.0 Beacon Chain.
2. **Validator Operations:** Validators can retrieve beacon block headers to perform various operations, such as proposing and attesting to blocks.

## Parameters

| Name              | Type     | Required | Description                                                                                              |
| :---------------- | :------- | :------- | :------------------------------------------------------------------------------------------------------- |
| **`slot`**        | `string` | No       | The slot number to fetch beacon block headers for.                                                       |
| **`parent_root`** | string   | No       | The root hash of the parent beacon block header. Fetches beacon block headers for the given parent root. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array): The **`data`** array contains a list of beacon block headers, where each header has the following structure:
  - **root** (string, hex): The root is a hexadecimal string representing the root hash of the beacon block header. It follows the pattern: ^0x[a-fA-F0-9]{64}$.
  - **canonical** (boolean): `true` if the block header is considered canonical, indicating it's part of the main chain.
  - **header** (object): The header object contains detailed information about the beacon block header.
    - **message** (array): The BeaconBlockHeader object
      - **slot** (string): The slot to which this block corresponds
      - **proposer_index** (string):  The index of validator in validator registry
      - **parent_root** (string): The signing merkle root of the parent BeaconBlock 
      - **state_root** (string): The tree hash merkle root of the BeaconState for the BeaconBlock
      - **body_root** (string): The tree hash merkle root of the BeaconBlockBody for the BeaconBlock
    - **signature** (string): The signature

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM });

// Retrieve beacon block headers using the getBlockHeaders method
const beaconHeaders = await tatum.rpc.beacon.v1.getBlockHeaders();

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```
