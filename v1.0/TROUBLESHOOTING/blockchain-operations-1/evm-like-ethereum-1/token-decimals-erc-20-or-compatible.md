---
title: "Token decimals (ERC-20 or compatible)"
slug: "token-decimals-erc-20-or-compatible"
excerpt: ""
hidden: false
createdAt: "Tue Feb 06 2024 17:22:00 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 06 2024 17:22:00 GMT+0000 (Coordinated Universal Time)"
---
**Decimals** refer to how divisible a token can be, from 0 (not divisible at all) to 18 (very divisible), and could even be higher if required.

At this time, we do not have a comprehensive list, by token, on what's the maximum amount of decimal places you need to consider. You may use the blockchain explorer and find the token you are interested in. The `symbol` and `decimal` should be accessible. 

If you still can't find the related token details, try going after the token's documentation via web search.

### Example based on sending ERC-20 via JavaScript:

```javascript JavaScript
import {sendEthOrErc20Transaction} from '@tatumio/tatum';
/**
 * Send Ethereum or supported ERC20 transaction to the blockchain.
 * @param chain - chain to work with
 * @param fromPrivateKey - private key of sender address. Private key, or signature Id must be present.
 * @param contractAddress - address of ERC20 token
 * @param digits - number of decimal points that ERC20 token has
 * @param amount - amount to be sent
 * @param to - blockchain address to send ERC20 token to
 * @returns transaction id of the transaction in the blockchain
 */
  const transaction = await sendEthOrErc20Transaction({
  chain: Currency.ETH,
  fromPrivateKey: '##_related_pric_address_here_##',
  contractAddress: '##_related_contract_address_here_##',
  digits: 10,   //This is the token decimals value
  amount: "100000",
  to: "##_destination_address_here_##"
});
```
