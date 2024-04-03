---
title: "XRP - Account not found"
slug: "xrp-account-not-found"
excerpt: ""
hidden: false
createdAt: "Sun Feb 11 2024 22:20:12 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 22:22:53 GMT+0000 (Coordinated Universal Time)"
---
With XRP, every address is required to hold a small amount of XRP as a **Reserve** to be active and usable for transactions on the network.

If you make a query to an XRP address that does not hold funds, you will likely get an error looking as follows or similar:

```json JSON
{'statusCode': 403, 'errorCode': 'xrp.account.failed', 'message': 'Account not found. Code: 19'}
```

## Current reserve requirements on Mainnet

- Base reserve: 10 XRP
- Owner reserve: 2 XRP per item

> 📘 Reserve amounts are subject to change. Additional information is available at [the following link](https://xrpl.org/reserves.html).
