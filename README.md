# Harbor

> The library of ready-to-run money agents on Sail Protocol.

[![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)

**Harbor** is the library of ready-to-run money agents, built on [Sailor](https://github.com/sail-money/Sailor). Sailor is the harness that turns any AI coding agent into a builder and operator of money agents; Harbor ships complete, installable agents you start with one command instead of building from scratch.

Capital stays in your own **separately managed account (SMA)**. A Harbor agent never holds your private key and acts only through a **mandate**: deterministic onchain permissions checked on every transaction. That is what makes a Harbor agent safe to run with real money.

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

```bash
npx @sail.money/sailor harbor list           # see the agents available
npx @sail.money/sailor harbor create <slug>  # create one and begin onboarding
```

`harbor create` resolves the blueprint from this registry, scaffolds the project, installs dependencies, and opens your coding agent to onboard it.

Harbor is in active development on the Sailor `feature/harbor` branch; the `sailor harbor` command ships with the next Sailor release.

## How the library works

Released blueprints live here as GitHub releases tagged `<slug>-v<n>`. The flow:

1. `sailor harbor publish` packages an agent and opens a release.
2. `sailor harbor list` searches the library.
3. `sailor harbor create <slug>` downloads and starts a released agent.

Download counts on the release assets are the popularity metric.

## Trust

A blueprint is verified for **integrity** (every file is hashed and checked), not for publisher identity. Read the import plan before you approve it. Authority always stays bounded by your own keys and your onchain mandate. Blueprint signing and registry trust are separate, later concerns.

## Contributing

Harbor is built for community agents. Publish one with `sailor harbor publish`, or open a pull request against an existing blueprint. Start with the [Sailor contributing guide](https://github.com/sail-money/Sailor/blob/main/CONTRIBUTING.md).

## License

[MIT](./LICENSE) © Agentic Finance Inc.
