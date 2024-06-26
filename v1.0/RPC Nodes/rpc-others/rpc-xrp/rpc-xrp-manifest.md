---
title: "manifest"
slug: "rpc-xrp-manifest"
excerpt: "XRP RPC"
hidden: false
metadata: 
  description: "XRP RPC"
  image: []
  keywords: "xrp, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:06 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it

```javascript
// yarn add @tatumio/tatum

import { TatumSDK, Xrp, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Xrp>({network: Network.XRP})

const res = await tatum.rpc.manifest('nHUFE9prPXPrHcG3SkwP1UzAQbSphqyQkQK9ATXLZsfkezhhda3p')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

### Overview

The `manifest` method is a specialized RPC method provided by the Ripple (XRP) blockchain to report the current "manifest" information for a given validator's public key. The "manifest" is a block of data that authorizes an ephemeral signing key with a signature from the validator's master key pair.

This method is particularly useful in scenarios where one needs to verify the authenticity of a validator. It could also be used to gather information about a validator's association with a domain, its ephemeral and master keys, and the sequence number of its manifest.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/PoxgXRB",
  "href": "https://codepen.io/tatum-devrel/pen/PoxgXRB",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

The `manifest` method accepts a single parameter:

- `publicKey`: The base58-encoded public key of the validator to look up. This can be the master public key or ephemeral public key.

### Return Object

The `manifest` method returns an object with the following fields:

- `details`: An object containing detailed information about the manifest. This field is omitted if the server does not have a manifest for the `public_key` from the request. The details object has the following fields:
  - `domain`: The domain name this validator claims to be associated with. If the manifest does not contain a domain, this is an empty string.
  - `ephemeral_key`: The ephemeral public key for this validator, in base58.
  - `master_key`: The master public key for this validator, in base58.
  - `seq`: The sequence number of this manifest. This number increases whenever the validator operator updates the validator's token to rotate ephemeral keys or change settings.
- `manifest`: The full manifest data in base64 format. This data is serialized to binary before being base64-encoded. This field is omitted if the server does not have a manifest for the `public_key` from the request.
- `requested`: The `public_key` from the request.
- `status`: The status of the request, typically "success".

### JSON-RPC Request Example

```json
{
    "method": "manifest",
    "params": [{
        "public_key":"nHUFE9prPXPrHcG3SkwP1UzAQbSphqyQkQK9ATXLZsfkezhhda3p"
    }]
}
```

### JSON-RPC Response Example

```json
{
  "result": {
    "details": {
      "domain": "",
      "ephemeral_key": "n9J67zk4B7GpbQV5jRQntbgdKf7TW6894QuG7qq1rE5gvjCu6snA",
      "master_key": "nHUFE9prPXPrHcG3SkwP1UzAQbSphqyQkQK9ATXLZsfkezhhda3p",
      "seq": 1
    },
    "manifest": "JAAAAAFxIe3AkJgOyqs3y+UuiAI27Ff3Mrfbt8e7mjdo06bnGEp5XnMhAhRmvCZmWZXlwShVE9qXs2AVCvhVuA/WGYkTX/vVGBGwdkYwRAIgGnYpIGufURojN2cTXakAM7Vwa0GR7o3osdVlZShroXQCIH9R/Lx1v9rdb4YY2n5nrxdnhSSof3U6V/wIHJmeao5ucBJA9D1iAMo7YFCpb245N3Czc0L1R2Xac0YwQ6XdGT+cZ7yw2n8JbdC3hH8Xu9OUqc867Ee6JmlXtyDHzBdY/hdJCQ==",
    "requested": "nHUFE9prPXPrHcG3SkwP1UzAQbSphqyQkQK9ATXLZsfkezhhda3p",
    "status": "success"
  }
}
```
