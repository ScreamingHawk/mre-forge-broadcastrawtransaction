# Forge broadcastRawTransaction MRE

A minimum reproducible example for [this issue with `forge broadcastRawTransaction` command](https://github.com/foundry-rs/foundry/issues/8993).

## Issue

When trying to deploy a pre-signed transaction via a script using the following command, the script fails:

```shell
$ anvil
$ forge script script/DeployCreate2.s.sol:Deploy --rpc-url http://127.0.0.1:8545 --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
```

```shell
...
├─ [0] VM::broadcastRawTransaction(0xf8a58085174876e800830186a08080b853604580600e600039806000f350fe7fffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffe03601600081602082378035828234f58015156039578182fd5b8082525050506014600cf31ba02222222222222222222222222222222222222222222222222222222222222222a02222222222222222222222222222222222222222222222222222222222222222)
    │   └─ ← [Revert] vm.broadcastRawTransaction: transact_from_tx: No `to` field found
```

## Repo Setup

Create the repo with forge:

```shell
$ forge init mre-forge-broadcastrawtransaction
```

Delete generated files:

```shell
$ rm -rf src/ tests/ script/Counter.s.sol .github/
```

Create a new script:

```shell
$ touch script/DeployCreate2.s.sol
# Copy the content from the script/DeployCreate2.s.sol file in this repo
```
