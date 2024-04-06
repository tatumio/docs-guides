---
title: "estimatefee"
slug: "rpc-bch-estimatefee"
excerpt: "BCH RPC"
hidden: false
metadata: 
  description: "BCH RPC"
  image: []
  keywords: "bch, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
import { TatumSDK, BitcoinCash, Network } from '@tatumio/tatum';

// Initialize Tatum SDK for Bitcoin Cash
const tatum = await TatumSDK.init<BitcoinCash>({ network: Network.BITCOIN_CASH });

// Call the estimatefee method
const estimatedFee = await tatum.rpc.estimateFee();

console.log('Estimated fee:', estimatedFee.result);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `estimatefee` method is used to estimate the transaction fee for a transaction. It calculates the fee based on the current network conditions.

### Example use cases:

1. **Transaction Fee Calculation:**  
   This method is commonly used by wallet applications to calculate the appropriate transaction fee for a transaction based on the desired confirmation time.

2. **Custom Fee Estimation:**  
   Developers can use this method to implement custom fee estimation logic in their applications.

### Request Parameters

The `estimatefee` method does not require any parameters.

### Return Object

The `estimatefee` method returns an estimated transaction fee in currency unit. The fee is typically represented as a numeric value.
