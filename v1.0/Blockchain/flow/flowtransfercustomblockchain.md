---
title: "Send arbitrary transaction to blockchain"
slug: "flowtransfercustomblockchain"
excerpt: "<h4>100 credits per API call.</h4><br/>\n<p>Send arbitrary blockchain transaction to FLOW blockchain. Tatum covers the fee connected to the transaction costs in subscription credits. This operation can be done on mainnet only for paid plans.<br/>\nThere are two possibilites how the transaction on the blockchain can be created:\n<ul>\n<li>Using mnemonic and index - private key is generated based on the index in the mnemonic.</li>\n<li>Using secret - private keys is entered manually.</li>\n</ul><br/><br/>\nThis operation needs the private key of the blockchain address. Every time the funds are transferred, the transaction must be signed with the corresponding private key.\nNo one should ever send it's own private keys to the internet because there is a strong possibility of stealing keys and losing funds. In this method, it is possible to enter privateKey\nor signatureId. PrivateKey should be used only for quick development on testnet versions of blockchain when there is no risk of losing funds. In production,\n<a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Tatum KMS</a> should be used for the highest security standards, and signatureId should be present in the request.\nAlternatively, using the Tatum client library for supported languages.\n</p>"
category: 65a8e44fccf94800381cd6f7
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:58 GMT+0000 (Coordinated Universal Time)"
---
