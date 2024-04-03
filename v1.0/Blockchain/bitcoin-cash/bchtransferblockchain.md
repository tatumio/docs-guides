---
title: "Send BCH to Bitcoin Cash addresses"
slug: "bchtransferblockchain"
excerpt: "<p><b>10 credits per API call</b></p>\n<p>Send BCH to blockchain addresses.</p>\n<p>Bitcoin Cash transactions are based on UTXOs. \"UTXO\" stands for \"Unspent Transaction Output\". A UTXO is the amount of BCH that remains at a Bitcoin Cash address after a cryptocurrency transaction involving this address has been performed. The UTXO can then be used as input for a new cryptocurrency transaction. For more information the UTXO, see the <a href=\"https://developer.bitcoin.org/devguide/transactions.html\" target=\"_blank\">Bitcoin user documentation</a>.</p>\n<p>You build a BCH transaction by sending BCH from UTXOs. Each UTXO is included in the transaction.</p>\n<p>When an UTXO is entered into a transaction, the whole UTXO amount is included and must be spent. For example, address A receives two transactions, T1 with 1 BCH and T2 with 2 BCH. A transaction that consumes the UTXOs from both T1 and T2 will have an available amount of 3 BCH to spend:<br/><code>1 BCH (from T1) + 2 BCH (from T2) = 3 BCH (to spend in total)</code></p>\n<p>You can send the assets to one or multiple recipients in one transaction. If you send the assets to multiple addresses, each address must have its own amount to receive.</p>\n<p><b>Paying the gas fee and receiving the change</b><br/>\nWhen the amount that the recipients should receive is lower than the amount from the UTXOs, the difference between these two amounts is by default used as the gas fee for the transaction. Because this amount may be considerable and you may not want to spend it all on the gas fee, you can explicitly specify the fee amount and the blockchain address where any extra funds remaining after covering the fee will be sent (the <code>fee</code> and <code>changeAddress</code> parameters in the request body, correspondingly).</p>\n<p><b>Signing a transaction</b><br/>\nWhen sending BCH, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:55 GMT+0000 (Coordinated Universal Time)"
---