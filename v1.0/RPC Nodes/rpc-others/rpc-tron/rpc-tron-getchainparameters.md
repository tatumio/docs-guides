---
title: "getchainparameters"
slug: "rpc-tron-getchainparameters"
excerpt: "Tron RPC"
hidden: false
metadata: 
  description: "Tron RPC"
  image: []
  keywords: "tron, rpc"
  robots: "index"
createdAt: "Wed Mar 06 2024 10:35:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Sat Apr 06 2024 15:36:46 GMT+0000 (Coordinated Universal Time)"
---
[block:html]
{
  "html": "<div style=\"padding: 10px 20px; border-radius: 5px; background-color: #e6e2ff; margin: 0 0 30px 0;\">\n  <h5>Archive Method</h5>\n  <p>Only on the full archive nodes. Complex queries might take longer and incur additional cost</p>\n</div>"
}
[/block]


### How to use it



```typescript
// yarn add @tatumio/tatum

import { TatumSDK, Tron, Network } from '@tatumio/tatum'

const tatum = await TatumSDK.init<Tron>({network: Network.TRON})

const chainParameters = await tatum.rpc.getChainParameters()

await tatum.destroy() // Destroy Tatum SDK - needed for stopping background jobs
```



### Overview

The `getChainParameters` method retrieves all parameters that the blockchain committee can set. This method is useful for getting detailed information about the blockchain's configurable parameters.

[block:embed]
{
  "html": false,
  "url": "https://codepen.io/tatum-devrel/pen/BaGEMej",
  "href": "https://codepen.io/tatum-devrel/pen/BaGEMej",
  "typeOfEmbed": "iframe",
  "height": "300px",
  "width": "100%",
  "iframe": true,
  "provider": "codepen.io"
}
[/block]

### Parameters

This method doesn't require any parameters.

### Return Object

The return object is an array of ChainParameters objects. Each ChainParameters object contains the following parameters:

- `chainParameter (array)`
  - `key` (string): The parameter name.
  - `value` (integer): The parameter value.

### HTTP Request Example

```curl
{]
```

### HTTP Response Example

```json
{
  "chainParameter": [
    {
      "key": "getMaintenanceTimeInterval",
      "value": 600000
    },
    {
      "key": "getAccountUpgradeCost",
      "value": 9999000000
    },
    {
      "key": "getCreateAccountFee",
      "value": 100000
    },
    {
      "key": "getTransactionFee",
      "value": 1000
    },
    {
      "key": "getAssetIssueFee",
      "value": 1024000000
    },
    {
      "key": "getWitnessPayPerBlock",
      "value": 100000000000
    },
    {
      "key": "getWitnessStandbyAllowance",
      "value": 100000000
    },
    {
      "key": "getCreateNewAccountFeeInSystemContract",
      "value": 1000000
    },
    {
      "key": "getCreateNewAccountBandwidthRate",
      "value": 1
    },
    {
      "key": "getAllowCreationOfContracts",
      "value": 1
    },
    {
      "key": "getRemoveThePowerOfTheGr",
      "value": -1
    },
    {
      "key": "getEnergyFee",
      "value": 420
    },
    {
      "key": "getExchangeCreateFee",
      "value": 1024000000
    },
    {
      "key": "getMaxCpuTimeOfOneTx",
      "value": 120
    },
    {
      "key": "getAllowUpdateAccountName"
    },
    {
      "key": "getAllowSameTokenName",
      "value": 1
    },
    {
      "key": "getAllowDelegateResource",
      "value": 1
    },
    {
      "key": "getTotalEnergyLimit",
      "value": 50000000000
    },
    {
      "key": "getAllowTvmTransferTrc10",
      "value": 1
    },
    {
      "key": "getTotalEnergyCurrentLimit",
      "value": 50000000000000
    },
    {
      "key": "getAllowMultiSign",
      "value": 1
    },
    {
      "key": "getAllowAdaptiveEnergy",
      "value": 1
    },
    {
      "key": "getTotalEnergyTargetLimit",
      "value": 3472222
    },
    {
      "key": "getTotalEnergyAverageUsage",
      "value": 8384
    },
    {
      "key": "getUpdateAccountPermissionFee",
      "value": 100000000
    },
    {
      "key": "getMultiSignFee",
      "value": 1000000
    },
    {
      "key": "getAllowAccountStateRoot"
    },
    {
      "key": "getAllowProtoFilterNum"
    },
    {
      "key": "getAllowTvmConstantinople",
      "value": 1
    },
    {
      "key": "getAllowTvmSolidity059",
      "value": 1
    },
    {
      "key": "getAllowTvmIstanbul",
      "value": 1
    },
    {
      "key": "getAllowShieldedTRC20Transaction",
      "value": 1
    },
    {
      "key": "getForbidTransferToContract"
    },
    {
      "key": "getAdaptiveResourceLimitTargetRatio",
      "value": 10
    },
    {
      "key": "getAdaptiveResourceLimitMultiplier",
      "value": 1000
    },
    {
      "key": "getChangeDelegation",
      "value": 1
    },
    {
      "key": "getWitness127PayPerBlock",
      "value": 10000000
    },
    {
      "key": "getAllowMarketTransaction"
    },
    {
      "key": "getMarketSellFee"
    },
    {
      "key": "getMarketCancelFee"
    },
    {
      "key": "getAllowPBFT"
    },
    {
      "key": "getAllowTransactionFeePool"
    },
    {
      "key": "getMaxFeeLimit",
      "value": 15000000000
    },
    {
      "key": "getAllowOptimizeBlackHole",
      "value": 1
    },
    {
      "key": "getAllowNewResourceModel"
    },
    {
      "key": "getAllowTvmFreeze"
    },
    {
      "key": "getAllowTvmVote",
      "value": 1
    },
    {
      "key": "getAllowTvmLondon",
      "value": 1
    },
    {
      "key": "getAllowTvmCompatibleEvm"
    },
    {
      "key": "getAllowAccountAssetOptimization"
    },
    {
      "key": "getFreeNetLimit",
      "value": 1500
    },
    {
      "key": "getTotalNetLimit",
      "value": 43200000000
    },
    {
      "key": "getAllowHigherLimitForMaxCpuTimeOfOneTx",
      "value": 1
    },
    {
      "key": "getAllowAssetOptimization",
      "value": 1
    },
    {
      "key": "getAllowNewReward",
      "value": 1
    },
    {
      "key": "getMemoFee",
      "value": 1000000
    },
    {
      "key": "getAllowDelegateOptimization",
      "value": 1
    },
    {
      "key": "getUnfreezeDelayDays",
      "value": 14
    },
    {
      "key": "getAllowOptimizedReturnValueOfChainId",
      "value": 1
    },
    {
      "key": "getAllowDynamicEnergy",
      "value": 1
    },
    {
      "key": "getDynamicEnergyThreshold",
      "value": 3000000000
    },
    {
      "key": "getDynamicEnergyIncreaseFactor",
      "value": 2000
    },
    {
      "key": "getDynamicEnergyMaxFactor",
      "value": 12000
    }
  ]
}
```
