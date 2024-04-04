---
title: "Assign a blockchain address to a virtual account"
slug: "assignaddress"
excerpt: "<p><b>2 credits per API call</b></p>\n<p>Assign an existing blockchain address to a virtual account. The blockchain address becomes a deposit address associated with this account.</br>Use this API when the <a href=\"https://apidoc.tatum.io/tag/Account#operation/createAccount\" target=\"_blank\">virtual account has no default extended public key</a> (<code>xpub</code>) and deposit addresses are handled manually.</p>\n<p>You can assign multiple blockchain addresses to one virtual account. When you have multiple blockchain addresses assigned to the same virtual account, you aggregate various blockchain transactions from different addresses under a single account.<br/>You can deposit funds from another blockchain address to a deposit address associated with the virtual account, and the funds will be credited to that virtual account.</p>\n<p><b>Scanning for incoming deposits</b><br/>\nBy default, deposit addresses are scanned for incoming deposits. Deposit addresses are automatically synchronized with the associated virtual account, and you can see incoming deposits on the virtual account.<br/>Scanning deposit addresses for incoming deposits consumes <b>20 credits per address per day</b>.</p>\n<p>If you want to be notified about certain events occurring on the deposit addresses, <a href=\"https://apidoc.tatum.io/tag/Notification-subscriptions#operation/createSubscription\" target=\"_blank\">subscribe for notifications</a>.</p>"
category: 65c0c89f01bfc0001709afa1
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
---
