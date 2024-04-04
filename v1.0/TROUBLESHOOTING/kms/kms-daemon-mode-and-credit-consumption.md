---
title: "KMS - Daemon mode and credit consumption"
slug: "kms-daemon-mode-and-credit-consumption"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Sun Feb 25 2024 12:49:07 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 25 2024 12:49:12 GMT+0000 (Coordinated Universal Time)"
---
KMS in Daemon mode periodically checks for pending transactions every 5 seconds by default, costing 4 credits per minute. This means 4 (credits) \_60 (minutes) \_24 (hours) == 5760 credits/day.

On top of that, there's a cost to sign transactions at a rate of x1 credit for every 500 txID signature attempts.

To lower the baseline credit consumption, you may increase the periodicity checks.

### Example:

```shell CLI
tatum-kms daemon --period=15
```

> 📘 Additional information is available at [the following link](https://github.com/tatumio/tatum-kms#daemon-mode).
