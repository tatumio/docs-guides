---
title: "Sign and Broadcast a Transaction"
slug: "sign-and-broadcast-a-transaction-2"
excerpt: ""
hidden: false
createdAt: "Fri Mar 15 2024 14:29:10 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 15 2024 14:29:10 GMT+0000 (Coordinated Universal Time)"
---
Signing and broadcasting a transaction is about authorising a transfer of funds or interaction with a smart contract and then sending that authorisation to the blockchain to be processed.

```typescript
// Import the necessary library and initialize the SDK
import { UtxoWalletProvider } from '@tatumio/utxo-wallet-provider';
import { TatumSDK, Network, Bitcoin } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init<Bitcoin>({network: Network.BITCOIN,
     configureWalletProviders: [
         UtxoWalletProvider,
     ]});

// Define your transaction details
const payloadUtxo = {
   fromAddress: [{ address: 'YOUR_WALLET_ADDRESS', privateKey: 'YOUR_PRIVATE_KEY'}],
   to: [{ address: 'TARGET_WALLET_ADDRESS', value: 0.0001 }], // BTC_AMOUNT
   fee: '0.00001', // BTC_AMOUNT
   changeAddress: 'CHANGE_WALLET_ADDRESS',
}

// Sign and broadcast the transaction using the UTXO Wallet Provider submodule
const txHash = await tatumSdk.walletProvider.use(UtxoWalletProvider)
.signAndBroadcast(payloadUtxo);

// This will print the transaction hash of the broadcasted transaction
console.log(txHash);

await tatum.destroy();

```
```javascript
// Import the necessary library and initialize the SDK
import { UtxoWalletProvider } from '@tatumio/utxo-wallet-provider';
import { TatumSDK, Network } from '@tatumio/tatum';

const tatumSdk = await TatumSDK.init({network: Network.BITCOIN,
     configureWalletProviders: [
         UtxoWalletProvider,
     ]});

// Define your transaction details
const payloadUtxo = {
   fromAddress: [{ address: 'YOUR_WALLET_ADDRESS', privateKey: 'YOUR_PRIVATE_KEY'}],
   to: [{ address: 'TARGET_WALLET_ADDRESS', value: 0.0001 }], // BTC_AMOUNT
   fee: '0.00001', // BTC_AMOUNT
   changeAddress: 'CHANGE_WALLET_ADDRESS',
}

// Sign and broadcast the transaction using the UTXO Wallet Provider submodule
const txHash = await tatumSdk.walletProvider.use(UtxoWalletProvider)
.signAndBroadcast(payloadUtxo);

// This will print the transaction hash of the broadcasted transaction
console.log(txHash);

await tatum.destroy();

```