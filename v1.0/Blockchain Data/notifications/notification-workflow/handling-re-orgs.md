---
title: "Handling Re Orgs"
slug: "handling-re-orgs"
excerpt: ""
category: 65c0c716d716fe0040919d8b
hidden: false
createdAt: "Thu Mar 07 2024 13:26:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 13:27:28 GMT+0000 (Coordinated Universal Time)"
---
# Identifying the Re Org Notifications

Because of Tatum's fast notification implementation we are closely following tip of the chain. In rare occasions there can be a blockchain reorg happening over blocks that we've already processed. In such cases there is a secondary mechanism in place following the first in a certain distance (X blocks depending on chain), that will handle any transactions that might have been recently updated - those transactions will have respective notifications sent as normal with additional reorg flag.

# Example: Updated Notification delivered after Re Org

```json
{
  "address": "0xfAF0F447715dEeDF6Dd79c2fd1F7966F0CC647A1",
  "amount": "0.001",
  "asset": "ETH",
  "blockNumber": 3553692,
  "counterAddress": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
  "txId": "0xde48b2572176eb3e1c4a2a9abe62c5552f778afcbba1ded8491a2ceb675a6390",
  "type": "native",
  "chain": "ethereum-mainnet",
  "subscriptionType": "ADDRESS_EVENT",
  "reorg": true,
}
```

Please note that such notifications might arrive with a certain delay which could be upto couple of minutes depending on the chain.
