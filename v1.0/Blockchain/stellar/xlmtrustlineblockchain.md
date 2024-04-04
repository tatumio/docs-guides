---
title: "Create / Update / Delete XLM trust line"
slug: "xlmtrustlineblockchain"
excerpt: "<h4>10 credits per API call.</h4><br/><p>\n<p>Create / Update / Delete XLM trust line between accounts to transfer private assets.\nBy creating trustline for the first time, the asset is created automatically and can be used in the transactions.<br/><br/>\nThis operation needs the private key of the blockchain address. Every time the funds are transferred, the transaction must be signed with the corresponding private key.\nNo one should ever send it's own private keys to the internet because there is a strong possibility of stealing keys and loss of funds. In this method, it is possible to enter privateKey\nor signatureId. PrivateKey should be used only for quick development on testnet versions of blockchain when there is no risk of losing funds. In production,\n<a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Tatum KMS</a> should be used for the highest security standards, and signatureId should be present in the request.\nAlternatively, using the Tatum client library for supported languages.\n</p>"
category: 65c0c8c6ba99f1006df40d7a
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
---
