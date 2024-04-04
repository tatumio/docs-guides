---
title: "Send payment in batch"
slug: "sendtransactionbatch"
excerpt: "<h4>2 + 2 * N per API call. (N - count of transactions)</h4><br/>\n<p>Sends the N payments within Tatum Private Ledger. All assets are settled instantly.<br/>\nWhen a transaction is settled, 2 transaction records are created, 1 for each of the participants. These 2 records are connected via a transaction reference, which is the same for both of them.<br/>\nThis method is only used for transferring assets between accounts within Tatum and will not send any funds to blockchain addresses.<br/>\nIf there is an insufficient balance in the sender account, no transaction is recorded.<br/>\nIt is possible to perform an anonymous transaction where the sender account is not visible for the recipient.<br/>\nThe FIAT currency value of every transaction is calculated automatically. The FIAT value is based on the accountingCurrency of the account connected to the transaction and is available in the marketValue parameter of the transaction.</p>"
category: 65c0c89f01bfc0001709afa1
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
---
