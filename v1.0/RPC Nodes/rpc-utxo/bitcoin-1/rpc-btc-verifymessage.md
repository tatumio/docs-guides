---
title: "verifymessage"
slug: "rpc-btc-verifymessage"
excerpt: "Bitcoin RPC"
category: 65a9112c408e3a004ae466df
hidden: false
metadata: 
  image: []
  keywords: "bitcoin, rpc"
  robots: "index"
createdAt: "Wed Mar 27 2024 07:17:22 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Apr 03 2024 08:56:29 GMT+0000 (Coordinated Universal Time)"
---
## Overview

The `verifymessage` is a Bitcoin RPC method that allows users to verify a signed message using a Bitcoin address. This method can be used to confirm the authenticity of a message by verifying that the signature was created by the owner of the address, without revealing the private key. Use cases include proving ownership of an address, verifying the content of a message, or validating communications within a trustless system.

## Parameters

The `verifymessage` method accepts three required parameters:

`address`: The Bitcoin address that supposedly signed the message.

`signature`: The base64-encoded signature of the message.

`message`: The message that was signed.

## Returns

The `verifymessage` method returns a single boolean value:

`isvalid`: Indicates if the signature is valid for the given message and address

## Request Example

```curl cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/bitcoin-mainnet/' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {API_KEY}' \
--data '{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "verifymessage",
  "params": [
    "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
"HxK7Mw0K6Uox7iGcOe9v9Ll+OZzG7TjTkeTJCD7VHw4yKP4O4a4gFtgm9XNmxfH1tK7JRgYrP/+20xP/ek8iQ2E=",
    "Hello, this is a signed message."
  ]
}'
```
```typescript JS SDK
// yarn add @tatumio/tatum

import { TatumSDK, Bitcoin, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN})

const result = await tatum.rpc.verifyMessage( "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa", "HxK7Mw0K6Uox7iGcOe9v9Ll+OZzG7TjTkeTJCD7VHw4yKP4O4a4gFtgm9XNmxfH1tK7JRgYrP/+20xP/ek8iQ2E=", "Hello, this is a signed message.")

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```
