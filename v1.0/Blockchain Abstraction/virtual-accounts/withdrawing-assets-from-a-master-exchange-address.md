---
title: "Withdrawing Assets from a Master Exchange Address"
slug: "withdrawing-assets-from-a-master-exchange-address"
excerpt: ""
category: 65a8e44fccf94800381cd6f8
hidden: false
createdAt: "Thu Feb 08 2024 14:08:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 26 2024 07:42:17 GMT+0000 (Coordinated Universal Time)"
---
There are two withdrawal methods from a Virtual Account:

- From each Virtual Account deposit address
- From a Master Exchange Address

## How to withdraw assets from a Master Exchange Address

1. **Store information about withdrawal**
   1. Check the id of the Virtual Account, the available balance or the UTXO balance
   2. Decrease the **amount** and **fees** from the Virtual Account
   3. Prepare transaction to broadcast transfer to the blockchain
2. **Blockchain transfer**
   1. Standard blockchain transfer from address to address
   2. Verify the result of the transfer
3. **Complete/Rollback**
   1. IF blockchain transfer fails - rollback VA balance
   2. ELSE complete withdrawal

### Example:

1. `User_A: VirtualAccount_A` balance is 0 MATIC.
2. `User_A: DepositAddress_A` connected to `VirtualAccount_A` receives 3 MATIC.
   1. `VirtualAccount_A` balance is now 3 MATIC.
3. `Exchange_Owner`: Transfers 3 MATIC from `DepositAddress_A` to `MasterExchangeAddress`.
   1. This is a standard blockchain transfer via: [Send MATIC from account to account](https://apidoc.tatum.io/tag/Polygon/#operation/PolygonBlockchainTransfer)
   2. `VirtualAccount_A` balance remains 3 MATIC.
4. `User_A`: Withdraws and transfers 3 MATIC from VirtualAccount_A to VirtualAccount_B owned by User_B.
   1. Endpoint: [Send payment](https://apidoc.tatum.io/tag/Transaction/#operation/sendTransaction)
   2. `VirtualAccount_A` balance is now 0 MATIC.
   3. `VirtualAccount_B` balance is now 3 MATIC.
5. `User_B`: Withdraws to transfer out 3 MATIC from `VirtualAccount_B`  to an unrelated blockchain address.
   1. `Exchange_Owner`: [Store withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/storeWithdrawal) --> `/v3/offchain/withdrawal`
   2. `Exchange_Owner`: Standard blockchain transfer via: [Send MATIC from account to account](https://apidoc.tatum.io/tag/Polygon/#operation/PolygonBlockchainTransfer)
   3. `Exchange_Owner`: Completes or Cancels the withdrawal
      1. [Complete withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/completeWithdrawal) --> `/v3/offchain/withdrawal/{id}/{txId}`
      2. [Cancel withdrawal](https://apidoc.tatum.io/tag/Withdrawal/#operation/cancelInProgressWithdrawal) --> `/v3/offchain/withdrawal/{id}`
