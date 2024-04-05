---
title: "getOffer"
slug: "rpc-stellar-getOffer"
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
const offerId = "OFFER_ID";

// Retrieve information on a specific offer
const offerInfo = await tatum.rpc.getOffer(offerId);

// Always destroy the Tatum SDK instance when done to stop any background processes
await tatum.destroy();
```

### Overview

The `getOffer` method allows you to retrieve information on a specific offer by providing the offer's unique identifier.

### Example use cases:

1. **Offer Information Retrieval:**
   Developers and applications can use this method to retrieve detailed information about a specific offer on the Stellar network.

2. **Offer Verification:**
   Users can verify the details of an offer, including the asset types, issuer, code, and other relevant information.

### Request Parameters

The `getOffer` method accepts the following parameter:

- `offerId` (string, required):
  The unique identifier of the offer for which you want to retrieve information.

### Return Object

The `getOffer` method returns detailed information about the specified offer on the Stellar blockchain. The response includes data such as the offer ID, sponsor, seller, buying asset, selling asset, and more.

(Note: The exact fields in the return object might vary based on the Stellar blockchain's implementation and version.)

```json
{
  "_links": {
    "self": {
      "href": "https://01-vinthill-068-01.rpc.tatum.io/offers/2"
    },
    "offer_maker": {
      "href": "https://01-vinthill-068-01.rpc.tatum.io/accounts/GBPO4N6XOLOLW2EV6X2AEQMLKOBH3WF2IJCZEQU65SVVSN4JD44WORKD"
    }
  },
  "id": "2",
  "paging_token": "2",
  "seller": "GBPO4N6XOLOLW2EV6X2AEQMLKOBH3WF2IJCZEQU65SVVSN4JD44WORKD",
  "selling": {
    "asset_type": "credit_alphanum4",
    "asset_code": "CHP",
    "asset_issuer": "GDW3CNKSP5AOTDQ2YCKNGC6L65CE4JDX3JS5BV427OB54HCF2J4PUEVG"
  },
  "buying": {
    "asset_type": "credit_alphanum4",
    "asset_code": "BEER",
    "asset_issuer": "GDW3CNKSP5AOTDQ2YCKNGC6L65CE4JDX3JS5BV427OB54HCF2J4PUEVG"
  },
  "amount": "1.9991292",
  "price_r": {
    "n": 1903,
    "d": 20
  },
  "price": "95.1500000",
  "last_modified_ledger": 50044488,
  "last_modified_time": null
}
```
