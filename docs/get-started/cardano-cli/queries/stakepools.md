---
id: stake-pools
sidebar_label: Stake Pools
title: Query stake pools
sidebar_position: 3
description: Query the current list of stakepools
keywords: [Cardano, CLI, query, blockchain, stake pools, pools]
---

### Description

`cardano-cli query stake-pools` queries the node's for the current set of stake pools.

### Usage

```sh
cardano-cli query stake-pools   [--mainnet | --testnet-magic NATURAL]
                                [--socket-path SOCKET_PATH]
                                [--volatile-tip | --immutable-tip]
                                [--output-json | --output-text]
                                [--out-file FILEPATH]
```

### Examples

Running the command without any flags is equivalent to using `--output-text`:

```
cardano-cli query stake-pools
```
or explicitly:
```
cardano-cli query stake-pools --output-text
```
Example output:
```
pool1la6wjq8uaqctd05zw58dczxp6csf2z66wf726kdfyr9l7hnr6jp
pool1l7xwy6sswcpxcepf9m43sez4kwgrgxuw5ekhkavj3k2lv6njvec
pool1l7elukrgntsdwrt0hyu6sshw0rk05y82k4sjwse8u79hkhf862z
pool1llxh8l0h8g9ghz3nrzh7ndvev4x43vnk72nsemzm795vxqs6dp8
pool1llfrhf0htc528jcmp9dr2tzsjnt93y2gkjfjn5znjh9a79avwv7
pool1llwfa6erdh7k87j06y2z9999jcc84cnezwhg9e2sulrgwzrsug4
pool1llwt52flj60vwd2tv3z4qzynu9p2njvsm95cf603zemlua4f955
pool1ll5mu4rgne203spelzdgrse0v7yk9rfzkp243rtt60rgu8mh3q8
pool1llknxwa7zzugc52mnv3lpxgh7az8wnqylrxxfqhzzm9e2eufug3
pool1lll300yc7lf6v34agp6ctzxdwk6s96cu0lxq3kk0msgvzchq3f4
pool1lllmq2jgcqrag5c77lpc5m34fsqn63leadyx9tzx842n66ly3ql
```

Using `--output-json` returns the set of stake pools in JSON

```
cardano-cli query stake-pools --output-json
```

Example output:

```json
[
    "pool1la6wjq8uaqctd05zw58dczxp6csf2z66wf726kdfyr9l7hnr6jp",
    "pool1l7xwy6sswcpxcepf9m43sez4kwgrgxuw5ekhkavj3k2lv6njvec",
    "pool1l7elukrgntsdwrt0hyu6sshw0rk05y82k4sjwse8u79hkhf862z",
    "pool1llxh8l0h8g9ghz3nrzh7ndvev4x43vnk72nsemzm795vxqs6dp8",
    "pool1llfrhf0htc528jcmp9dr2tzsjnt93y2gkjfjn5znjh9a79avwv7",
    "pool1llwfa6erdh7k87j06y2z9999jcc84cnezwhg9e2sulrgwzrsug4",
    "pool1llwt52flj60vwd2tv3z4qzynu9p2njvsm95cf603zemlua4f955",
    "pool1ll5mu4rgne203spelzdgrse0v7yk9rfzkp243rtt60rgu8mh3q8",
    "pool1llknxwa7zzugc52mnv3lpxgh7az8wnqylrxxfqhzzm9e2eufug3",
    "pool1lll300yc7lf6v34agp6ctzxdwk6s96cu0lxq3kk0msgvzchq3f4",
    "pool1lllmq2jgcqrag5c77lpc5m34fsqn63leadyx9tzx842n66ly3ql"
]
```
### JSON Output Schema

When the `--output-json` option is used, the command returns data in the following JSON format:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "array",
  "items": {
    "type": "string",
    "pattern": "^pool1[0-9a-z]{52}$",
    "description": "Bech32-encoded stake pool IDs."
  },
  "minItems": 1,
  "uniqueItems": true,
  "description": "An array of stake pool IDs registered on chain."
}
```
