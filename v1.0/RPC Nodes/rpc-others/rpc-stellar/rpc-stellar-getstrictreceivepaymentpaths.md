---
title: "getStrictReceivePaymentPaths"
slug: "rpc-stellar-getstrictreceivepaymentpaths"
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
  sourceAccount: "SOURCE_ACCOUNT",
  sourceAssets: ["CODE:ISSUER_ACCOUNT", "CODE:ISSUER_ACCOUNT2"],
  destinationAssetType: "DESTINATION_ASSET_TYPE",
  destinationAssetIssuer: "DESTINATION_ASSET_ISSUER",
  destinationAssetCode: "DESTINATION_ASSET_CODE",
  destinationAmount: "DESTINATION_AMOUNT",
};

// List strict receive payment paths
const paymentPaths = await tatum.rpc.listStrictReceivePaymentPaths(params);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `listStrictReceivePaymentPaths` method allows you to list the payment paths a payment can take based on the amount of an asset you want the recipient to receive. The destination asset amount remains constant, and the type and amount of the source asset sent varies based on offers in the order books. The methods requires either a list of source assets or a source account. Both fields cannot be present.

### Example use cases:

1. **Payment Path Analysis:**  
   Developers and applications can use this method to analyze and retrieve payment paths based on specific destination amounts and assets.

2. **Payment Path Selection:**  
   Users can select the optimal payment path to ensure that a recipient receives a specific amount of a destination asset.

3. **Streaming Payment Paths:**  
   Users can use streaming mode to listen for updates to payment paths in real-time.

### Request Parameters

The `listStrictReceivePaymentPaths` method accepts a `params` object with the following properties:

- `sourceAccount` (string, required if sourceAssets are not selected):  
  The source account from which to start the payment path search.

- `sourceAssets` (array of strings, required if sourceAccount is not selected):  
  An array of source assets that are available to the sender. A comma-separated list of assets available to the sender. Any returned path must start with an asset in this list. Each asset is formatted as CODE:ISSUER_ACCOUNT. For example: USD:GDUKMGUGDZQK6YHYA5Z6AY2G4XDSZPSZ3SW5UN3ARVMO6QSRDWP5YLEX. Using either source_account or source_assets as an argument is required for strict receive path payments.

- `destinationAssetType` (string, required):  
  The asset type of the destination asset (e.g., "native" or "credit_alphanum4" or "credit_alphanum12").

- `destinationAssetIssuer` (string, optional):  
  The issuer account of the destination asset (required if the destination asset type is not "native").

- `destinationAssetCode` (string, optional):  
  The asset code of the destination asset (required if the destination asset type is not "native").

- `destinationAmount` (string, required):  
  The amount of the destination asset that the recipient should receive.

### Return Object

The `listStrictReceivePaymentPaths` method returns a list of payment paths from the source assets to the destination asset that satisfy the specified destination amount. Each path includes details about the source and destination assets, as well as the offers in the order books that make up the path.

(Note: The exact fields in the return object might vary based on the Stellar blockchain's implementation and version.)

```json
{
  "value": {
    "_embedded": {
      "records": [
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "CNY",
          "source_asset_issuer": "GAREELUB43IRHWEASCFBLKHURCGMHE5IF6XSE7EXDLACYHGRHM43RFOX",
          "source_amount": "28.9871131",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "5.0000000",
          "path": [
            {
              "asset_type": "credit_alphanum4",
              "asset_code": "XCN",
              "asset_issuer": "GCNY5OXYSY4FKHOPT2SPOQZAOEIGXB5LBYW3HVU3OWSTQITS65M5RCNY"
            },
            {
              "asset_type": "native"
            }
          ]
        },
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "CNY",
          "source_asset_issuer": "GAREELUB43IRHWEASCFBLKHURCGMHE5IF6XSE7EXDLACYHGRHM43RFOX",
          "source_amount": "29.0722784",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "5.0000000",
          "path": [
            {
              "asset_type": "credit_alphanum4",
              "asset_code": "ULT",
              "asset_issuer": "GC76RMFNNXBFDSJRBXCABWLHXDK4ITVQSMI56DC2ZJVC3YOLLPCKKULT"
            },
            {
              "asset_type": "native"
            }
          ]
        },
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "CNY",
          "source_asset_issuer": "GAREELUB43IRHWEASCFBLKHURCGMHE5IF6XSE7EXDLACYHGRHM43RFOX",
          "source_amount": "29.4000002",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "5.0000000",
          "path": [
            {
              "asset_type": "native"
            }
          ]
        },
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "CNY",
          "source_asset_issuer": "GAREELUB43IRHWEASCFBLKHURCGMHE5IF6XSE7EXDLACYHGRHM43RFOX",
          "source_amount": "31.8955888",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "5.0000000",
          "path": [
            {
              "asset_type": "credit_alphanum4",
              "asset_code": "USD",
              "asset_issuer": "GBUYUAI75XXWDZEKLY66CFYKQPET5JR4EENXZBUZ3YXZ7DS56Z4OKOFU"
            },
            {
              "asset_type": "native"
            }
          ]
        },
        {
          "source_asset_type": "credit_alphanum4",
          "source_asset_code": "CNY",
          "source_asset_issuer": "GAREELUB43IRHWEASCFBLKHURCGMHE5IF6XSE7EXDLACYHGRHM43RFOX",
          "source_amount": "34.7086084",
          "destination_asset_type": "credit_alphanum4",
          "destination_asset_code": "BB1",
          "destination_asset_issuer": "GD5J6HLF5666X4AZLTFTXLY46J5SW7EXRKBLEYPJP33S33MXZGV6CWFN",
          "destination_amount": "5.0000000",
          "path": [
            {
              "asset_type": "credit_alphanum4",
              "asset_code": "USD",
              "asset_issuer": "GDUKMGUGDZQK6YHYA5Z6AY2G4XDSZPSZ3SW5UN3ARVMO6QSRDWP5YLEX"
            },
            {
              "asset_type": "native"
            }
          ]
        }
      ]
    }
  }
}
```
