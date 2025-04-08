---
id: get-started
title: Get started 
sidebar_position: 1
sidebar_label: Get started
keywords: [cardano-cli, cli, keys, addresses, cardano-node]
---

## Setting up environment variables 

### CARDANO_NODE_SOCKET_PATH

Cardano CLI uses the *node-to-client* protocol to communicate with the node. This requires setting an environment variable for the node socket path. Ensure you use the path declared when starting the node.

```bash
export CARDANO_NODE_SOCKET_PATH=~/node.socket
```

### CARDANO_NODE_NETWORK_ID

Each network has a unique identifier (--mainnet or --testnet-magic NATURAL). This is used by the node-to-client protocol to ensure communication with a node on the desired network. It is useful to set up an environment variable for the network ID. Alternatively, you can provide the flag `--testnet-magic <network-id>` with each command that interacts with the node.  

- **Mainnet**
```bash 
export CARDANO_NODE_NETWORK_ID=mainnet 
```
- **Pre-production testnet**
```bash
export CARDANO_NODE_NETWORK_ID=1
```
- **Preview testnet**
```bash
export CARDANO_NODE_NETWORK_ID=2
```

### Using the Cardano CLI


- The squared brackets `[]` around a flag or number of flags denote an **optional** flag.
- The round brackets `()` around a flag or set of flags denote **mandatory** flags. Failing to provide all of the mandatory flags
causes an error. 
- Flags `--flag` without a `[]` or `()` are **mandatory**.

TODO


