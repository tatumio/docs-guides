---
title: "Get information about a transaction output (UTXO) in a Litecoin transaction"
slug: "ltcgetutxo"
excerpt: "<p><b>5 credits per API call</b></p>\n<p>Get information about a transaction output in a transaction and check whether this output is a UTXO or has been spent.</p>\n<p>\"UTXO\" stands for \"Unspent Transaction Output\". A UTXO is the amount of LTC that remains at a Litecoin address after a cryptocurrency transaction involving this address has been performed. The UTXO can then be used as input for a new cryptocurrency transaction. For more information the UTXO, see the <a href=\"https://developer.bitcoin.org/devguide/transactions.html\" target=\"_blank\">Bitcoin user documentation</a>.</p>\n<ul>\n<li>If the transaction output is an UTXO, the API returns data about it.</li>\n<li>If the transaction output has been spent and there is no UTXO to return, the API returns an error with the <code>404</code> response code.</li>\n</ul>\n<br />Examples of using this endpoint with the Tatum JS SDK can be found in <a href=\"https://github.com/tatumio/tatum-js/tree/v2/examples/ltc-example/src/app/ltc.blockchain.example.ts\" target=\"_blank\">Tatum LTC SDK</a>."
category: 65c0c8c6ba99f1006df40d7a
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
---
