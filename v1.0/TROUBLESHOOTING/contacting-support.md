---
title: "Contacting Support"
slug: "contacting-support"
excerpt: ""
category: 65ae6349f216f9001c42cc4d
hidden: false
createdAt: "Mon Jan 29 2024 14:11:54 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 12:59:50 GMT+0000 (Coordinated Universal Time)"
---
Should you come across issues while using Tatum services, you may reach out to our Support team.

## Step_1: Keeping Up-to-date

We update the core API, KMS, and our SDK regularly. Please make sure you have the latest update release and verify if the issue persists.

## Step_2: Information gathering and ticket creation

1. Retrieve the "`dashboardLog`" code from the **Error Response Body**. Looks as follows:
   ```json JSON
   {
       "statusCode": ###,
       "errorCode": "###",
       "message": "###.",
       "data": [
           "###error_verbose"
       ],
       "dashboardLog": "https://dashboard.tatum.io/logs?id=####" //The Support team needs this
   }
   ```
   > 📘 Error Investigations require the "dashboardLog" id. If you did not store it or lost it, go to the Tatum Dashboard and find it in the \[[Error Logs](https://dashboard.tatum.io/logs)] section. Copy the URL.
2. **Create a Ticket**: [Submit a ticket to our support team](https://support.tatum.io/support/home) with a brief subject line naming the issue or bug.
3. **Provide Detailed Information**: In the ticket, include the following:
   - The "`dashboardLog`" id code OR the HyperLink of the URL of the Error log (from your Dashboard)
     - IF you do not have the "`dashboardLog`", we will require the cURL with Header, Payload, and Response Body, showing all the steps required to reproduce the issue from start to finish.
   - **Problem Statement**: A brief description of the issue and or Use Case. Including:
     - **Environment**: Testnet or Mainnet
     - **Timestamp**: When the issue or bug happened. E.g., 2023.01.12 - 15:00 GMT (YYYY.MM.DD)
   - **Expected Outcome**: A clear explanation of what the expected behavior should have been.
   - **Add Relevant Screenshots or Videos**: If possible, include screenshots or videos that demonstrate the issue you are encountering. This will help us understand and resolve the issue more quickly.

> 📘 As of the writing of this article, Tatum does not have an active bug bounty program. Should this change, our documentation will be revised accordingly.

## Discharge of Responsibility

You must keep your `privateKey`(s) and `mnemonics`/seed phrases confidential and secure at all times. Sharing this information with anyone can result in serious consequences such as the loss of your funds. Your private keys and mnemonics give full access to your funds, and once they are shared, you lose control over your assets. 

No legitimate `Tatum staff member` will ever ask for your private keys or mnemonics. If you are asked for this information, it is most likely a scam attempt and you should immediately report it. Your security is of the utmost importance, and we highly encourage you to never share your private keys or mnemonics with anyone, under any circumstances.

> 🚧 It is your responsibility to safeguard your Private Keys and mnemonics/seed phrases and protect them from unauthorized access.
