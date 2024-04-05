---
title: "getGenesis"
slug: "rpc-arbitrum-getgenesis"
excerpt: "Ethereum RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  image: []
  keywords: "ethereum, rpc"
  robots: "index"
createdAt: "Mon Mar 18 2024 17:43:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:58:06 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The **`getGenesis`** endpoint allows you to retrieve critical information about the genesis state of the Ethereum Beacon Chain.

## Example use cases:

1. **Network Monitoring:** Network administrators and developers use this data to monitor and analyze the Ethereum 2.0 network's health and progress.
2. **Validator Setup:** Validators joining the Ethereum Beacon Chain network need the genesis information to initialize their nodes correctly.

## Parameters

The **`getGenesis`** endpoint does not require any additional parameters. You can simply make a GET request to the endpoint to retrieve the genesis information.

## Returns

- **data** (object): The object with the following values:
  - **genesis_time** (string): The genesis_time configured for the beacon node, which is the unix time in seconds at which the Eth2.0 chain began
  - **genesis_validators_root** (string): The genesis validator root
  - **genesis_fork_version** (string): A fork version number

## Request Example

```Text cURL

```
```javascript JS SDK
// Import necessary libraries and modules
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

// Initialize the Tatum SDK with Ethereum-specific parameters
const tatum = await TatumSDK.init<Ethereum>({ network: Network.ETHEREUM })

// Retrieve the Ethereum Beacon Chain genesis information
const response = await tatum.rpc.beacon.v1.getGenesis()

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy()
```
