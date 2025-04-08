---
id: stake-address-info
sidebar_label:  Stake address info
title: Query stake address info
sidebar_position: 4
description: query delegation choices and deposits associated to a stake addresses.
keywords: [Cardano, CLI, query, blockchain, stake address information, info]
---

### Description

Querry delegation choices and deposits of asociated to a stake address.

### Usage

```
cardano-cli query stake-address-info    [--mainnet | --testnet-magic NATURAL]
                                        [--socket-path SOCKET_PATH]
                                        [--volatile-tip | --immutable-tip]
                                        --address ADDRESS
                                        [--out-file FILEPATH]
```
### Examples

```
cardano-cli conway query stake-address-info \
--address stake_test1ur9qkerxpsy725xqx7papwls90h9zkgaaxu7rejmvynpy9q5839sy 
```
```json
[
    {
        "address": "stake_test1ur9qkerxpsy725xqx7papwls90h9zkgaaxu7rejmvynpy9q5839sy",
        "govActionDeposits": {
            "777a9fc6a37a1492c55cd2f3db02ff06c7a4bf729a972308faf34e4c5efbdfa5#0": 100000000000
        },
        "rewardAccountBalance": 144189283,
        "stakeDelegation": "pool12hhawx50me8cfp3u20t6cs59k587h5chhkmvfnj454a5jzdp4q4",
        "stakeRegistrationDeposit": 2000000,
        "voteDelegation": "keyHash-d3bec0b90a409cbcca1a1ee146d64304734cabaebbc2c69c765df24b"
    }
]
```
#### Saving output to a file

```
cardano-cli conway query stake-address-info \
--address stake_test1ur9qkerxpsy725xqx7papwls90h9zkgaaxu7rejmvynpy9q5839sy \
--out-file stakeaddressinfo.json
```

### JSON Output Schema

The command returns JSON data with the following structure:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
      "address": {
        "type": "string",
        "description": "The stake address associated with the account."
      },
      "govActionDeposits": {
        "type": "object",
        "description": "A mapping of governance action id to their corresponding deposit values. Can be an empty object if no deposits exist.",
        "additionalProperties": {
          "type": "integer",
          "description": "The deposit amount associated with a governance action."
        },
        "default": {}
      },
      "rewardAccountBalance": {
        "type": "integer",
        "minimum": 0,
        "description": "The balance of the reward account in Lovelace."
      },
      "stakeDelegation": {
        "type": ["string", "null"],
        "description": "The ID of the stake pool to which the account is delegated. Can be null if not delegated."
      },
      "stakeRegistrationDeposit": {
        "type": "integer",
        "description": "The amount of deposit paid for stake registration in Lovelace."
      },
      "voteDelegation": {
        "type": ["string", "null"],
        "description": "The key hash of the delegate representing the stake address in governance votes. Can be null if not delegated."
      }
    },
    "required": [
      "address",
      "govActionDeposits",
      "rewardAccountBalance",
      "stakeRegistrationDeposit"
    ],
    "additionalProperties": false
  }
}
```
