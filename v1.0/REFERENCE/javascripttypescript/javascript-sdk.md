---
title: "Get Started with JS/TS SDK"
slug: "javascript-sdk"
excerpt: "Tatum offers a very powerful JS/TS SDK which can help developers to make dapps easier and quicker."
category: 65a9112c408e3a004ae366df
hidden: false
createdAt: "Thu Feb 22 2024 12:02:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Mar 07 2024 13:49:53 GMT+0000 (Coordinated Universal Time)"
---
This page provides a step-by-step guide on getting started creating a dapp that fetches the native balance of a user under a minute.

# Prerequisites

Before diving into TatumSDK, ensure that you have the following prerequisites installed:

- **Node.js**: Ensure you have the latest LTS version installed.
- **npm**: npm is bundled with Node.js, so installing Node.js should automatically install npm.

# Installation

To install TatumSDK, simply run the following command in your terminal or command prompt:

#### Install using [npm](https://www.npmjs.com/)

```javascript
npm install @tatumio/tatum
```

#### Install using [yarn](https://yarnpkg.com/)

```javascript
yarn add @tatumio/tatum
```

#### Install using [pnpm](https://pnpm.io/)

```javascript
pnpm install @tatumio/tatum
```

# Making your first Call

Now that you have installed Tatum SDk, lets make your first call in which we will fetch the native balance of wallet in just 3 steps.

Here's the code snippet for same,

```javascript
import { TatumSDK, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init({ network: Network.ETHEREUM });
const balance = await tatum.address.getBalance({
    addresses: [addressInput.value],
});
console.log(balance.data[0]);
});
```

Try the first call in the codepen below.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/embed/MWzZXqz?default-tab=result&theme-id=light",
  "href": "https://codepen.io/tatum-devrel/embed/MWzZXqz?default-tab=result&theme-id=light",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]
