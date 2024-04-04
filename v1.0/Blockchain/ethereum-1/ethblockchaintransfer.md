---
title: "Send ETH or fungible tokens (ERC-20) from account to account"
slug: "ethblockchaintransfer"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Send ETH or Tatum-supported fungible tokens (ERC-20) from account to account.</p>\n<p style=\"border:4px solid DeepSkyBlue;\"><b>NOTE:</b> Sending the fungible tokens is supported only on the mainnet.</p>\n<p><b>Signing a transaction</b><br/>\nWhen sending ETH, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
category: 65a8e44fccf94800381cd6f7
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
---
