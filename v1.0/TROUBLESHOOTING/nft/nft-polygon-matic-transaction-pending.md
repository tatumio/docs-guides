---
title: "NFT - Transaction Pending"
slug: "nft-polygon-matic-transaction-pending"
excerpt: ""
hidden: false
createdAt: "Fri Jan 26 2024 08:50:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Jan 26 2024 13:13:22 GMT+0000 (Coordinated Universal Time)"
---
After minting an NFT via the v3 REST API you may get a successful response body with a transaction hash.

However, when checking the transaction details on the blockchain you may get:

```Text JSON
Pending - "This txn hash was found in our secondary node and should be picked up by our indexer in a short while."  
HTML
```

And minutes later:

```Text JSON
"Sorry, We are unable to locate this TxnHash"
```

**Good to know**

This happens when the transaction didn’t make it through, most likely because you used the wrong nonce or wrong sequence index. 

If you didn’t use a manual gas or nonce, the node dropped your transaction from the Mempool TTL for our nodes.
