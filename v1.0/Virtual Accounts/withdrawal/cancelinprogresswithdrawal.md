---
title: "Cancel withdrawal"
slug: "cancelinprogresswithdrawal"
excerpt: "<h4>1 credit per API call.</h4><br/>\n<p>This method is helpful if you need to cancel the withdrawal if the blockchain transaction fails or is not yet processed.\nThis does not cancel already broadcast blockchain transaction, only Tatum internal withdrawal, and the ledger transaction, that was linked to this withdrawal.<br/>\nBy default, the transaction fee is included in the reverted transaction. There are situations, like sending ERC20 on ETH, TRC token on TRON, XLM or XRP based assets, when the fee should not be reverted, because e.g. the fee is in calculated\nin Ethereum and transaction was in ERC20 currency. In this situation, only the transaction amount should be reverted, not the fee.\n</p>"
category: 65c0c89f01bfc0001709afa1
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:14 GMT+0000 (Coordinated Universal Time)"
---
