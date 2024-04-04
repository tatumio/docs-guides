---
title: "Smart Contract Verification"
slug: "smart-contract-verification"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 25 2024 07:34:26 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 07:34:26 GMT+0000 (Coordinated Universal Time)"
---
You can verify Smart Contracts deployed using the Tatum API on Blockchain Explorers. 

> 📘 The source is available at [the following link](https://github.com/tatumio/smart-contracts/blob/master/README.md).

[block:parameters]
{
  "data": {
    "h-0": "Type",
    "h-1": "Compiler Version",
    "h-2": "Optimized Enabled",
    "h-3": "Source Code",
    "h-4": "Link",
    "0-0": "Tatum ERC-20",
    "0-1": "EVM Chains: v0.8.18+commit.87f61d96",
    "0-2": "Yes; 200 runs",
    "0-3": "Single file, MIT licensed",
    "0-4": "[TatumErc20CappedToken.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/TatumErc20CappedToken.sol)",
    "1-0": "Tatum ERC-20",
    "1-1": "TRON: tron_v0.8.18+commit.f18bedfe",
    "1-2": "Yes; 200 runs",
    "1-3": "Single file, MIT licensed",
    "1-4": "[TatumErc20CappedToken.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/TatumErc20CappedToken.sol)",
    "2-0": "Tatum ERC-721",
    "2-1": "EVM Chains: v0.8.18+commit.87f61d96",
    "2-2": "Yes; 200 runs",
    "2-3": "Single file, MIT licensed",
    "2-4": "[TatumTron721.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/TatumTron721.sol)",
    "3-0": "Tatum ERC-721",
    "3-1": "TRON: tron_v0.5.18+commit.6124c56",
    "3-2": "Yes; 200 runs",
    "3-3": "Single file, MIT licensed",
    "3-4": "[Tatum721General.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/Tatum721General.sol)",
    "4-0": "Tatum ERC-1155",
    "4-1": "EVM Chains: 0.8.7+commit.e28d00a7  \nTRON: tron_v0.5.18+commit.6124c56",
    "4-2": "Yes; 200 runs",
    "4-3": "Single file, MIT licensed",
    "4-4": "[Tatum1155.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/Tatum1155.sol)",
    "5-0": "Tatum NFT Auction",
    "5-1": "EVM Chains: 0.8.7+commit.e28d00a7  \nTRON 0.5.5 or 0.6.12",
    "5-2": "Yes; 200 runs",
    "5-3": "Single file, MIT licensed",
    "5-4": "[NftAuction.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/NftAuction.sol)",
    "6-0": "Tatum Marketplace Listing",
    "6-1": "EVM Chains: 0.8.7+commit.e28d00a7  \nTRON tron_v0.5.18+commit.6124c56",
    "6-2": "Yes; 200 runs",
    "6-3": "Single file, MIT licensed",
    "6-4": "[MarketplaceListing.sol](https://github.com/tatumio/smart-contracts/blob/master/verification/MarketplaceListing.sol)"
  },
  "cols": 5,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


### Example of a contract verified on BSC for BEP-20

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d9cd3cf-uida23TTw-qORrHtlSmGcO1feAM-r44BoA.png",
        "",
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


## Good to Know

- **BSC** - Our contract uses the compiler available at the time of publication. Newer versions have fixed some minor bugs. The impact of these bugs, however, is low and not significant.
- **SOL** - Verifying an NFT on Solana means that the NFT is a part of the collection (setting the `Verified` parameter to `true` for the NFT). To know more about Solana collections and verification, refer to the [Solana user documentation](https://docs.metaplex.com/programs/token-metadata/certified-collections).
