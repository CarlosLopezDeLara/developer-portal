---
id: protocol-parameters
sidebar_label: Protocol parameters
title: Query protocol parameters
sidebar_position: 1
description: Retrieve the current protocol parameters.
keywords: [Cardano, CLI, query, blockchain, protocol parameters, parameters]
---

### Description  

The `cardano-cli query protocol-parameters` command retrieves the current protocol parameters.

### Usage  
```sh
cardano-cli conway query protocol-parameters  
                        [--mainnet | --testnet-magic NATURAL]  
                        [--socket-path SOCKET_PATH]  
                        [--out-file FILEPATH]  
```

### Example
  
Retrieving the protocol parameters:  
```sh
cardano-cli conway query protocol-parameters
```
Example output:

```json
{
    "collateralPercentage": 150,
    "committeeMaxTermLength": 146,
    "committeeMinSize": 7,
    "costModels": {
        "PlutusV1": [...],
        "PlutusV2": [...],
        "PlutusV3": [...]
    },
    "dRepActivity": 20,
    "dRepDeposit": 500000000,
    "dRepVotingThresholds": {
        "committeeNoConfidence": 0.6,
        "committeeNormal": 0.67,
        "hardForkInitiation": 0.6,
        "motionNoConfidence": 0.67,
        "ppEconomicGroup": 0.67,
        "ppGovGroup": 0.75,
        "ppNetworkGroup": 0.67,
        "ppTechnicalGroup": 0.67,
        "treasuryWithdrawal": 0.67,
        "updateToConstitution": 0.75
    },
    "executionUnitPrices": {
        "priceMemory": 5.77e-2,
        "priceSteps": 7.21e-5
    },
    "govActionDeposit": 100000000000,
    "govActionLifetime": 6,
    "maxBlockBodySize": 90112,
    "maxBlockExecutionUnits": {
        "memory": 62000000,
        "steps": 20000000000
    },
    "maxBlockHeaderSize": 1100,
    "maxCollateralInputs": 3,
    "maxTxExecutionUnits": {
        "memory": 14000000,
        "steps": 10000000000
    },
    "maxTxSize": 16384,
    "maxValueSize": 5000,
    "minFeeRefScriptCostPerByte": 15,
    "minPoolCost": 170000000,
    "monetaryExpansion": 3.0e-3,
    "poolPledgeInfluence": 0.3,
    "poolRetireMaxEpoch": 18,
    "poolVotingThresholds": {
        "committeeNoConfidence": 0.51,
        "committeeNormal": 0.51,
        "hardForkInitiation": 0.51,
        "motionNoConfidence": 0.51,
        "ppSecurityGroup": 0.51
    },
    "protocolVersion": {
        "major": 10,
        "minor": 0
    },
    "stakeAddressDeposit": 2000000,
    "stakePoolDeposit": 500000000,
    "stakePoolTargetNum": 500,
    "treasuryCut": 0.2,
    "txFeeFixed": 155381,
    "txFeePerByte": 44,
    "utxoCostPerByte": 4310
}
```

### JSON Output Schema

