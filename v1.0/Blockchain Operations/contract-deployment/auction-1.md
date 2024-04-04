---
title: "🏛️ Auction"
slug: "auction-1"
excerpt: ""
category: 65e9ba02205d9900590782fe
hidden: false
createdAt: "Thu Mar 07 2024 13:32:13 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 12:57:56 GMT+0000 (Coordinated Universal Time)"
---
Peer-to-peer NFT marketplaces like OpenSea allow users to create NFTs with metadata (pictures, videos, songs, 3D art, etc.) and post listings to sell them to one another. OpenSea then takes a percentage of each sale. Users can create fixed-price listings for their NFTs or put them up for auction and sell them to the highest bidder.

Creating NFTs has always been super simple with Tatum. However, peer-to-peer NFT auctions can take a bit of work to implement properly. So we've created out-of-the-box NFT auction functionality that can be deployed in just a few minutes.

When an NFT is sold, the creator is automatically paid, the NFT is instantly transferred to the buyer, and you as the owner of the marketplace automatically receive a percentage of the transaction. Everything happens on the blockchain, so you don’t even need to create a complex, application-level backend to run the listings.

Smart contract enables auction operator to create new auction for NFT (ERC-721/1155). Operator can set a fee in percentage, which will be paid on top of the price of the asset. can be offered for native asset - ETH, BSC, etc. - or any ERC20 token - this is configurable during auction creation. Before auction is created, seller must approve transfer of the NFT to the auction contract. Buyer will bid for the asset from the auction using native asset - send assets along the gid() smart contract call, or via ERC20 token. Buyer of the auction must perform approval for the smart contract to access ERC20 token, before the actual bid() method is called. Once there is higher bid then the actual one, the previous bidder's funds will be returned to him and new bidder will be the current winning one. When auction ends, anyone can settle the auction - NFT will be sent to the bidder, assets to the seller and fee to the operator.  
This operation deploys a smart contract on the blockchain.

This API is supported for the following blockchains:

| Network         |
| :-------------- |
| BNB Smart Chain |
| Celo            |
| Ethereum        |
| Harmony         |
| Klaytn          |
| Polygon         |

[**API Reference**](/reference/generateauction)
