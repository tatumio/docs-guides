---
title: "getStateValidators"
slug: "rpc-ethereum-getstatevalidators"
excerpt: "Ethereum RPC"
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Wed Mar 20 2024 18:09:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 12:59:40 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getStateValidator`** endpoint allows you to retrieve detailed information about a specific validator in the Ethereum Beacon Chain. This information is valuable for anyone interested in understanding the status and details of a particular validator.

## Parameters

| Name          | Type           | Required | Description                                                                                                                                                                                                                                         |
| :------------ | :------------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`stateId`** | `string`       | Yes      | The state identifier. It can be one of: head (canonical head in node's view), genesis, finalized, justified, slot and stateRoot (hex encoded stateRoot with 0x prefix)                                                                              |
| **`id`**      | `string array` | No       | An array of either hex-encoded public keys (any bytes48 with a 0x prefix) or validator indices.                                                                                                                                                     |
| **`status`**  | `string array` | No       | Validator status specification. Available values: pending_initialized, pending_queued, active_ongoing, active_exiting, active_slashed, exited_unslashed, exited_slashed, withdrawal_possible, withdrawal_done, active, pending, exited, withdrawal. |

## Returns

- **execution_optimistic** (boolean): `true` if the response references an unverified execution payload. Optimistic information may be invalidated at a later time. If the field is not present, assume the `false` value.
- **finalized** (boolean): If the response mentions the chain's final history picked by forks, it's `true`. Without the field, more calls are needed to compare the requested epoch with the final checkpoint.
- **data**  (object array ): The `data` object arrays contain the following structure:
  - **index** (string): The index of validator in validator registry
  - **balance** (string): The current validator balance in gwei
  - **status** (string): The Validator status which could have possible values of:
    - **pending_initialized**: When the first deposit is processed, but not enough funds are available (or not yet the end of the first epoch) to get validator into the activation queue
    - **pending_queued**: When validator is waiting to get activated, and has enough funds, etc. while in the queue, validator activation epoch keeps changing until it gets to the front and makes it through (finalization is a requirement here too)
    - **active_ongoing**: When validator must be attesting and has not initiated any exit
    - **active_exiting**: When validator is still active, but filed a voluntary request to exit
    - **active_slashed**: When validator is still active, but has a slashed status and is scheduled to exit
    - **exited_unslashed**: When validator has reached the regular exit epoch, is not being slashed, and doesn't have to attest any more, but cannot withdraw yet
    - **exited_slashed**: When validator has reached the regular exit epoch, but was slashed, have to wait for a longer withdrawal period
    - **withdrawal_possible**: After validator has exited, a while later is permitted to move funds and is truly out of the system
    - **withdrawal_done**: (not possible in phase0, except slashing full balance) having moved funds away
  - **validator** (object): Validator details containing the following fields:
    - **pubkey** (string): The validator's BLS public key, uniquely identifying them. \_48-bytes, hex encoded with 0x prefix, case insensitive
    - **withdrawal_crendetials** (string): The root of withdrawal credentials
    - **effective_balance** (string): The balance at stake in Gwei
    - **slashed** (string): The validator is slashed (no longer active) or not
    - **activation_elgibility_epoch** (string): When criteria for activation were met
    - **activation_epoch** (string):  Epoch when validator activated. FAR_FUTURE_EPOCH if not activated
    - **exit_epoch** (string): Epoch when validator exited
    - **withdrawable_epoch** (string): When validator can withdraw or transfer funds. FAR_FUTURE_EPOCH if not defined

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM })

// Specify the state ID, optional ID array, and optional status array
const params = {
  stateId: 'your-state-id',
  id: ['validator-1', 'validator-2']; // Optional,
  status: ['active', 'exited']; // Optional,
}
const idArray = 
const statusArray = 

// Retrieve information about validators using the getStateValidators method
const validators = await tatum.rpc.beacon.v1.getStateValidators(params);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy()
```
