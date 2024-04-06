---
title: "validators"
slug: "rpc-bnb-beacon-validators"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:03 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to Use It

```typescript
// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Optional parameters 
const params = {
    height : 'your-height',
    page : 'your-page',
    perPage : 'entries-per-page'
};
// Retrieve the current validator set
const validatorSet = await tatum.rpc.validators(params);
console.log(validatorSet);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `validators` method is used to retrieve the current validator set on the BNB Beacon Chain.

### Parameters

- `height` (string, optional): Height to return. If no height is provided, it will fetch the validator set corresponding to the latest block.
- `page` (string, optional): Page number (1-based).
- `perPage` (string, optional): Number of entries per page (max: 100).

### Return Object (Required)

- `block_height` (string): Example: `55`
- `validators` (array): An array of validator objects representing the validators in the set. Example: `[]`

(Note: The exact structure of the validator objects and response may vary based on the BNB Beacon Chain's implementation and version.)