The command returns JSON data with the following structure:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "collateralPercentage": {
      "type": "integer",
      "description": "The percentage of collateral required for transactions using scripts."
    },
    "committeeMaxTermLength": {
      "type": "integer",
      "description": "The maximum term length (in epochs) for committee members."
    },
    "committeeMinSize": {
      "type": "integer",
      "description": "The minimum number of members required for the committee."
    },
    "costModels": {
      "type": "object",
      "description": "Cost models for different versions of Plutus.",
      "properties": {
        "PlutusV1": {
          "type": "array",
          "items": { "type": "integer" },
          "description": "Cost model parameters for PlutusV1."
        },
        "PlutusV2": {
          "type": "array",
          "items": { "type": "integer" },
          "description": "Cost model parameters for PlutusV2."
        },
        "PlutusV3": {
          "type": "array",
          "items": { "type": "integer" },
          "description": "Cost model parameters for PlutusV3."
        }
      }
    },
    "dRepActivity": {
      "type": "integer",
      "description": "The activity threshold for a DRep to remain active."
    },
    "dRepDeposit": {
      "type": "integer",
      "description": "The deposit required for registering a DRep."
    },
    "dRepVotingThresholds": {
      "type": "object",
      "description": "DRep voting thresholds for different governance actions.",
      "properties": {
        "committeeNoConfidence": { "type": "number" },
        "committeeNormal": { "type": "number" },
        "hardForkInitiation": { "type": "number" },
        "motionNoConfidence": { "type": "number" },
        "ppEconomicGroup": { "type": "number" },
        "ppGovGroup": { "type": "number" },
        "ppNetworkGroup": { "type": "number" },
        "ppTechnicalGroup": { "type": "number" },
        "treasuryWithdrawal": { "type": "number" },
        "updateToConstitution": { "type": "number" }
      }
    },
    "executionUnitPrices": {
      "type": "object",
      "description": "Pricing for execution units.",
      "properties": {
        "priceMemory": { "type": "number" },
        "priceSteps": { "type": "number" }
      }
    },
    "govActionDeposit": {
      "type": "integer",
      "description": "Deposit required for governance actions."
    },
    "govActionLifetime": {
      "type": "integer",
      "description": "The lifetime of a governance action in epochs."
    },
    "maxBlockBodySize": {
      "type": "integer",
      "description": "The maximum size of a block body in bytes."
    },
    "maxBlockExecutionUnits": {
      "type": "object",
      "description": "Execution unit limits for a block.",
      "properties": {
        "memory": { "type": "integer" },
        "steps": { "type": "integer" }
      }
    },
    "maxBlockHeaderSize": {
      "type": "integer",
      "description": "The maximum size of a block header in bytes."
    },
    "maxCollateralInputs": {
      "type": "integer",
      "description": "The maximum number of collateral inputs (UTxO) allowed in a transaction."
    },
    "maxTxExecutionUnits": {
      "type": "object",
      "description": "Execution unit limits for a transaction.",
      "properties": {
        "memory": { "type": "integer" },
        "steps": { "type": "integer" }
      }
    },
    "maxTxSize": {
      "type": "integer",
      "description": "The maximum size of a transaction in bytes."
    },
    "maxValueSize": {
      "type": "integer",
      "description": "The maximum size of a transaction output value."
    },
    "minFeeRefScriptCostPerByte": {
      "type": "integer",
      "description": "Minimum fee per byte for reference scripts."
    },
    "minPoolCost": {
      "type": "integer",
      "description": "Minimum operational cost for a stake pool."
    },
    "monetaryExpansion": {
      "type": "number",
      "description": "The rate of monetary expansion."
    },
    "poolPledgeInfluence": {
      "type": "number",
      "description": "The influence of stake pool pledge on rewards."
    },
    "poolRetireMaxEpoch": {
      "type": "integer",
      "description": "The maximum epoch after which a pool can retire."
    },
    "poolVotingThresholds": {
      "type": "object",
      "description": "Stake pools voting thresholds for different governance actions.",
      "properties": {
        "committeeNoConfidence": { "type": "number" },
        "committeeNormal": { "type": "number" },
        "hardForkInitiation": { "type": "number" },
        "motionNoConfidence": { "type": "number" },
        "ppSecurityGroup": { "type": "number" }
      }
    },
    "protocolVersion": {
      "type": "object",
      "description": "The ledger's protocol version.",
      "properties": {
        "major": { "type": "integer" },
        "minor": { "type": "integer" }
      }
    },
    "stakeAddressDeposit": {
      "type": "integer",
      "description": "The deposit required to register a stake address."
    },
    "stakePoolDeposit": {
      "type": "integer",
      "description": "The deposit required to register a stake pool."
    },
    "stakePoolTargetNum": {
      "type": "integer",
      "description": "The target number of stake pools for the network."
    },
    "treasuryCut": {
      "type": "number",
      "description": "The fraction of rewards allocated to the treasury."
    },
    "txFeeFixed": {
      "type": "integer",
      "description": "The fixed transaction fee."
    },
    "txFeePerByte": {
      "type": "integer",
      "description": "The per-byte transaction fee."
    },
    "utxoCostPerByte": {
      "type": "integer",
      "description": "The cost per byte for UTXO entries."
    }
  },
  "required": [
    "collateralPercentage",
    "committeeMaxTermLength",
    "committeeMinSize",
    "costModels",
    "dRepActivity",
    "dRepDeposit",
    "dRepVotingThresholds",
    "executionUnitPrices",
    "govActionDeposit",
    "govActionLifetime",
    "maxBlockBodySize",
    "maxBlockExecutionUnits",
    "maxBlockHeaderSize",
    "maxCollateralInputs",
    "maxTxExecutionUnits",
    "maxTxSize",
    "maxValueSize",
    "minFeeRefScriptCostPerByte",
    "minPoolCost",
    "monetaryExpansion",
    "poolPledgeInfluence",
    "poolRetireMaxEpoch",
    "poolVotingThresholds",
    "protocolVersion",
    "stakeAddressDeposit",
    "stakePoolDeposit",
    "stakePoolTargetNum",
    "treasuryCut",
    "txFeeFixed",
    "txFeePerByte",
    "utxoCostPerByte"
  ],
  "additionalProperties": false
}
```
