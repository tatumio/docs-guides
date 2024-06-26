---
title: "abciQuerry"
slug: "rpc-bnb-beacon-abciquerry"
excerpt: "Bnb Beacon RPC"
hidden: false
metadata: 
  description: "Bnb Beacon RPC"
  image: []
  keywords: "bnb-beacon, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:00:05 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```typescript
/// Importing Tatum SDK for Beacon Chain
import { TatumSDK, Network, Bnb } from '@tatumio/tatum';

// Initializing SDK for Beacon Chain network
const tatum = await TatumSDK.init<Bnb>({ network: Network.BNB });

// Defining query parameters for the 'abciQuery' method
const queryParams = {
  path: 'YOUR_PATH_HERE',   
  data: 'YOUR_DATA_HERE',  
  height: 'YOUR_HEIGHT_VALUE',  
  prove: YOUR_PROVE_BOOLEAN
};

// Using the 'abciQuery' method to query data from the ABCI application
const abciQueryData = await tatum.rpc.abciQuery(queryParams);

console.log(abciQueryData);

// Destroying the Tatum SDK instance. This is necessary to stop any background jobs that the SDK may have started.
await tatum.destroy();
```

### Overview

The `abciQuery` method is used to query the BNB Beacon Chain application directly via ABCI. This provides a direct interface to the application layer, enabling specific data retrieval from the chain.

### Parameters

- `path` (string, required): The query path which corresponds to the type of data or information you want to retrieve. This is a required parameter and should follow a format like `"/a/b/c"`.
- `data` (string, required): The data associated with the query. This is also a required parameter and is used to provide additional context or filters for the query.
- `height` (string number, optional): The height at which to perform the query. If set to 0, it queries the latest data. This is an optional parameter.
- `prove` (boolean, optional): If set to `true`, the response will include proofs of the transactions' inclusion in the block. This is also an optional parameter.

### Return Object

The `abciQuery` method returns an object with details about the queried data from the application layer. The exact structure and content depend on the query path and data, but the return object might typically include:

- `response` (object): The response data from the ABCI query. It may contain fields like `key`, `value`, `height`, and `index`.

(Note: The exact fields in the return object might vary based on the BNB Beacon Chain's implementation and version.)
