---
title: "Get TRC-20 transactions for a TRON account"
slug: "tronaccounttx20"
excerpt: "<p><b>5 credits per API call</b></p>\n<p>Get TRC-20 transactions for a TRON account.</p>\n<p>This API returns up to 200 transactions in one API call. If there are more than 200 transactions for the TRON account, the response body will contain the <code>next</code> parameter with the fingerprint of the transaction that follows the last (200<sup>th</sup>) transaction in the returned list.</p>\n<p>To get the next 200 transactions, make another call using this API, but this time add the <code>next</code> parameter the endpoint URL and set it to the transaction fingerprint from the <code>next</code> parameter in the response, for example:</p>\n<p><code>https://api.tatum.io/v3/tron/transaction/account/{address}/trc20?next=81d0524acf5967f3b361e03fd7d141ab511791cd7aad7ae406c4c8d408290991</code></p>"
category: 65a8e44fccf94800381cd6f7
hidden: false
createdAt: "Mon Feb 05 2024 11:38:51 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:39:08 GMT+0000 (Coordinated Universal Time)"
---
