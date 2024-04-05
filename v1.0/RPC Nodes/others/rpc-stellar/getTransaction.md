---
title: "getTransaction"
slug: "rpc-stellar-getTransaction"
excerpt: "Stellar RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Stellar RPC"
  image: []
  keywords: "stellar, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Stellar, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Stellar
const tatum = await TatumSDK.init<Stellar>({ network: Network.STELLAR });

// Define parameters (Replace placeholders with actual values and remove redundant)
const transactionHash = "YOUR_TRANSACTION_HASH";

// Retrieve a specific transaction by its hash
const transaction = await tatum.rpc.getTransaction(transactionHash);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getTransaction` method allows you to retrieve information about a specific transaction on the Stellar blockchain. You can specify the transaction you want to retrieve by providing its unique transaction hash.

### Example use cases:

1. **Transaction Details:**
   Developers and applications can use this method to fetch detailed information about a specific transaction, including its source, destination, amount, and other transaction-specific data.

2. **Transaction Verification:**
   Users can use this method to verify and validate specific transactions on the Stellar network.

3. **Auditing and Reporting:**
   Platform administrators can access transaction data for auditing and reporting purposes.

### Request Parameters

The `getTransaction` method accepts a `transactionHash` parameter, which is a string representing the unique hash of the transaction you want to retrieve.

- `transactionHash` (string, required):
  The unique hash of the transaction you want to retrieve.

### Return Object

The `getTransaction` method returns detailed information about the specified transaction on the Stellar blockchain. The response includes data such as the transaction ID, source account, destination account, amount, fee, and other transaction-specific details.

(Note: The exact fields in the return object might vary based on the Stellar blockchain's implementation and version.)

```json
{
  "value": {
    "_links": {
      "self": {
        "href": "https://horizon.stellar.org/transactions/5ebd5c0af4385500b53dd63b0ef5f6e8feef1a7e1c86989be3cdcce825f3c0cc"
      },
      "account": {
        "href": "https://horizon.stellar.org/accounts/GDI5EK4HNMBHJJQGP3GUXQJIIOHU2CJO3LABPWD6WYSPJZP5NP67TMNN"
      },
      "ledger": {
        "href": "https://horizon.stellar.org/ledgers/27963785"
      },
      "operations": {
        "href": "https://horizon.stellar.org/transactions/5ebd5c0af4385500b53dd63b0ef5f6e8feef1a7e1c86989be3cdcce825f3c0cc/operations{?cursor,limit,order}",
        "templated": true
      },
      "effects": {
        "href": "https://horizon.stellar.org/transactions/5ebd5c0af4385500b53dd63b0ef5f6e8feef1a7e1c86989be3cdcce825f3c0cc/effects{?cursor,limit,order}",
        "templated": true
      },
      "precedes": {
        "href": "https://horizon.stellar.org/transactions?order=asc&cursor=120103542047408128"
      },
      "succeeds": {
        "href": "https://horizon.stellar.org/transactions?order=desc&cursor=120103542047408128"
      }
    },
    "id": "5ebd5c0af4385500b53dd63b0ef5f6e8feef1a7e1c86989be3cdcce825f3c0cc",
    "paging_token": "120103542047408128",
    "successful": true,
    "hash": "5ebd5c0af4385500b53dd63b0ef5f6e8feef1a7e1c86989be3cdcce825f3c0cc",
    "ledger": 27963785,
    "created_at": "2020-01-28T10:03:33Z",
    "source_account": "GDI5EK4HNMBHJJQGP3GUXQJIIOHU2CJO3LABPWD6WYSPJZP5NP67TMNN",
    "source_account_sequence": "65046128646685383",
    "fee_charged": 100,
    "max_fee": 100,
    "operation_count": 1,
    "envelope_xdr": "hex data",
    "result_xdr": "AAAAAAAAAGQAAAAAAAAAAQAAAAAAAAABAAAAAAAAAAA=",
    "result_meta_xdr": "hex data",
    "fee_meta_xdr": "hex data"
  }
}
```
