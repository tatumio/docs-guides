---
title: "getBlockHeader"
slug: "rpc-ethereum-getblockheader"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 17:25:56 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:39 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getBlockHeader`** endpoint allows you to retrieve a specific beacon block header from the Ethereum 2.0 Beacon Chain based on its unique block ID.

## Example use cases:

1. **Header Retrieval:** Developers and network administrators can use this endpoint to fetch the header of a specific beacon block for analysis or verification purposes.
2. **Validator Operations:** Validators may need to retrieve specific beacon block headers for proposing and attesting to blocks.

## Parameters

| Name          | Type     | Required | Description                                                                                             |
| :------------ | :------- | :------- | :------------------------------------------------------------------------------------------------------ |
| **`blockId`** | `string` | Yes      | The unique block ID of the Ethereum 2.0 Beacon Chain block for which you want to retrieve attestations. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array): The `data` object with the following fields:
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

// Specify the block ID
const BlockId = '0xabcdef1234567890';

// Retrieve the beacon block header using the getBlockHeader method
const beaconHeader = await tatum.rpc.beacon.v1.getBlockHeader({blockId: BlockId});

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```
