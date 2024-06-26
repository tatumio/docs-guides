---
title: "account_nfts"
slug: "rpc-xrp-account_nfts"
excerpt: "XRP RPC"
hidden: false
metadata: 
  description: "XRP RPC"
  image: []
  keywords: "xrp, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 13:09:04 GMT+0000 (Coordinated Universal Time)"
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

const res = await tatum.rpc.accountNfts('rsuHaTvJh1bDmDoxX9QcKP7HEBSBt4XsHx', {
  ledger_index: 'validated',
  limit: 100
})

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```

### Overview

The `accountNfts` method returns a list of Non-Fungible Tokens (NFTs) objects for a specific account. This method is useful when you want to retrieve all the NFTs owned by a particular account. The method is available due to the NonFungibleTokensV1\_1 amendment.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/NWEmLae",
  "href": "https://codepen.io/tatum-devrel/pen/NWEmLae",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

#### Main Parameters

- `account`: A unique identifier for the account, most commonly the account's Address.

#### Optional Parameters (part of `options?: Ledger & Pagination` object)

- `ledger_hash`: A 20-byte hex string for the ledger version to use.
- `ledger_index`: The ledger index of the ledger to use, or a shortcut string to choose a ledger automatically.
- `limit`: Limit the number of token pages to retrieve. Each page can contain up to 32 NFTs. The limit value cannot be lower than 20 or more than 400. The default is 100.
- `marker`: Value from a previous paginated response. Resume retrieving data where that response left off.

### Return Object

The returned object will be a successful result containing the account's address and an array of NFT objects. 

Here are the fields in the response:

- `Flags`: This is a number that represents a bit-map of boolean flags enabled for this NFToken. This can provide additional information about the token, such as whether it's transferable, mintable, etc. The specific flags and their meanings can vary based on the implementation.
- `Issuer`: This is a string that represents the address of the account that issued this NFToken. It's the unique identifier of the account that created and originally owned this token.
- `NFTokenID`: This is a string that represents the unique identifier of this NFToken, in hexadecimal. This is typically a unique identifier that differentiates this token from all others on the ledger.
- `NFTokenTaxon`: This is a number that represents the unscrambled version of this token's taxon. Several tokens with the same taxon might represent instances of a limited series. This can be used to group similar tokens together.
- `URI`: This is a string that represents the URI data associated with this NFToken, in hexadecimal. This often points to a resource that has more information about the token, such as an image, audio file, or a webpage.
- `nft_serial`: This is a number that represents the token sequence number of this NFToken, which is unique for its issuer. This can be used to determine the order in which the tokens were created.

### JSON-RPC Request Example

```json
{
  "method": "account_nfts",
  "params": [
    {
      "account": "rsuHaTvJh1bDmDoxX9QcKP7HEBSBt4XsHx",
      "ledger_index": "validated",
      "limit": 100
    }
  ]
}
```

### JSON-RPC Response Example

```json
{
  "result": {
    "account": "rsuHaTvJh1bDmDoxX9QcKP7HEBSBt4XsHx",
    "account_nfts": [
      {
        "Flags": 1,
        "Issuer": "rGJUF4PvVkMNxG6Bg6AKg3avhrtQyAffcm",
        "NFTokenID": "00010000A7CAD27B688D14BA1A9FA5366554D6ADCF9CE0875B974D9F00000004",
        "NFTokenTaxon": 0,
        "URI": "697066733A2F2F62616679626569676479727A74357366703775646D37687537367568377932366E6634646675796C71616266336F636C67747179353566627A6469",
        "nft_serial": 4
      },
      // More NFTs...
    ],
    "status": "success",
    "validated": true
  }
}
```
