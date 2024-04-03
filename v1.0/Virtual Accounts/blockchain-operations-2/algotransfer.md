---
title: "Send ALGO from a virtual account to the blockchain"
slug: "algotransfer"
excerpt: "<p><b>4 credits per API call</b></p>\n<p>Send Algos or ERC-20-equivalent Algorand tokens from a virtual account (even from a virtual account without deposit addresses adssigned) to the Algorand blockchain.</p>\n<p>The recipient has to agree in advance to receive assets because Algorand charges users for storing assets on their addresses, and an Algorand blockchain address by default does not receive assets unless explicitly agreed. Before sending any asset from a virtual account to the blockchain, make sure that the recipient <a href=\"https://apidoc.tatum.io/tag/Algorand#operation/AlgorandBlockchainReceiveAsset\" target=\"_blank\">has agreed to receive the assets</a> to their address.</p>\n<p>Sending Algorand assets creates an internal Tatum withdrawal request with an ID. If everything works as expected, the withdrawal request is marked as complete and a transaction ID is assigned to it.</p>\n<ul>\n<li>If a server connection is unavailable, the withdrawal request is cancelled.</li>\n<li>If the transfer to the blockchain is successful, but the Tatum infrastructure cannot be accesses, the ID of the blockchain transaction is returned and you have to <a href=\"https://apidoc.tatum.io/tag/Withdrawal#operation/completeWithdrawal\" target=\"_blank\">complete the withdrawal request manually</a>. Otherwise, all other withdrawals will be pending.</li>\n</ul>\n<p><b>Signing a transaction</b><br/>\nWhen sending Algos or ERC-20-equivalent Algorand tokens, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:17 GMT+0000 (Coordinated Universal Time)"
---