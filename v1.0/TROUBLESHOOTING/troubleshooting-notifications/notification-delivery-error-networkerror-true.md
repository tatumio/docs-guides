---
title: "Notifications - Delivery error: \"networkError: true\""
slug: "notification-delivery-error-networkerror-true"
excerpt: ""
hidden: false
createdAt: "Thu Feb 08 2024 20:34:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sun Feb 11 2024 16:30:23 GMT+0000 (Coordinated Universal Time)"
---
Getting the notification delivery error `networkError: true` occurs when the webhook delivery attempts fail to reach your assigned URL with your subscription. 

> 📘 This error can appear when our notification service is unable to verify the certificate of your domain.

### Example error:

```json JSON
"nextTime": 1672646494972,
"timestamp": 1672646502000,
"retryCount": 4,
"failed": true,
"response": {
     "networkError": true
 }
```

## Steps to troubleshoot

- Verify that everything is set up correctly for that subdomain/domain on your end.
- If some webhooks work but others do not, try comparing the settings between your subdomains and find differences that can lead to issues.  
  E.g., DNS settings, cipher, certificate issuer, web server settings, and more.
- To guarantee the authenticity of the notification, you may want to consider using HMAC.
