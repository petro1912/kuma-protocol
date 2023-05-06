# Overview

This repo contains source contracts and testing suites for the MCAG contracts and the KUMA Protocol. Each corresponding project directory contains documentation in the /docs folder.

The [src/kuma-protocol/](https://github.com/code-423n4/2023-02-kuma/tree/main/src/kuma-protocol) folder contains the contracts that comprise the decentralized KUMA protocol. See [docs/kuma-protocol/](https://github.com/code-423n4/2023-02-kuma/tree/main/docs/kuma-protocol/) for KUMA protocol docs.

The [src/mcag-contracts/](https://github.com/code-423n4/2023-02-kuma/tree/main/src/mcag-contracts) contains contracts that are managed by the centralized MCAG entity. See [docs/mcag-contracts/](https://github.com/code-423n4/2023-02-kuma/tree/main/docs/mcag-contracts/) for MCAG contracts docs.

# Additional Context

Please see the [docs/](https://github.com/code-423n4/2023-02-kuma/tree/main/docs/) folder for more context.


# Tests

This repo contains relevant tests for the two source projects. To run tests:

1. Make sure all git submodules are installed using `git submodule update --init`
2. Run `forge test`

Make sure `forge` is at least on the following version: `forge 0.2.0 (1a56901 2023-02-15T00:05:20.802314Z)`

To skip invariant and fuzz tests run `forge test --no-match-path "{*invariant*,*fuzz*}"`

## Quickstart Command

Alternatively use the following quickstart command:

```
rm -Rf 2023-02-kuma || true && git clone https://github.com/code-423n4/2023-02-kuma.git -j8 --recurse-submodules && cd 2023-02-kuma && git submodule update --init && foundryup && forge install && forge build && forge test --gas-report
```

## Running Static Analysis

The root folder contains a `slither.config.json` file that can be used to run static analysis on the `kuma-protocol` project. Refer to the [foundry docs](https://book.getfoundry.sh/config/static-analyzers?highlight=slither.config#slither) on how to run Slither

## Invariant testing

For the following files the invariants should be run with `fail_on_revert = true` in the `foundry.toml`:

```
[invariant]
runs = 256
depth = 256
fail_on_revert = true
```

- [KIBToken.fail.on.revert.invariant](https://github.com/code-423n4/2023-02-kuma/tree/main/test/kuma-protocol/invariants/KIBToken.fail.on.revert.invariant.sol)
- [KUMASwap.fail.on.revert.invariant](https://github.com/code-423n4/2023-02-kuma/tree/main/test/kuma-protocol/invariants/KUMASwap.fail.on.revert.invariant.sol)

Then run the tests with `forge test --match-path "*fail.on.revert*"`
