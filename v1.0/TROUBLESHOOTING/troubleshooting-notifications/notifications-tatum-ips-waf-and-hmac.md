---
title: "Notifications - Tatum IPs, WAF and HMAC"
slug: "notifications-tatum-ips-waf-and-hmac"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 20:42:38 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2024 20:43:29 GMT+0000 (Coordinated Universal Time)"
---
Tatum supports HMAC webhook digest for those who want to verify their origin. 

## Using HMAC and advantages

With HMAC, each notification fired by Tatum has within the HTTP header a digest in the `x-payload-hash` field, which users can reconstruct on their end. 

- You can trust the webhook content wasn't changed by a "[Man-in-the-middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack)", otherwise, the digest will not match.
- You can trust that only Tatum could calculate the hash, hence you can trust the request was fired by Tatum and not an attacker.
- Find the related v3 REST API endpoint at [the following link](https://apidoc.tatum.io/tag/Notification-subscriptions/#operation/enableWebHookHmac).

## IP Whitelisting

Alternatively, although not recommended, you can whitelist Tatum IPs in your Web Application Firewall (WAF). 

- Tatum IP ranges are available in the following file: [tatum.io/ips.json](https://ips.tatum.io/ips.json)
- Using HMAC is a much more reliable approach compared to IP whitelisting.
