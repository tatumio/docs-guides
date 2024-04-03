---
title: "Submodules"
slug: "submodules"
excerpt: "A quick overview of th different submodules in Tatum SDK and how they simplify blockchain development. These submodules include RPC, Notification, NFT, Address, and Wallet Provider."
hidden: false
createdAt: "Thu Feb 22 2024 13:02:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 22 2024 13:40:45 GMT+0000 (Coordinated Universal Time)"
---
TatumSDK is thoughtfully designed and organized into two primary submodules to provide a clean and efficient way of interacting with the various blockchains:

**RPC submodule - `tatum.rpc.*`: **This submodule enables you to make direct Remote Procedure Call (RPC) calls to multiple blockchains, providing seamless access to various on-chain data and functionalities. With the RPC submodule, you can fetch account balances, send transactions, interact with smart contracts, and more.

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const latestBlock = await tatum.rpc.blockNumber()
```

**Notification submodule - `tatum.notification.*`: **This submodule allows you to subscribe to real-time notifications for a wide range of events related to specified blockchain addresses. By leveraging the notification submodule, you can effortlessly track incoming and outgoing transactions, NFT transfers, and other events without constantly polling the blockchain.

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const subscription = await tatum.notification.subscribe.nativeIncomingTx({
    "address": "0xcb31c8B2Ce9D229b1968Ceb2516B2EB650151227",
    "url": "https://dashboard.tatum.io/webhook-handler" // REPLACE WITH YOUR URL HANDLER
})
```

**NFT submodule - `tatum.nft.*`:** This submodule offers a comprehensive suite of tools for working with Non-Fungible Tokens (NFTs). With the NFT submodule, you can query the balance of NFTs on an address, retrieve NFT transactions associated with a specific address, explore NFTs within a collection, or identify the owners of a particular NFT.

```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

// Get balance of all NFTs this wallet holds
const balance = await tatum.nft.getBalance({
    "addresses": ["0xcb31c8B2Ce9D229b1968Ceb2516B2EB650151227"]
})
```

**Wallet address submodule - `tatum.address.*`: **This submodule simplifies wallet management across multiple blockchains by allowing you to fetch wallet balances and retrieve transactions for a given address. With the Address submodule, you can easily manage your wallets and monitor transactions, making your blockchain application development more efficient and user-friendly.

By dividing the library into these submodules, TatumSDK offers an organized, easy-to-use interface that makes interacting with Ethereum and other blockchains a breeze. Both beginners and advanced developers can benefit from the streamlined architecture, enabling them to focus on building powerful blockchain applications.
