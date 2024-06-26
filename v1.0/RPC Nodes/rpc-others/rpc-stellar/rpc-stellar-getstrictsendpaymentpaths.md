---
title: "getStrictSendPaymentPaths"
slug: "rpc-stellar-getstrictsendpaymentpaths"
excerpt: "Stellar RPC"
hidden: false
metadata: 
  description: "Stellar RPC"
  image: []
  keywords: "stellar, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 14:36:35 GMT+0000 (Coordinated Universal Time)"
---
### How to use it

```typescript
// Import required libraries and modules from Tatum SDK
import { TatumSDK, Stellar, Network } from "@tatumio/tatum";

// Initialize the Tatum SDK for Stellar
const tatum = await TatumSDK.init<Stellar>({ network: Network.STELLAR });

// Define parameters (Replace placeholders with actual values and remove redundant)
const params = {
  sourceAccount: "SOURCE_ACCOUNT",
  sourceAssets: ["SOURCE_ASSET_1", "SOURCE_ASSET_2"],
  sourceAssetType: "SOURCE_ASSET_TYPE",
  sourceAssetIssuer: "SOURCE_ASSET_ISSUER",
  sourceAssetCode: "SOURCE_ASSET_CODE",
  sourceAmount: "SOURCE_AMOUNT",
  destinationAccount: "DESTINATION_ACCOUNT",
  destinationAssets: ["DESTINATION_ASSET_1", "DESTINATION_ASSET_2"],
};

// List strict send payment paths
const paymentPaths = await tatum.rpc.getStrictSendPaymentPaths(params);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getStrictSendPaymentPaths` method allows you to list the payment paths a payment can take based on the amount of a source asset you want to send. The source asset amount remains constant, and the type and amount of the asset received vary based on offers in the order books.

### Example use cases:

1. **Payment Path Analysis:**  
   Developers and applications can use this method to analyze and retrieve payment paths based on specific source amounts and assets.

2. **Payment Path Selection:**  
   Users can select the optimal payment path to send a specific source amount and receive a variable amount of a destination asset.

3. **Streaming Payment Paths:**  
   Users can use streaming mode to listen for updates to payment paths in real-time.

### Request Parameters

The `getStrictSendPaymentPaths` method accepts a `params` object with the following properties:

- `sourceAccount` (string, optional):  
  The source account from which to start the payment path search.

- `sourceAssets` (array of strings, optional):  
  An array of source assets that the sender wants to send.

- `sourceAssetType` (string, required):  
  The asset type of the source asset (e.g., "native" or "credit_alphanum4" or "credit_alphanum12").

- `sourceAssetIssuer` (string, optional):  
  The issuer account of the source asset (required if the source asset type is not "native").

- `sourceAssetCode` (string, optional):  
  The asset code of the source asset (required if the source asset type is not "native").

- `sourceAmount` (string, required):  
  The constant amount of the source asset that the sender wants to send.

- `destinationAccount` (string, required if destinationAssets are not present):  
  The destination account to which the recipient can receive the assets.

- `destinationAssets` (array of strings, required if destinationAccount is not present):  
  An array of destination assets that the recipient can receive.

### Return Object

The `getStrictSendPaymentPaths` method returns a list of payment paths from the source assets to the destination asset that satisfy the specified source amount. Each path includes details about the source and destination assets, as well as the offers in the order books that make up the path.

(Note: The exact fields in the return object might vary based on the Stellar blockchain's implementation and version.)

```json
{
  "value": {
    "_embedded": {
      "records": [
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "BRL",
          "source_asset_issuer": "GDVKY2GU2DRXWTBEYJJWSFXIGBZV6AZNBVVSUHEPZI54LIS6BA7DVVSP",
          "source_amount": "400.0000000",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "87.6373649",
          "path": [
            {
              "asset_type": "native"
            }
          ]
        },
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "BRL",
          "source_asset_issuer": "GDVKY2GU2DRXWTBEYJJWSFXIGBZV6AZNBVVSUHEPZI54LIS6BA7DVVSP",
          "source_amount": "400.0000000",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "36.0841597",
          "path": [
            {
              "asset_type": "native"
            },
            {
              "asset_type": "credit_alphanum4",
              "asset_code": "EURT",
              "asset_issuer": "GAP5LETOV6YIE62YAM56STDANPRDO7ZFDBGSNHJQIYGGKSMOZAHOOS2S"
            }
          ]
        }
      ]
    }
  }
}
```
