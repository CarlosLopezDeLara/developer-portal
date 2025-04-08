---
id: query-tip
sidebar_label: Tip
title: Query Tip
sidebar_position: 2
description: Retrieve the latest block information from the local Cardano node.
keywords: [Cardano, CLI, query, blockchain, tip]
---

### Description

The `cardano-cli query tip` command retrieves information about the latest block known to the local node. This includes details such as the current block number, epoch, era, block hash, slot number, and synchronization progress.

### Usage

```sh
cardano-cli query tip   [--mainnet | --testnet-magic NATURAL]
                        [--socket-path SOCKET_PATH]
                        [--volatile-tip | --immutable-tip]
                        [--out-file FILEPATH]
```

### Examples

#### Querying the current tip

Running the command without any flags is equivalent to using `--volatile-tip`:

```sh
cardano-cli query tip
```

or explicitly:

```sh
cardano-cli query tip --volatile-tip
```

Example output:

```json
{
    "block": 11499370,
    "epoch": 540,
    "era": "Conway",
    "hash": "b3f8470a08492479ddd793674e62aaa0f73c31d8c910721c86e832c5e32ea69b",
    "slot": 148295912,
    "slotInEpoch": 379112,
    "slotsToEpochEnd": 52888,
    "syncProgress": "100.00"
}
```
#### Querying the immutable tip

```sh
cardano-cli query tip --immutable-tip
```
Example output:

```json
{
    "block": 11497210,
    "epoch": 540,
    "era": "Conway",
    "hash": "65abf25ae949e3ca6ccc446ce47e8ed32a0789fe2a7e7ddb620b2677741b474d",
    "slot": 148253430,
    "slotInEpoch": 336630,
    "slotsToEpochEnd": 95370,
    "syncProgress": "99.98"
}
```

#### Saving output to a file

The default behavior prints output to `stdout`. To save it to a file:

```sh
cardano-cli query tip --out-file tip.json
cat tip.json
```

Example file content:

```json
{
    "block": 11499370,
    "epoch": 540,
    "era": "Conway",
    "hash": "b3f8470a08492479ddd793674e62aaa0f73c31d8c910721c86e832c5e32ea69b",
    "slot": 148295912,
    "slotInEpoch": 379112,
    "slotsToEpochEnd": 52888,
    "syncProgress": "100.00"
}

```

### JSON Output Schema

The command returns JSON data with the following structure:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "block": {
      "type": "integer",
      "description": "The latest block number known to the local node."
    },
    "epoch": {
      "type": "integer",
      "description": "The current epoch number."
    },
    "era": {
      "type": "string",
      "description": "The name of the current Cardano era."
    },
    "hash": {
      "type": "string",
      "description": "The hash of the latest block, represented as a 64-character hexadecimal string."
    },
    "slot": {
      "type": "integer",
      "description": "The absolute slot number since the genesis block."
    },
    "slotInEpoch": {
      "type": "integer",
      "description": "The slot number within the current epoch."
    },
    "slotsToEpochEnd": {
      "type": "integer",
      "description": "The number of slots remaining until the epoch ends."
    },
    "syncProgress": {
      "type": "string",
      "description": "The synchronization progress as a percentage (e.g., '100.00')."
    }
  },
  "required": [
    "block",
    "epoch",
    "era",
    "hash",
    "slot",
    "slotInEpoch",
    "slotsToEpochEnd",
    "syncProgress"
  ],
  "additionalProperties": false
}

```

[^1]: The security parameter (`k`) defines the depth at which blocks are considered stable: **Mainnet**: `k=2600` **PreProduction**: `k=2600` **Preview**: `k=432`


