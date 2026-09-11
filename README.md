# Harbor

> The library of ready-to-run money agents on Sail Protocol.

[![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)

**Harbor** is the library of ready-to-run money agents, built on [Sailor](https://github.com/sail-money/Sailor). Sailor is the harness that turns any AI coding agent into a builder and operator of money agents; Harbor ships complete, installable agents you start with one command instead of building from scratch.

A Harbor agent never holds your private key and acts only through a **mandate**: deterministic onchain permissions checked on every transaction. That is what makes a Harbor agent safe to run with real money.

## Available agents

| Agent | Description |
|---|---|
| **Portfolio** | Build a weighted portfolio of assets (tokens and tokenized stocks) and keep it rebalanced across the chains you choose. USDC is the deposit asset; the agent bridges it with CCTP where USDC is native and with Across where it is not. |
| **Onchain Finance Portfolio** | Hold the companies whose product is money: cbHYPE and UNI (exchange), AAVE and MORPHO (credit), SKY (yield), CRCL (payments), ZAMA (privacy), rebalanced across Base, Ethereum, and Robinhood Chain. The basket ships with the agent; the thesis is in its [README](https://github.com/aadopii/onchain-finance-portfolio). |

## Where Harbor sits

| Layer | What it is | What it does |
|---|---|---|
| [Sail Protocol](https://github.com/sail-money/Protocol) | the onchain primitive | SMAs and the kernel that enforces mandates |
| [Sailor](https://github.com/sail-money/Sailor) | the harness | build and operate agents |
| **Harbor** (this repo) | the library | ready-to-run agents, one command from running |

## What a Harbor agent is

An agent in Harbor is a **blueprint**: a portable, verified package of a whole agent: its skills, its runtime, its permission contracts, and its operating guide. One command starts it, and your coding agent walks the onboarding.

Every agent is different: its own strategy, its own onboarding questions, its own dashboard and reports. What they share is the safety model: self-custody, an onchain mandate, and a fail-closed permission check on every transaction.

## Getting started

Harbor commands ship with Sailor 2.3 and later.

```bash
npm install -g @sail.money/sailor@latest
sailor harbor create portfolio                    # name your own basket
sailor harbor create onchain-finance-portfolio    # start from the Onchain Finance Portfolio basket
```

`create` pulls the blueprint, verifies every file against its manifest, shows you what it will write, scaffolds the project, installs dependencies, typechecks the runtime, and opens your coding agent to onboard you. It launches `codex` by default; pass `--agent claude` (or any executable on your PATH) to use another, or `--no-agent` to open the folder yourself.

Onboarding asks for the few things only you can provide: an RPC endpoint per chain, the owner wallet that holds custody, the assets and weights, and the mandate you sign. No keys are ever copied; the agent wallet is generated locally and encrypted.

## How the library works

Released blueprints live here as GitHub releases tagged `<slug>-v<n>`. The flow:

1. `sailor harbor publish` packages an agent and opens a review pull request; a maintainer verifies it locally and merges.
2. `sailor harbor list` searches the library.
3. `sailor harbor create <slug>` downloads the highest-numbered release for that slug.

Download counts on the release assets are the popularity metric. They are an unauthenticated counter, good for a leaderboard and nothing more.

## Trust

A blueprint is verified for **integrity** (every file is hashed and checked), not for publisher identity. Releases are not signed. Read the import plan before you approve it. Authority always stays bounded by your own keys and your onchain mandate. Blueprint signing and registry trust are separate, later concerns.

## Contributing

Harbor is built for community agents. Publish one with `sailor harbor publish`, or open a pull request against an existing blueprint. Start with the [Sailor contributing guide](https://github.com/sail-money/Sailor/blob/main/CONTRIBUTING.md). Security issues: see Sailor's [SECURITY.md](https://github.com/sail-money/Sailor/blob/main/SECURITY.md).

## License

[MIT](./LICENSE) © Agentic Finance Inc.
