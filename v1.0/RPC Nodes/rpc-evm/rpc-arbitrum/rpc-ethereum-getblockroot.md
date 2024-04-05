---
title: "getBlockRoot"
slug: "rpc-ethereum-getblockroot"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 17:01:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:03 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getBlockRoot`** endpoint allows you to retrieve the root of a specific Ethereum Beacon Chain block or block header.

## Parameters

| Name          | Type     | Required | Description                                                                                             |
| :------------ | :------- | :------- | :------------------------------------------------------------------------------------------------------ |
| **`blockId`** | `string` | Yes      | The unique block ID of the Ethereum 2.0 Beacon Chain block for which you want to retrieve attestations. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array): The `data` object with the following fields:
  - **root** (string, hex): The root of the Beacon Block or Block Header is a hexadecimal string representing the root hash of the beacon block header. It follows the pattern: ^0x[a-fA-F0-9]{64}$.

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM });

// Specify the block ID
const blockId = {blockId: 'your-block-id'}; // Replace with the desired block ID

// Retrieve the root of the specified Ethereum Beacon Chain block or block header
const blockRoot = await tatum.rpc.beacon.v1.getBlockRoot(blockId);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```
