---
title: "getAccountOperations"
slug: "rpc-stellar-getaccountoperations"
excerpt: "Stellar RPC"
hidden: false
metadata: 
  description: "Stellar RPC"
  image: []
  keywords: "stellar, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:30:57 GMT+0000 (Coordinated Universal Time)"
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
  cursor: "now",
  order: "asc",
  limit: 10,
  includeFailed: true,
  join: true,
};

// Retrieve successful operations for a given account
const operations = await tatum.rpc.getAccountOperations(params);

// Log the list of operations
console.log("Account Operations:", operations);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getAccountOperations` method allows you to retrieve successful operations for a given account on the Stellar blockchain. You can use this endpoint in streaming mode to listen for new operations for the specified account as they are added to the Stellar ledger. When called in streaming mode, Horizon will start at the earliest known operation unless a cursor is set, in which case it will start from that cursor. Setting the cursor value to 'now' allows you to stream operations created since your request time.

### Request Parameters

The `getAccountOperations` method accepts the following request parameters:

- `accountId` (string, required):  
  The unique identifier (account ID) of the account for which you want to retrieve operations.

- `cursor` (string, optional):  
  A cursor value that determines the starting point for retrieving operations. Set it to 'now' to stream operations created since your request time.

- `order` (string, optional):  
  A designation of the order in which records should appear. Options include 'asc' (ascending) or 'desc' (descending). If this argument isn’t set, it defaults to 'asc'.

- `limit` (number, optional):  
  The maximum number of records returned. It defines the number of operations to fetch in a single request.

- `includeFailed` (boolean, optional):  
  A flag to indicate whether to include failed operations in the results. Set to `true` to include failed operations.

- `join` (boolean, optional):  
  A flag to indicate whether to join operation data with relevant accounts. Set to `true` to join operation data with accounts.

### Return Object

The `getAccountOperations` method returns a JSON object containing the list of operations associated with the specified account. Each operation may represent a variety of actions such as payments, account creations, and more.

(Note: The exact fields in the return object might vary based on the Stellar blockchain's implementation and version.)

```json
{
    "_links": {
        "self": {
            "href": "https://01-vinthill-068-01.rpc.tatum.io/accounts/GA2224DCGO3WHC4EALA2PR2BZEMAYZPBPTHS243ZYYWQMBWRPJSZH5A6/operations?cursor=&limit=10&order=asc"
        },
        "next": {
            "href": "https://01-vinthill-068-01.rpc.tatum.io/accounts/GA2224DCGO3WHC4EALA2PR2BZEMAYZPBPTHS243ZYYWQMBWRPJSZH5A6/operations?cursor=216532408316960769&limit=10&order=asc"
        },
        "prev": {
            "href": "https://01-vinthill-068-01.rpc.tatum.io/accounts/GA2224DCGO3WHC4EALA2PR2BZEMAYZPBPTHS243ZYYWQMBWRPJSZH5A6/operations?cursor=216517620744060929&limit=10&order=desc"
        }
    },
    "_embedded": {
        "records": [
            {
                "_links": {
                    "self": {
                        "href": "https://01-vinthill-068-01.rpc.tatum.io/operations/216517620744060929"
                    },
                    "transaction": {
                        "href": "https://01-vinthill-068-01.rpc.tatum.io/transactions/8ed978ce9f9f2cfe245470a06e9d0ce178f0cc602fd2b8d5e6047192e13d7475"
                    },
                    "effects": {
                        "href": "https://01-vinthill-068-01.rpc.tatum.io/operations/216517620744060929/effects"
                    },
                    "succeeds": {
                        "href": "https://01-vinthill-068-01.rpc.tatum.io/effects?order=desc&cursor=216517620744060929"
                    },
                    "precedes": {
                        "href": "https://01-vinthill-068-01.rpc.tatum.io/effects?order=asc&cursor=216517620744060929"
                    }
                },
                "id": "216517620744060929",
                "paging_token": "216517620744060929",
                "transaction_successful": true,
                "source_account": "GBOXZWWNZL3MQ7EP3KNL66WBVE4NH2UOLCMFKEKZFYQT5MOP2JDKENIZ",
                "type": "create_claimable_balance",
                "type_i": 14,
                "created_at": "2024-02-17T14:03:50Z",
                "transaction_hash": "8ed978ce9f9f2cfe245470a06e9d0ce178f0cc602fd2b8d5e6047192e13d7475",
                "sponsor": "GBOXZWWNZL3MQ7EP3KNL66WBVE4NH2UOLCMFKEKZFYQT5MOP2JDKENIZ",
                "asset": "ENIZ:GDLMUA4ZQSU3LMKEW7LETSIYLYMATTGVPXCHFRRTGQTF6K55XOQIENIZ",
                "amount": "5000.0000000",
                "claimants": [
                    {
                        "destination": "GA2224DCGO3WHC4EALA2PR2BZEMAYZPBPTHS243ZYYWQMBWRPJSZH5A6",
                        "predicate": {
                            "unconditional": true
                        }
                    },
                    {
                        "destination": "GBOXZWWNZL3MQ7EP3KNL66WBVE4NH2UOLCMFKEKZFYQT5MOP2JDKENIZ",
                        "predicate": {
                            "unconditional": true
                        }
                    }
                ]
            }
```
