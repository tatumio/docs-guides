---
title: "Quick Start"
slug: "quick-start"
excerpt: "Fastest SDK to get you started"
category: 65d73feeb4be160ab098d70d
hidden: false
createdAt: "Thu Feb 22 2024 13:42:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 22 2024 13:42:20 GMT+0000 (Coordinated Universal Time)"
---
# Install the SDK

```typescript
npm install @tatumio/tatum
```

# Make your first RPC call

```typescript
import { TatumSDK, Ethereum, Network } from '@tatumio/tatum'

// Init chain of your choice
 const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})
 
 // Use our interfaces to make the call
 const latestBlock = await tatum.rpc.blockNumber()
 
 console.log(`Latest block is ${latestBlock}`)

```
