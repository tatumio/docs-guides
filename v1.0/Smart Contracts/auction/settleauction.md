---
title: "Settle an NFT auction"
slug: "settleauction"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Settle an auction once it has ended and there is a buyer of the asset at this auction. Settling the auction means that the asset is transferred to the buyer, the amount is transferred to the seller, and the fee is transferred to the fee recipient of the auction.<br/>Both seller and buyer can settle the auction.</p>\n<p>This API is supported for the following blockchains:</p>\n<ul>\n<li>BNB Smart Chain</li>\n<li>Celo</li>\n<li>Ethereum</li>\n<li>Harmony</li>\n<li>Klaytn</li>\n<li>Polygon</li>\n</ul>\n<p><b>The \"execution reverted\" message</b><br/>\nWhen making this API call, you may get the following message:<br/>\n<code>Although one or more Error Occurred [execution reverted] Contract Execution Completed</code><br/>\nThis message is a result of the auction version check and has no impact on completing the API call. You can safely ignore it.</p>\n<p><b>Signing a transaction</b><br/>\nWhen settling the NFT auction, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:36:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:36:24 GMT+0000 (Coordinated Universal Time)"
---