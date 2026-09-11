# Harbor

> The library of ready-to-run money agents on Sail Protocol.

[![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)

**Harbor** is the library of ready-to-run money agents, built on [Sailor](https://github.com/sail-money/Sailor). Sailor is the harness that turns any AI coding agent into a builder and operator of money agents; Harbor ships complete, installable agents you start with one command instead of building from scratch.

A Harbor agent never holds your private key and acts only through a **mandate**: deterministic onchain permissions checked on every transaction. That is what makes a Harbor agent safe to run with real money.

## Start in Claude Code or Codex

Use **Node.js 22+**. Run one of these commands in your terminal (or ask your coding agent to run it). Choose one agent; no repository clone or global Sailor installation is needed.

**Portfolio:** choose your own assets and weights.

```bash
npx @sail.money/sailor@latest harbor create portfolio my-portfolio --no-agent
```

**Onchain Finance Portfolio:** start with the predefined basket and confirm its weights.

```bash
npx @sail.money/sailor@latest harbor create onchain-finance-portfolio my-onchain-portfolio --no-agent
```

Accept the npm installation prompt and review the blueprint import when prompted. Use a new folder name if the destination already exists. Sailor downloads the blueprint, verifies it, installs dependencies, and checks the project. `--no-agent` stops it from launching a second coding-agent session.

**Next:** open the generated folder in Claude Code or Codex, then send:

> Read AGENTS.md and guide me through setting up this portfolio agent.

The coding agent helps you install Foundry, configure an RPC endpoint for each required chain, connect your owner wallet, confirm the strategy, and sign its permissions. It explains gas and registration costs before you fund or sign. Creating the project does not start trading.

### Launch a coding agent from a standalone terminal

If you want Sailor to launch the coding-agent CLI for you, omit `--no-agent`. The selected CLI must already be installed and on your PATH. For example:

```bash
# Codex
npx @sail.money/sailor@latest harbor create onchain-finance-portfolio my-onchain-portfolio

# Or Claude Code (choose this instead)
npx @sail.money/sailor@latest harbor create onchain-finance-portfolio my-onchain-portfolio --agent claude
```

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
