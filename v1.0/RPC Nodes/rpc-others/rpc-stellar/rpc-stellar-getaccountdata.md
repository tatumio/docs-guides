---
title: "getAccountData"
slug: "rpc-stellar-getaccountdata"
excerpt: "Stellar RPC"
hidden: false
metadata: 
  description: "Stellar RPC"
  image: []
  keywords: "stellar, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Apr 05 2024 16:39:11 GMT+0000 (Coordinated Universal Time)"
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

// Define input parameters as an object (Replace placeholders with actual values and remove redundant)
const params = {
  accountId: "YOUR_ACCOUNT_ID",
  key: "YOUR_DATA_KEY",
};

// Retrieve data for a specific key of a given account
const data = await tatum.rpc.getAccountData(params);

// Log the data value
console.log("Account Data:", data.value);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountData` method allows you to retrieve a single data value for a specific key of a given account on the Stellar blockchain. Please note that the content and structure of the data returned can vary based on the specific use case and applications interacting with the Stellar blockchain.

### Request Parameters

The `getAccountData` method accepts the following request parameters:

- `accountId` (string, required):  
  The unique identifier (account ID) of the account for which you want to retrieve data.

- `key` (string, required):  
  The data key for which you want to retrieve the corresponding value.

### Return Object

The `getAccountData` method returns a JSON object with account data:

`value` (string):  
The value associated with the specified data key for the given account.
