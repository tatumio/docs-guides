---
title: "validateaddress"
slug: "rpc-dogecoin-validateaddress"
excerpt: "Dogecoin RPC"
category: 65c5e93c623cad004b45d505
hidden: false
metadata: 
  description: "Dogecoin RPC"
  image: []
  keywords: "dogecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]{"html":"<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"}[/block]

### How to use it

{% tabs %}
{% tab title="TypeScript/JavaScript" %}
{% code overflow="wrap" lineNumbers="true" %}
```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Dogecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Dogecoin>({network: Network.DOGECOIN})

const result = await tatum.rpc.validateAddress("1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Overview <a href="#overview" id="overview"></a>

`validateaddress` is an Dogecoin RPC method that enables users to verify if a given Dogecoin address is valid. This method provides important information about the address, such as its type and whether it's a spendable or watch-only address. It can be particularly useful in applications where address validation is necessary before performing transactions or when dealing with user-generated addresses to ensure their validity.

{% embed url="https://codepen.io/Jan-Musil-the-lessful/pen/OJaqWLp?editors=1111" %}

### Parameters <a href="#parameters" id="parameters"></a>

The `validateaddress` method accepts one required parameter:

* `address` (string, required): The Dogecoin address to be validated.

### Return Object <a href="#return-object" id="return-object"></a>

The `validateaddress` method returns an object with the following fields:

* `isvalid` (boolean): Indicates if the supplied address is valid.
* `address` (string): The validated Dogecoin address.
* `scriptPubKey` (string): The hex-encoded scriptPubKey generated by the address.
* `isscript` (boolean): Indicates if the address is a script address (P2SH).
* `iswitness` (boolean): Indicates if the address is a witness address (P2WPKH or P2WSH).
* `witness_version` (numeric, optional): The version number of the witness program, if applicable.
* `witness_program` (string, optional): The hex value of the witness program, if applicable.
* `isspendable` (boolean): Indicates if the address is spendable (has the private key).
* `iswatchonly` (boolean): Indicates if the address is watch-only (wallet has the public key but not the private key).
* `iscompressed` (boolean, optional): Indicates if the associated public key is compressed.
* `account` (string, optional): DEPRECATED. The account associated with the address, if any. Example:

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "validateaddress",
  "params": [
    "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa"
  ]
}
```
{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}
```json
{
    "result": {
        "isvalid": true,
        "address": "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
        "scriptPubKey": "76a91462e907b15cbf27d5425399ebf6f0fb50ebb88f1888ac",
        "isscript": false,
        "iswitness": false
    },
    "error": null,
    "id": 1
}
```
{% endcode %}

\