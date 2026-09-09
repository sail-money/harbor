# Contributing to Harbor

Harbor is the library of ready-to-run money agents on Sail Protocol. A contribution is a
**blueprint**: a packaged agent produced by `sailor harbor publish` from a project built with
[Sailor](https://github.com/sail-money/Sailor).

## Publish a blueprint

1. Build and operate your agent with Sailor until it runs unattended.
2. Fill in `.sail/share.json` (name, slug, summary, strategy, mandate, chains).
3. Run `sailor harbor publish`. It packs the agent surface, redacts your identity, scans for
   secrets, hashes every file, and opens a pull request here adding `blueprints/<slug>/`.
4. A maintainer verifies it locally (`sailor blueprint verify`, `sailor blueprint import --dry-run`)
   and merges. The merge becomes a release tagged `<slug>-v<n>`.

Before you publish, check that nothing in `scripts/` or `docs/` hard-codes your account or
agent wallet address: redaction is seeded from your `.sail/` state and cannot find a literal you
typed elsewhere.

## Update a blueprint

Publish again from the same project. The next release number is assigned on merge.

## Review standard

A blueprint is merged when its permission contracts have Foundry tests and fail closed, its
`package.json` has no auto-running scripts, its payload carries no secrets or operator identity,
and the strategy and mandate it describes match the code. See the pull request template.

## Code of conduct and licensing

Contributions are licensed under the repository's MIT license. Be direct and respectful in
reviews; the goal is agents that are safe to run with real money.
