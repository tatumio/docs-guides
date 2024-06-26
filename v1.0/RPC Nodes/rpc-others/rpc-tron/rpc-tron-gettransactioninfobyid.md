---
title: "gettransactioninfobyid"
slug: "rpc-tron-gettransactioninfobyid"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:46 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const transactionInfo = await tatum.rpc.getTransactionInfoById('7c2d4206c03a883dd9066d920335dc1be272a8dc733cfa3f6d10308faa37facc')

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getTransactionInfoById` method allows you to query the transaction fee, block height, and other related information by a transaction id. This can be particularly useful when you need to track the status of specific transactions or analyse the transactions for auditing purposes.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/XWyQOGE",
  "href": "https://codepen.io/tatum-devrel/pen/XWyQOGE",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

- `value`: The transaction hash, or transaction ID, you want to get information about. It should be a string.

### Return Object

- `id`: The transaction ID (string)
- `fee`: The total number of TRX burned in this transaction, represented as an integer.
- `blockNumber`: The block number (integer)
- `blockTimeStamp`: The block timestamp, in milliseconds (integer)
- `contractResult`: Transaction execution results (string array)
- `contract_address`: Contract address (string)
- `receipt`: Transaction receipt, including transaction execution result and transaction fee details. It contains the following fields:
  - `energy_usage`: The amount of energy consumed in the caller's account
  - `energy_fee`: The amount of TRX burned to pay for energy
  - `origin_energy_usage`: The amount of energy consumed in the contract deployer's account
  - `energy_usage_total`: The total amount of energy consumed by the transaction
  - `net_usage`: The amount of bandwidth consumed
  - `net_fee`: The amount of TRX burned to pay for the bandwidth
  - `result`: Transaction execution result
  - `energy_penalty_total`: The amount of extra energy that needs to be paid for calling a few popular contracts
- `log`: The log of events triggered during the smart contract call.
- `result`: Execution results. If the execution is successful, the field will not be displayed in the returned value, if the execution fails, the field will be "FAILED"
- `resMessage`: When the transaction execution fails, the details of the failure will be returned through this field. Hex format, you can convert it to a string to get plaintext information.
- `withdraw_amount`: For the withdrawal reward transaction, unfreeze transaction, they will withdraw the vote reward to account. The number of rewards withdrawn to the account is returned through this field, and the unit is sun.
- `unfreeze_amount`: In the Stake1.0 stage, for unstaking transactions, this field returns the amount of unstaked TRX, the unit is sun.
- `internal_transactions`: Internal transaction
- `withdraw_expire_amount`: In the Stake2.0 stage, for unstaking transactions and withdrawing unfrozen balance transactions, this field returns the amount of unfrozen TRX withdrawn to the account in this transaction, the unit is sun.

### HTTP Request Example

```json
{
 "value": "0x94eea63bb6774c1565a5a5adc37cc8b73bb5292c63f7829231e195314d338b98",
}
```

### HTTP Response Example

```json
{
  "id": "7c2d4206c03a883dd9066d620335dc1be272a8dc733cfa3f6d10308faa37facc",
  "fee": 1100000,
  "blockNumber": 32880248,
  "blockTimeStamp": 1681368027000,
  "contractResult": [
    ""
  ],
  "receipt": {
    "net_fee": 100000
  }
}
```
