# ThinkChain

ThinkChain is an on-chain service that enables smart contracts to perform _verifiable_ large language model (LLM) inference.
The service provides access to a variety of popular LLMs, such as DeepSeek-R1, DeepScaleR, Qwen2.5 and SmolLM2.
A simple Solidity interface makes it easy for smart contracts to construct prompts and decode replies entirely on-chain.
Completion requests are charged in Ether.

_Client_ contracts send completion requests to the _Completer_ contract, which issues tasks to EigenLayer operators.
Operators run the selected inference model inside a Cartesi Machine to guarantee determinism.
Results are then signed by operators, and an aggregated signature is submitted to a solver.
Once the solver submits the signed result on-chain, the _Completer_ forwards it to a _Callback_ contract, designated by the _Client_.

ThinkChain is suitable for smart contracts that would benefit from on-chain access to LLMs.
Examples of use cases include AI agents, AI-assisted decision making, data analysis, and content generation.
_Client_ contracts can propagate the cost of using the service to their users, and even charge extra for their services.

## Features

- Access to a wide variety of LLMs
- Simple Solidity interface
- Configurable inference options
- Fast finality
- Accepts payments in Ether

## Overview

For a quick overview and demo of the project,
you can watch the presentation submitted for [Cartesi X EigenLayer Experimentation Week](https://cartesi-x-eigenlayer.devfolio.co/):

[![ThinkChain Quick Demo](https://img.youtube.com/vi/Ni0cgn2cR2o/0.jpg)](https://youtu.be/Ni0cgn2cR2o)

## Getting Started

First, please make sure your machine contains all the necessary [dependencies](https://docs.mugen.builders/cartesi-co-processor-tutorial/installation).
Then, clone this repository and its [submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) recursively.

```sh
git clone --recurse-submodules https://github.com/guidanoli/thinkchain.git
```

In order to run ThinkChain locally, you first need to start up a devnet.

```sh
cartesi-coprocessor start-devnet
```

Once the devnet is up, you may publish the machine.

```sh
cartesi-coprocessor publish --network devnet
```

Then, you may deploy the contracts.

```sh
make deploy
```

Once the contracts are deployed, you can interactively request a completion.

```sh
make request
```

## Documentation

You can learn more about ThinkChain smart contracts [here](./contracts/README.md).

## Web Frontend

This repository also includes a proof-of-concept chat app that uses ThinkChain.
You can run it locally and interact with it through a web front-end.

```sh
make run-frontend-dev
```

In order to interact in the frontend you will need to import a wallet with funds,
you could import the wallet with the private key
`0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80`
in Metamask browser extension.

## Related projects

- [Cartesi Co-processor](https://github.com/zippiehq/cartesi-coprocessor)
- [Cartesi](https://cartesi.io/)
- [EigenLayer](https://www.eigenlayer.xyz/)

## Authors

- Eduardo Bart ([edubart](https://github.com/edubart))
- Felipe F. Grael ([felipefg](https://github.com/felipefg))
- Guilherme Dantas ([guidanoli](https://github.com/guidanoli))

## License

ThinkChain is licensed under GPL-3.0.
