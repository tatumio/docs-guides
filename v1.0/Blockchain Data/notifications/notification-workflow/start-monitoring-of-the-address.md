---
title: "Start monitoring of the address"
slug: "start-monitoring-of-the-address"
excerpt: ""
hidden: false
createdAt: "Thu Mar 07 2024 12:52:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 13:39:15 GMT+0000 (Coordinated Universal Time)"
---
Starting to monitor an address means that the Tatum system begins observing the specified blockchain address for any changes, particularly balance updates. When monitoring an address, Tatum listens for incoming transactions, outgoing transactions, and internal contract interactions that may affect the balance of the address.

> 📘 Hint
> 
> In the context of Ethereum or any other EVM blockchain, monitoring an address involves tracking the Ethereum blockchain for transactions that involve the given address either as a sender or a receiver. The system also checks for interactions with smart contracts that may change the address's balance, such as token transfers or contract executions.

When an event related to the address is detected, Tatum triggers the webhook, sending a notification to the user's specified webhook listener URL. This allows users to receive real-time updates about events occurring on the monitored address, enabling them to react promptly to any changes in their address's balance.

# How to start with address monitoring

Use the Tatum API or Tatum SDK (@tatumio/tatum) to create a subscription for address events.

```curl curl
curl -i -X POST \
  https://api.tatum.io/v4/subscription?type=mainnet \
  -H 'Content-Type: application/json' \
  -d '{
    "type": "ADDRESS_EVENT",
    "attr": {
      "address": "0xF64E82131BE01618487Da5142fc9d289cbb60E9d",
      "chain": "ETH",
      "url": "https://<YOUR_WEBHOOK_URL>"
    }
  }'
```
```javascript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, ResponseDto, AddressBasedNotification} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const subscription: ResponseDto<AddressBasedNotification> = await tatum.notification.subscribe.addressEvent({
  address: '0xF64E82131BE01618487Da5142fc9d289cbb60E9d', // replace with your address
  url: 'https://<YOUR_WEBHOOK_URL>' // replate with your URL handler
})
```

This function returns an object with a `id` property - a string identifier of the created subscription. Store this identifier in order to stop the monitoring of this address in the future.

> 📘 Hint
> 
> Playing with curl and having a need to define type of net, please, use query parameter `type` with `testnet` or `mainnet` values.
> 
> Example: `https://api.tatum.io/v4/subscription?type=mainnet`
> 
> If you do not use it explicitly `mainnet` is set by default.
> 
> You can also use [Get all existing monitoring subscriptions](get-all-existing-monitoring-subscriptions.md) operation to get the correct `id`.

```typescript
interface ResponseDto<T> {
  /**
   * Actual payload of the response
   */
  data: T
  /**
   * Status of the response
   */
  status: Status
  /**
   * In case of ERROR status, this field contains the error message and detailed description
   */
  error?: ErrorWithMessage
}

interface AddressBasedNotification {
  /**
   * ID of a subscription.
   */
  id: string
  /**
   * Monitored address.
   */
  address: string
  /**
   * URL of a webhook listener.
   */
  url: string
}
```

# Troubleshooting

## The address is already subscribed for a blockchain

If the same address is already subscribed to a notification type, the method call will fail with the following message:

`Subscription for type ADDRESS_EVENT on the address id 0xbaf6dc2e647aeb6f510f9e318856a1bcd66c5e19 and currency ETH already exists.`

> #### 🚧 Only 1 unique address per notification type on a blockchain can be subscribed at the same time for the same user

## Invalid format of the address

If the submitted address is in an invalid format it will respond with the following error message:

`address must be a valid ETH address. Address must start with 0x and must contain 40 hexadecimal characters after and have the correct checksum.`

> #### 🚧 Submitted address should be in valid format.
