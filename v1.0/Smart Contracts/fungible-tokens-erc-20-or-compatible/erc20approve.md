---
title: "Allow a blockchain address to transfer and burn fungible tokens"
slug: "erc20approve"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Allow a blockchain address (the <code>spender</code> parameter in the request body) to transfer and burn fungible tokens on behalf of the smart contract owner.</p>\n<p>This API is supported for the following blockchains:</p>\n<ul>\n<li>BNB Smart Chain</li>\n<li>Celo</li>\n<li>Ethereum</li>\n<li>Harmony</li>\n<li>Klaytn</li>\n<li>Polygon</li>\n</ul>\n<p><b>Signing a transaction</b><br/>\nWhen allowing a blockchain address to transfer and burn fungible tokens, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
category: 65c0c834f1cd450023eab1ed
hidden: false
createdAt: "Mon Feb 05 2024 11:36:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:36:29 GMT+0000 (Coordinated Universal Time)"
---
