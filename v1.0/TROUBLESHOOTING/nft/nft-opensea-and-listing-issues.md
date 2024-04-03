---
title: "NFT - OpenSea and listing issues"
slug: "nft-opensea-and-listing-issues"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 20:10:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2024 20:10:09 GMT+0000 (Coordinated Universal Time)"
---
When minting an NFT with the **Collection** `Tatum General NFT`and interacting with Opensea, you may get the following errors:

- '`(Opensea) - Wait till confirmation`'
- '`Unexpected Error Occurred`'

For the time being, Opensea does not list NFT minted with the **Collection** `Tatum General NFT`, so the preview link will not work. This means that the NFT will not be displayed on their platform.

## Good to know

- To view NFTs, you can use an explorer such as [NFTScan](https://www.nftscan.com/).
- If you still want to use Opensea, remove the preview option from your code to avoid a compromised Experience. For further details, you may reach out OpenSea.

## Workaround

Mint NFTs [using your Collection/SmartContract](https://apidoc.tatum.io/tag/NFT-(ERC-721-or-compatible)#operation/NftDeployErc721). This provides your own `name` and `symbol`.
