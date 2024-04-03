---
title: "Authentication"
slug: "authentication"
excerpt: ""
hidden: false
createdAt: "Mon Feb 05 2024 12:31:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Feb 05 2024 12:31:20 GMT+0000 (Coordinated Universal Time)"
---
When using the Tatum API, you authenticate yourself with an API key.

X-API-Key

The API key represents your pricing plan and defines how many API calls you can make per second and what the total number of API calls per month is available for you.

One API key must be used by only one person.

Choose one of the following authentication methods:

Provide the API key in each API call.

To obtain the API key, create a Tatum account. Once you are logged in, you are automatically assigned the Free plan.

With the Free plan:

You get two API keys, one tied to the testnet of a blockchain and the other to the mainnet.  
You can make up to five API calls per second.  
When making an API call, provide the appropriate API key (testnet or mainnet) as either an HTTP header.

If you ever need your API keys, you can find them in your Tatum account.  
Get an auto-generated API key attached to API calls.

Make an API call without any API key provided. The API key will be generated and tied to your IP address. This API key is stored within the Tatum platform and is automatically attached to all your API calls.

With the auto-generated API key:

You can make up to five API calls per second.  
These limits are applied to both the testnet and mainnet.

By default, API calls with the auto-generated API key are executed against the mainnet. To make an API call to the testnet, add the type query parameter set to testnet to the endpoint URL, for example:

<https://api.tatum.com/v1/subscription?type=testnet>  
Security Scheme Type: API Key  
Header parameter name: x-api-key
