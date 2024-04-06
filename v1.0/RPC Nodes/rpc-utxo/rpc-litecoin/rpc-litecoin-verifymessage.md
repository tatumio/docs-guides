---
title: "verifymessage"
slug: "rpc-litecoin-verifymessage"
excerpt: "Litecoin RPC"
hidden: false
metadata: 
  description: "Litecoin RPC"
  image: []
  keywords: "litecoin, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Apr 02 2024 08:40:59 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

{% tabs %}  
{% tab title="TypeScript/JavaScript" %}  
{% code overflow="wrap" lineNumbers="true" %}

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Litecoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Litecoin>({network: Network.LITECOIN})

const result = await tatum.rpc.verifyMessage( "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa", "HxK7Mw0K6Uox7iGcOe9v9Ll+OZzG7TjTkeTJCD7VHw4yKP4O4a4gFtgm9XNmxfH1tK7JRgYrP/+20xP/ek8iQ2E=", "Hello, this is a signed message.")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

{% endcode %}  
{% endtab %}  
{% endtabs %}

### Overview <a href="#overview" id="overview"></a>

`verifymessage` is an Litecoin RPC method that allows users to verify a signed message using a Litecoin address. This method can be used to confirm the authenticity of a message by verifying that the signature was created by the owner of the address, without revealing the private key. Use cases include proving ownership of an address, verifying the content of a message, or validating communications within a trustless system.

### Parameters <a href="#parameters" id="parameters"></a>

The `verifymessage` method accepts three required parameters:

- `address` (string, required): The Litecoin address that supposedly signed the message.
- `signature` (string, required): The base64-encoded signature of the message.
- `message` (string, required): The message that was signed.

### Return Object <a href="#return-object" id="return-object"></a>

The `verifymessage` method returns a single boolean value:

- `isvalid` (boolean): Indicates if the signature is valid for the given message and address

### JSON Examples

Request example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "verifymessage",
  "params": [
    "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
"HxK7Mw0K6Uox7iGcOe9v9Ll+OZzG7TjTkeTJCD7VHw4yKP4O4a4gFtgm9XNmxfH1tK7JRgYrP/+20xP/ek8iQ2E=",
    "Hello, this is a signed message."
  ]
}
```

{% endcode %}

Response example:

{% code overflow="wrap" lineNumbers="true" %}

```json
{
  "result": false,
  "error": null,
  "id": 1
}
```

{% endcode %}

\\
