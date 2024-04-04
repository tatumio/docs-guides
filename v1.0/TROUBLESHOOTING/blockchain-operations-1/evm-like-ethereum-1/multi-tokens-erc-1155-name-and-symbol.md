---
title: "Multi tokens (ERC-1155) name and symbol"
slug: "multi-tokens-erc-1155-name-and-symbol"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 11 2024 21:50:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 21:50:52 GMT+0000 (Coordinated Universal Time)"
---
By definition, `name` and `symbol` found in the ERC-20 and ERC-721 standards are not available.

### Name

The name function (for human-readable asset names, on-chain) was removed from the standard to allow the Metadata JSON to be the definitive asset name and reduce duplication of data.

### Symbol

The symbol function was not included since creators did not believe this is a globally useful piece of data to identify a generic virtual item/asset and is also prone to collisions. Short-hand symbols are used in tickers and currency trading, but they aren’t as useful outside of that space.

> 📘 Find additional information ar [the following link](https://eips.ethereum.org/EIPS/eip-1155#rationale).

## Good to know

To get `name` and `symbol`, you need to deploy and use your own smart contract via [the following endpoint](https://apidoc.tatum.io/tag/Multi-Tokens-(ERC-1155-or-compatible)/#operation/DeployMultiToken).

The mentioned endpoint contains the parameter `URI` on which you will be able to enter an IPFS URL from an uploaded \*.json file in the same way you would do when minting an ERC-712 NFT.

### Example:

```json JSON
//Endpoint: /v3/multitoken/deploy, where:

"uri": "https://bafkreiebg3ugqtumak2ueyf2j2sbggt47hxjvbozkxbgyssebufmbgp3fa",
```
