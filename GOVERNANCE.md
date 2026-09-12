# Governance

This document describes how the LedgerParity preview is maintained. It is a
social agreement, not a legal or commercial warranty.

## Status

LedgerParity is a **developer preview**. There is no demonstrated operator
adoption, production-readiness, or availability promise. Nothing here is an
admission of, or claim about, any external program, Drips, or partnership.

## Maintainers

Maintainers own merge decisions, CI verification, and release-worthy statements.
Current maintenance is by the project's original contributor. New maintainers
can be added by consensus of existing maintainers.

## Contribution process

- Open an issue before significant changes; the decision records
  (`DECISIONS.md` per repository) are the binding history.
- Pull requests must pass tests, vet, and build on the compatibility floor
  (Go 1.22.2) and a current stable Go.
- Evidence claims must be truthful: local runs are local, remote CI is remote,
  synthetic fixtures are synthetic, and external validation is external.
- No fabricated fixtures, no inferred completeness, no signed or submitted
  transactions, no fund movement.

## Decision records

Significant decisions are recorded in each repository's `DECISIONS.md`,
`ROADMAP.md`, and `docs/backlog.md`. Reverts and corrections are encouraged
over retroactive rewriting; mistakes are documented, not deleted.

## Conflicts and removal

Disputes are resolved by maintainer consensus. Persistent rule violations are
handled per [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). Contributors who do not
wish their work to continue may ask to have their contributions removed or
attributed differently; removal is handled on a best-effort basis without
rewriting repository history.

## No warranty

The software is distributed under the MIT License, which provides no warranty
or liability. The brand usage rules and honesty standards documented in this
organization's repositories remain applicable regardless of license terms.