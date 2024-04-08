---
title: "getFeeStats"
slug: "rpc-stellar-getfeestats"
excerpt: "Stellar RPC"
hidden: false
metadata: 
  description: "Stellar RPC"
  image: []
  keywords: "stellar, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:30:56 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Stellar, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Stellar
const tatum = await TatumSDK.init<Stellar>({ network: Network.STELLAR });

// Retrieve fee statistics
const feeStats = await tatum.rpc.getFeeStats();

// Log the fee statistics
console.log("Fee Statistics:", feeStats);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getFeeStats` method allows you to retrieve information about per-operation fee statistics over the last 5 ledgers on the Stellar blockchain.

### Return Object

The `getFeeStats` method returns a JSON object containing fee statistics for various operations. The structure of the returned object is defined by the `FeeStats` schema.

(Note: The exact fields in the return object may vary based on the Stellar blockchain's implementation and version.)

```json
{
  "last_ledger": "50744146",
  "last_ledger_base_fee": "100",
  "ledger_capacity_usage": "0.58",
  "fee_charged": {
    "max": "100",
    "min": "100",
    "mode": "100",
    "p10": "100",
    "p20": "100",
    "p30": "100",
    "p40": "100",
    "p50": "100",
    "p60": "100",
    "p70": "100",
    "p80": "100",
    "p90": "100",
    "p95": "100",
    "p99": "100"
  },
  "max_fee": {
    "max": "369592103",
    "min": "100",
    "mode": "100",
    "p10": "100",
    "p20": "100",
    "p30": "100",
    "p40": "1000",
    "p50": "20000",
    "p60": "51234",
    "p70": "51234",
    "p80": "100159",
    "p90": "250005",
    "p95": "500000",
    "p99": "358388826"
  }
}
```
