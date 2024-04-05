---
title: "getBlockAttestations"
slug: "rpc-arbitrum-getblockattestations"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 15:39:50 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:41:39 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getBlockAttestations`** endpoint allows you to retrieve attestations associated with a specific Ethereum 2.0 Beacon Chain block.

## Example use cases:

1. **Attestation Analysis:** Researchers and validators can use this endpoint to analyze attestations made for a specific block.
2. **Validator Operations:** Validators may need to retrieve attestations to check if their attestations have been included in a block.

## Parameters

| Name          | Type     | Required | Description                                                                                             |
| :------------ | :------- | :------- | :------------------------------------------------------------------------------------------------------ |
| **`blockId`** | `string` | Yes      | The unique block ID of the Ethereum 2.0 Beacon Chain block for which you want to retrieve attestations. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array): The **`data`** array contains information about attestations.
  - **aggregation_bits** (string): The attester aggregation bits
  - **data** (object array): The AttestationData object from the CL spec
    - **slot**: The corresponding slot
    - **index**: The index
    - **beacon_block_root**: The LMD GHOST vote
    - **source** (object array): The Checkpoint
      - **epoch** (string): The corresponding epoch
      - **root** (string): The corresponding root
    - **target** (object array): The Checkpoint
      - **epoch** (string): The corresponding epoch
      - **root** (string): The corresponding root
  - **signature** (string): The signature

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM });

// Specify the block ID in camel case
const blockId = '0xabcdef1234567890';

// Retrieve attestations for the specified block using the tatum.rpc.beacon.v1.getBlockAttestations method
const attestations = await tatum.rpc.beacon.v1.getBlockAttestations(blockId);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```
