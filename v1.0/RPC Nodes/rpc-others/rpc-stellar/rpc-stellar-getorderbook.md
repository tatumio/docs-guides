---
title: "getOrderBook"
slug: "rpc-stellar-getorderbook"
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

// Define parameters (Replace placeholders with actual values and remove redundant)
const params = {
  sellingAssetType: "SELLING_ASSET_TYPE",
  sellingAssetIssuer: "SELLING_ASSET_ISSUER",
  sellingAssetCode: "SELLING_ASSET_CODE",
  buyingAssetType: "BUYING_ASSET_TYPE",
  buyingAssetIssuer: "BUYING_ASSET_ISSUER",
  buyingAssetCode: "BUYING_ASSET_CODE",
  limit: 10,
};

// Retrieve an order book
const orderBook = await tatum.rpc.getOrderBook(params);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getOrderBook` method allows you to retrieve an order book for a specific trading pair on the Stellar blockchain. The order book provides information about the current bids and asks for the specified assets.

### Example use cases:

1. **Order Book Data Retrieval:**  
   Developers and applications can use this method to retrieve order book data for trading pairs on the Stellar network.

2. **Trading Pair Analysis:**  
   Traders and investors can analyze the current order book to make informed decisions about buying or selling assets.

3. **Streaming Order Book:**  
   Users can use streaming mode to listen for updates to the order book in real-time.

### Request Parameters

The `getOrderBook` method accepts a single `params` object with the following properties:

- `sellingAssetType` (string, required):  
  The asset type of the selling asset (e.g., "native" or "credit_alphanum4" or "credit_alphanum12").

- `sellingAssetIssuer` (string, optional):  
  The issuer account of the selling asset (required if the selling asset type is not "native").

- `sellingAssetCode` (string, optional):  
  The asset code of the selling asset (required if the selling asset type is not "native").

- `buyingAssetType` (string, required):  
  The asset type of the buying asset (e.g., "native" or "credit_alphanum4" or "credit_alphanum12").

- `buyingAssetIssuer` (string, optional):  
  The issuer account of the buying asset (required if the buying asset type is not "native").

- `buyingAssetCode` (string, optional):  
  The asset code of the buying asset (required if the buying asset type is not "native").

- `limit` (number, optional):  
  An optional parameter to specify the maximum number of bids and asks to return. The limit can range from 1 to 200.

### Return Object

The `getOrderBook` method returns an order book for the specified trading pair on the Stellar blockchain. The order book includes a list of bids (buy orders) and asks (sell orders) with details such as price and quantity.

(Note: The exact fields in the return object might vary based on the Stellar blockchain's implementation and version.)

```json
{
  "bids": [
    {
      "price_r": {
        "n": "10000000",
        "d": "139999999"
      },
      "price": "0.0714286",
      "amount": "24.9999990"
    },
    {
      "price_r": {
        "n": "1",
        "d": "14"
      },
      "price": "0.0714286",
      "amount": "188.0000000"
    },
    {
      "price_r": {
        "n": "1",
        "d": "15"
      },
      "price": "0.0666667",
      "amount": "230.3200000"
    },
    {
      "price_r": {
        "n": "1",
        "d": "16"
      },
      "price": "0.0625000",
      "amount": "50.0000000"
    }
  ],
  "asks": [
    {
      "price_r": {
        "n": "5000000",
        "d": "62500001"
      },
      "price": "0.0800000",
      "amount": "4.9400001"
    },
    {
      "price_r": {
        "n": "10000000",
        "d": "125000001"
      },
      "price": "0.0800000",
      "amount": "2516.5154327"
    },
    {
      "price_r": {
        "n": "2",
        "d": "25"
      },
      "price": "0.0800000",
      "amount": "3125.0000000"
    },
    {
      "price_r": {
        "n": "4",
        "d": "49"
      },
      "price": "0.0816327",
      "amount": "4593.7500000"
    }
  ],
  "base": {
    "asset_type": "native"
  },
  "counter": {
    "asset_type": "credit_alphanum4",
    "asset_code": "BB1",
    "asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN"
  }
}
```
