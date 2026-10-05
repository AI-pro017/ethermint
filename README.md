<!--
parent:
  order: false
-->

# Ethermint

A copy of [Ethermint](https://github.com/evmos/ethermint) v0.21, the library that adds a full Ethereum Virtual Machine to Cosmos SDK chains. It's what Evmos, and through it Cascadia, use to run Solidity contracts and speak the Ethereum JSON-RPC.

With Ethermint a Cosmos chain can run unmodified Ethereum smart contracts, use Ethereum style accounts and keys, and work with tools like MetaMask, Hardhat and ethers, while keeping Tendermint's fast finality and IBC.

## What's inside

- `x/evm`: the EVM module, which executes transactions and stores contract state
- `x/feemarket`: EIP-1559 style base fees
- `rpc/`: the Ethereum JSON-RPC server (`eth_`, `net_`, `web3_`, `debug_` and more)
- `crypto/`: `eth_secp256k1` keys and Ethereum compatible signing
- `indexer/`: a transaction indexer for fast lookups by Ethereum hash
- `cmd/ethermintd`: a sample chain that wires it all together

## Requirements

- Go 1.19 or newer
- make and git
- jq, for the local node script

## Building

```bash
git clone https://github.com/AI-pro017/ethermint.git
cd ethermint
make install
```

This installs the `ethermintd` binary.

## Running a local node

```bash
./init.sh
```

It creates a single validator chain with the ID `ethermint_9000-1`, funds a test key and starts it with the JSON-RPC enabled on `http://localhost:8545`, so you can connect MetaMask or deploy contracts with Hardhat. On Windows use `init.bat`.

## Tests

```bash
make test-unit
```

The integration tests under `tests/` use Nix to bring up full nodes.

## License

LGPL-3.0, same as the original project by Tharsis and the Evmos team. See [LICENSE](LICENSE).
