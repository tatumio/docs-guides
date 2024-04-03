---
title: "💶 Gas Pump"
slug: "gas-pump-1"
excerpt: ""
hidden: false
createdAt: "Thu Mar 07 2024 13:34:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 12:36:45 GMT+0000 (Coordinated Universal Time)"
---
As the owner of a custodial application (for example, a crypto exchange), every time you want to send assets from one of your user’s address, you have to calculate the gas fees, then send that amount to their address (a transaction that also incurs gas fees), and finally send the assets from their address. Two transactions incur gas fees and can result in minuscule differences of crypto "dust" remaining on user addresses. If you have thousands or millions of addresses, this method creates an enormous amount of work and fees for you as a custodial provider.

Gas Pump helps you manage gas fees in your custodial application in a more efficient way: gas fees for any transaction made by your customers are automatically deducted from a dedicated address (referred to as "master address") instead of the customer's address. This eliminates the need to send crypto to each customer's address to pay for gas fees.

**Gas Pump supports the following blockchains:**

| Network         |
| :-------------- |
| BNB Smart Chain |
| Celo            |
| Ethereum        |
| Harmony         |
| Klaytn          |
| Polygon         |
| TRON            |

- [API Reference](/reference/precalculategaspumpaddresses)
