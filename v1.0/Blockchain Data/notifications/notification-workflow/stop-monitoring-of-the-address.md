---
title: "Stop monitoring of the address"
slug: "stop-monitoring-of-the-address"
excerpt: ""
category: 65e9ba6715ec3b004bc82075
hidden: false
createdAt: "Thu Mar 07 2024 13:19:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 13:39:23 GMT+0000 (Coordinated Universal Time)"
---
Stopping the monitoring of an address means that the Tatum system will no longer push notifications via webhooks for any changes related to that address. Note that this only stops the Notification for a particular address which you are willing to stop monitoring for, incase 

> 📘 Hint
> 
> In the context of Ethereum or any other EVM chains, stopping the monitoring of an address means that Tatum will no longer track the Ethereum blockchain for transactions involving the given address, either as a sender or a receiver. The system will also discontinue checking for interactions with smart contracts that may change the address's balance, such as token transfers or contract executions.

# How to stop monitoring of the address

To stop monitoring an address, you can unsubscribe from the webhook notification by calling `tatum.notification.unsubscribe(id)` using the subscription identifier. Once unsubscribed, the Tatum system will no longer send notifications to the specified webhook listener URL about events occurring on the monitored address.

```curl curl
curl -i -X DELETE \
  https://api.tatum.io/v4/subscription/YOUR_SUBSCRIPTION_ID \
  -H 'Content-Type: application/json'
```
```javascript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

await tatum.notification.unsubscribe('YOUR_SUBSCRIPTION_ID')
```

> 📘 Hint
> 
> Playing with curl and having a need to define type of net, please, use query parameter type with `testnet` or `mainnet` values.
> 
> Example:`<https://api.tatum.io/v4/subscription/{id}?type=mainnet>`
> 
> If you do not use it explicitly `mainnet` is set by default.

# Troubleshooting

## Invalid subscription id

If the subscription id is invalid, the following message is returned:

`id should be valid id and 24 characters long, e.g. 6398ded68bfa23a9709b1b17`
