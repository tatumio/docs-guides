---
title: "Get all existing monitoring subscriptions"
slug: "get-all-existing-monitoring-subscriptions"
excerpt: ""
hidden: false
createdAt: "Thu Mar 07 2024 13:25:45 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 13:39:54 GMT+0000 (Coordinated Universal Time)"
---
Getting all existing monitoring subscriptions means retrieving a list of all the active webhook subscriptions that have been created through Tatum. Each subscription in the list represents a blockchain address being monitored for events, such as balance updates or contract interactions, along with the associated webhook listener URL to which the notifications are sent.

When you request to get all existing monitoring subscriptions, Tatum returns a collection of subscription objects. Each object typically includes information such as the subscription identifier, the monitored blockchain address, the webhook listener URL, and any additional configuration or filters applied to the subscription.

This functionality is useful for managing and reviewing your current webhook subscriptions, allowing you to keep track of which addresses are being monitored and the corresponding webhook listener URLs. By examining the list of existing subscriptions, you can ensure that you have the desired monitoring configurations in place and make any necessary adjustments or updates to your webhook subscriptions.

# How to get all existing/active notifications

When you request to get all active notifications using the `tatum.notification.`getAll`()` operation, Tatum returns a collection of active notifications that you have for monitoring the specified blockchain address(es) and detecting events such as balance updates or contract interactions.

```curl
curl -i -X GET \
  'https://api.tatum.io/v4/subscription?pageSize=10&type=mainnet'
```
```javascript
// yarn add @tatumio/tatum
import {TatumSDK, Network, Ethereum, NotificationSubscription, ResponseDto} from '@tatumio/tatum'

const tatum = await TatumSDK.init<Ethereum>({network: Network.ETHEREUM})

const {status, data}: ResponseDto<NotificationSubscription[]> = await tatum.notification.getAll()
```

> 📘 Hint
> 
> Playing with curl and having a need to define type of net, please, use query parameter `type` with `testnet` or `mainnet` values.
> 
> Example: `https://api.tatum.io/v4/subscription?pageSize=10&type=mainnet`
> 
> If you do not use it explicitly `mainnet` is set by default.

# Method parameters

The method accepts the optional object with the following properties.

```typescript
interface GetAllSubscriptionsQuery {
  /**
   * Number of records to return. The default is 10.
   */
  pageSize?: number
  /**
   * Number of records to skip. The default is 0.
   */
  offset?: number
  /**
   * Address to filter by.
   */
  address?: string
}
```

# Subscription response

The methods response has the following format.

```typescript
interface NotificationSubscription {
  /**
   * ID of a subscription.
   */
  id: string
  /**
   * Blockchain network.
   */
  network: Network
  /**
   * URL of the webhook listener.
   */
  url: string
  /**
   * Type of notification subscription.
   */
  type: NotificationType
  /**
   * Address to monitor, valid for some of the types only.
   */
  address?: string
}
```
