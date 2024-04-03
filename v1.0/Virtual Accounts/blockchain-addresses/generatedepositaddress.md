---
title: "Create a deposit address for a virtual account"
slug: "generatedepositaddress"
excerpt: "<p><b>2 credits per API call<br/>\nOn Flow, additional 3000 credits are consumed for <a href=\"https://apidoc.tatum.io/tag/Flow#operation/FlowGenerateAddress\" target=\"_blank\">each created address</a>.</b></p>\n<p>Create a deposit address associated with a virtual account.</p>\n<p>You can create multiple deposit addresses for one virtual account. When you have multiple deposit addresses created for the same virtual account, you aggregate various blockchain transactions from different addresses under a single account.<br/>You can deposit funds from another blockchain address to a deposit address associated with the virtual account, and the funds will be credited to that virtual account.</p>\n<p><b>Scanning for incoming deposits</b><br/>\nBy default, deposit addresses are scanned for incoming deposits. Deposit addresses are automatically synchronized with the associated virtual account, and you can see incoming deposits on the virtual account.<br/>Scanning deposit addresses for incoming deposits consumes <b>20 credits per address per day</b>.</p>\n<p>If you want to be notified about certain events occurring on the deposit addresses, <a href=\"https://apidoc.tatum.io/tag/Notification-subscriptions#operation/createSubscription\" target=\"_blank\">subscribe for notifications</a>.</p>\n<p><b>Virtual account cryptocurrency</b></p>\n<p>Depending on the cryptocurrency of the virtual account, this API generates:</p>\n<ul>\n<li><b>Public address</b> for BTC, BCH, ETH, or LTC</li>\n<li><b>DestinationTag</b> for XRP</li>\n<li><b>Message</b> for XLM</li>\n</ul>\n<p>For fore information about supported blockchains and address types, see the <a href=\"https://apidoc.tatum.io/tag/Account#operation/createAccount\" target=\"_blank\">API for creating virtual accounts</a>.</p>\n<p>Deposit addresses are generated in the natural order of the extended public key provided in the virtual account. The derivation index is the representation of that order; it starts from 0 and ends at 2^31.</p>\n<p>When a new deposit address is generated, the last not used index is used to generate the address. You can skip some addresses to a different index, which means all the skipped addresses will no longer be used.</p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:38:10 GMT+0000 (Coordinated Universal Time)"
---