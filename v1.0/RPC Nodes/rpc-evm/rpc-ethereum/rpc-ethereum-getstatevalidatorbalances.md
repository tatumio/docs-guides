---
title: "getStateValidatorBalances"
slug: "rpc-ethereum-getstatevalidatorbalances"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 17:56:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:59:15 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateValidatorBalances`** endpoint allows you to retrieve the balances of specific validators within the Ethereum Beacon Chain state.

## Parameters

| Name          | Type               | Required | Description                                                                                                                                                                     |
| :------------ | :----------------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **`stateId`** | `string`           | Yes      | The state identifier. It can be one of: head (canonical head in node's view), genesis, finalized, justified, slot and stateRoot (hex encoded stateRoot with 0x prefix)          |
| **`id`**      | `array of strings` | No       | specify the IDs of validators for which you want to retrieve balances. You can provide an array of hex-encoded public keys (any bytes48 with a 0x prefix) or validator indices. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array): The `data` object array contains the following properties:
  - **index** (string): The index of validator in validator registry
  - **balance** (string): The current validator balance in gwei

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM })

// Specify the state ID and optional array of validator IDs
const params = {
  state_id: 'your-state-id',
  id: ['validator-1', 'validator-2'], // Optional
}

// Retrieve validator balances using the getStateValidatorBalances method
const validatorBalances = await tatum.rpc.beacon.v1.getStateValidatorBalances(params);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy()
```
