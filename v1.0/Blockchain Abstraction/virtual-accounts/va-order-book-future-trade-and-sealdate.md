---
title: "Order Book: Future Trade and sealDate"
slug: "va-order-book-future-trade-and-sealdate"
excerpt: ""
category: 65e9ba6715ec3b004bc82075
hidden: false
createdAt: "Sun Feb 11 2024 22:42:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 07:42:23 GMT+0000 (Coordinated Universal Time)"
---
When creating a Future Trade via Order Book, `sealDate` acts as the timestamp on which the buyer and seller finalize the transaction and enter into the contractual obligation to buy or sell the underlying asset at a specified amount and price in the future.

With Future Trading, once the `sealDate` is up, the Order Book matchmaker will be allowed to execute the trading request.
