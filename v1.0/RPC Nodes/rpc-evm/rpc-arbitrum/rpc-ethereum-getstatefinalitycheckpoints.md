---
title: "getStateFinalityCheckpoints"
slug: "rpc-ethereum-getstatefinalitycheckpoints"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Tue Mar 19 2024 17:43:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:25 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateFinalityCheckpoints`** endpoint allows you to retrieve the finality checkpoints associated with a specific `stateId`.

## Example use cases:

1. **Finality Assessment:** Developers can use finality checkpoints to assess the level of finality reached by the Ethereum Beacon Chain. By examining the `previous_justified`, `current_justified`, and `finalized` checkpoints, they can determine the state of consensus and the security of the network.
2. **Validator Monitoring: **Validators in the Ethereum 2.0 network can use finality checkpoints to monitor the progress and stability of the network. They can track changes in the `previous_justified` and `current_justified` checkpoints to ensure they are participating in a secure and finalized chain.
3. **Network Stability Analysis:** Network administrators and developers can monitor the network's finality checkpoints to assess its stability. Sudden changes or deviations in the `previous_justified`, `current_justified`, and `finalized` checkpoints may indicate issues or attacks on the network, prompting immediate action.

## Parameters

| Name          | Type     | Required | Description                                                                                                    |
| :------------ | :------- | :------- | :------------------------------------------------------------------------------------------------------------- |
| **`stateId`** | `string` | Yes      | The unique identifier for the Ethereum Beacon Chain state for which you want to retrieve finality checkpoints. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object): The `data` object contains the finality checkpoints with the following structure:
  - **`previous_justified`** (object): Provides information about the previous justified beacon block.
    - **`epoch`** (string): The corresponding epoch
    - **`root`** (string): The corresponding root
  - **`current_justified`** (object): Provides information about the current justified beacon block.
    - **`epoch`** (string): The corresponding epoch
    - **`root`** (string): The corresponding root
  - **`finalized`** (object): Provides information about the finalized beacon block.
    - **`epoch`** (string): The corresponding epoch
    - **`root`** (string): The corresponding root

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum';

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM });

// Specify the state ID
const StateId = 'your-state-id';

// Retrieve the finality checkpoints using the getStateFinalityCheckpoints method
const finalityCheckpoints = await tatum.rpc.beacon.v1.getStateFinalityCheckpoints({stateId: StateId});

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```
