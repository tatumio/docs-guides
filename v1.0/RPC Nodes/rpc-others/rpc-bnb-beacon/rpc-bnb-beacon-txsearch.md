---
title: "txSearch"
slug: "rpc-bnb-beacon-txsearch"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style="padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Defining the search parameters
const searchParams = {
  query: 'QUERY_STRING',      // Replace with your query string (Required)
  prove: true,               // Include proofs of transaction inclusion in the block (true/false) (Required)
  page: '1',                   // Page number (1-based) (Optional)
  per_page: '10'               // Number of entries per page (max: 100) (Optional)
};

// Searching for transactions
const searchResults = await tatum.rpc.txSearch(searchParams);
console.log(searchResults);

// Destroy Tatum SDK - needed for stopping background jobs
await tatum.destroy();
```

### Overview

The `txSearch` method is used to search for transactions on the BNB beacon chain that match specific search criteria.

### Parameters

- `query` (string, Required): The query string used to search for transactions.
- `prove` (boolean, Required): Include proofs of the transaction's inclusion in the block (true/false).
- `page` (string number, Optional): Page number for paginating results (1-based).
- `per_page` (string number, Optional): Number of entries per page (max: 100).

### Return Object

The method returns a JSON-RPC response containing information about the matching transactions. The response includes the following fields:

- `total_count` (string, Required): The total count of matching transactions.
  - Example: `2`
- `txs` (array, Required): An array of transaction objects.
  - Example: `[ ]`

(Note: The exact structure of the transaction objects and response may vary based on the BNB beacon chain's implementation and version.)
