---
title: "TRON - Estimate Fee and FeeLimit for TRX, TRC10 and TRC20"
slug: "estimate-fee-and-feelimit-for-trx-trc10-and-trc20"
excerpt: ""
hidden: false
createdAt: "Tue Feb 06 2024 17:17:01 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Feb 09 2024 08:52:50 GMT+0000 (Coordinated Universal Time)"
---
Transaction fees on the TRON network are calculated based on energy, bandwidth, and transaction type.

## How Tron fees are calculated

- **Normal TRX transactions** cost bandwidth points. Users can access the free daily bandwidth points (5000) or freeze their TRX to gain more. When bandwidth points aren’t enough, TRX will be given directly from the sending account. Required TRX is the number of bytes \* 10 SUN. (1 TRX = 1,000,000 SUN).
- **Smart contracts** cost energy but need bandwidth points to broadcast and confirm the transaction. The bandwidth cost is the same as above.
- **Query transactions** are free since they don’t cost energy or bandwidth.

## Sending TRC-10, TRC-20 (like Tether USDT), and "FAILED - Out of Energy"

Sending Tokens over the TRON network has a higher price in energy.

### Good to know

- Tron's latest [governance proposal](https://github.com/tronprotocol/tips/blob/master/tip-491.md) increased the price of energy.
- Make sure you have at least **50 TRX** on your available balance to pay for network fees.

> 📘 The FeeLimit for TRC10 and TRC20 tokens over Tron is a [complex parameter to calculate](https://github.com/tronprotocol/java-tron/issues/2982).

You can get an approximate idea about the `FeeLimit` via the following RPC query example:

```json cURL
curl --location 'https://api.tatum.io/v3/blockchain/node/tron-mainnet/wallet/getchainparameters' \
--header 'x-api-key:{Mainnet_API_KEY}'
//response:
{
    "chainParameter": [
        {
            "key": "getMaintenanceTimeInterval",
            "value": 21600000
        },
        {
            "key": "getAccountUpgradeCost",
            "value": 9999000000
        },
        {
            "key": "getCreateAccountFee",
            "value": 100000
        },
        {
            "key": "getTransactionFee", // The value we are looking for
            "value": 1000
        },
...
```
