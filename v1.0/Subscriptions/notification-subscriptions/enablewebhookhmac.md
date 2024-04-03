---
title: "Enable HMAC webhook digest"
slug: "enablewebhookhmac"
excerpt: "<h4>2 credits per API call.</h4><br/><p>Enable HMAC hash ID on the fired webhooks from Tatum API.\nIn order to make sure that a webhook is sent by us, we have the possibility to sign it with the HMAC Sha512 Hex algorithm.<br/>\nTo verify that a webhook is sent by us\n<ol>\n<li>Get a webhook <b>x-payload-hash</b> header value and payload as it is as a JSON file.</li>\n<li>Convert the HTTP webhook body to stringify JSON without any spaces. In JavaScript, you would do it like this <pre>JSON.stringify(req.body)</pre></li>\n<li>Perform calculations on your side to create a digest using Secret Key, webhook payload in bytes and HMAC SHA512 algorithm. JavaScript example:\n<pre>require('crypto').createHmac('sha512', hmacSecret).update(JSON.stringify(req.body)).digest('base64')</pre>.</li>\n<li>Compare x-payload-hash header value with calculated digest as a Base64 string.</li></p>"
hidden: false
createdAt: "Mon Feb 05 2024 11:34:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 11:34:19 GMT+0000 (Coordinated Universal Time)"
---
