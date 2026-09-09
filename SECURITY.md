# Security

Harbor distributes packaged agents. The code that verifies and imports them lives in
[Sailor](https://github.com/sail-money/Sailor); report vulnerabilities in the import path, the
packer, or the registry workflow through Sailor's
[security policy](https://github.com/sail-money/Sailor/blob/main/SECURITY.md).

For a vulnerability in a published blueprint (a permission contract that can be bypassed, a
runtime that can be steered to a wrong address), use the same channel and name the blueprint
slug and release tag. Do not open a public issue for an exploitable finding.

A blueprint is verified for integrity, not for publisher identity. Releases are unsigned.
Read the import plan before approving it, and remember that the on-chain mandate you sign, not
the blueprint, is what bounds an agent.
