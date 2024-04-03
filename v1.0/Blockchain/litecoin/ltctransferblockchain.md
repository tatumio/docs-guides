---
title: "Send LTC to Litecoin addresses"
slug: "ltctransferblockchain"
excerpt: "<p><b>10 credits per API call</b></p>\n<p>Send LTC to blockchain addresses.</p>\n<p>Litecoin transactions are based on UTXOs. \"UTXO\" stands for \"Unspent Transaction Output\". A UTXO is the amount of LTC that remains at a Litecoin address after a cryptocurrency transaction involving this address has been performed. The UTXO can then be used as input for a new cryptocurrency transaction. For more information about the UTXO, see the <a href=\"https://developer.bitcoin.org/devguide/transactions.html\" target=\"_blank\">Bitcoin user documentation</a>. To check UTXOs in a transaction, see the <a href=\"#operation/LtcGetUTXO\">API for getting information about a transaction output (UTXO) in a Litecoin transaction</a>.</p>\n<p>You can build a LTC transaction by one of the following methods:</p>\n<ul>\n<li><b>Sending LTC from blockchain addresses</b><br/>The assets are sent from a list of addresses. For each address, the last 100 transactions are scanned for any UTXO to be included in the transaction. For easier control over the assets to be sent, we recommend that you use this method only if you have one address to send the assets from.<br/> To use this method, use the <code>LtcTransactionAddress</code> or <code>LtcTransactionAddressKMS</code> schema of the request body.</li>\n<li><b>Sending LTC from UTXOs</b><br/>The assets are sent from a list of UTXOs. Each UTXO is included in the transaction. Use this method if you want to manually calculate the amount to send.<br/> To use this method, use the <code>LtcTransactionFromUTXO</code> or <code>LtcTransactionFromUTXOKMS</code> schema of the request body.</li>\n</ul>\n<p>When an UTXO is entered into a transaction, the whole UTXO amount is included and must be spent. For example, address A receives two transactions, T1 with 1 LTC and T2 with 2 LTC. A transaction that consumes the UTXOs from both T1 and T2 will have an available amount of 3 LTC to spend:<br/><code>1 LTC (from T1) + 2 LTC (from T2) = 3 LTC (to spend in total)</code></p>\n<p>You can send the assets to one or multiple recipients in one transaction. If you send the assets to multiple addresses, each address must have its own amount to receive.</p>\n<p><b>Paying the gas fee and receiving the change</b><br/>\nWhen the amount that the recipients should receive is lower than the amount from the UTXOs, the difference between these two amounts is by default used as the gas fee for the transaction. Because this amount may be considerable and you may not want to spend it all on the gas fee, you can explicitly specify the fee amount and the blockchain address where any extra funds remaining after covering the fee will be sent (the <code>fee</code> and <code>changeAddress</code> parameters in the request body, correspondingly).</p>\n<p><b>Signing a transaction</b><br/>\nWhen sending LTC, you are charged a fee for the transaction, and you must sign the transaction with the private key of the blockchain address from which the fee will be deducted.</p>\n<p>Providing the private key in the API is not a secure way of signing transactions, because the private key can be stolen or exposed. Your private keys should never leave your security perimeter. You should use the private keys only for testing a solution you are building on the <b>testnet</b> of a blockchain.</p>\n<p>For signing transactions on the <b>mainnet</b>, we strongly recommend that you use the Tatum <a href=\"https://github.com/tatumio/tatum-kms\" target=\"_blank\">Key Management System (KMS)</a> and provide the signature ID instead of the private key in the API. Alternatively, you can use the <a href=\"https://github.com/tatumio/tatum-js/tree/v2\" target=\"_blank\">Tatum JavaScript client</a>.</p>\n<br />Examples of using this endpoint with the Tatum JS SDK can be found in <a href=\"https://github.com/tatumio/tatum-js/tree/v2/examples/ltc-example/src/app/ltc.blockchain.example.ts\" target=\"_blank\">Tatum LTC SDK</a>."
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
---