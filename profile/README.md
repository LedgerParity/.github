![LedgerParity banner](assets/banner.png)

# LedgerParity

Reconciliation for Stellar payment operators: bring your application's payment
ledger into parity with ordinary classic Stellar payment operations — exactly,
read-only, and reproducibly.

**Developer preview.** No demonstrated operator adoption or production-readiness
claim. The reconciliation CLI never signs, funds, or moves funds, and it never fabricates
missing evidence.

Full documentation: **[ledgerparity.vercel.app](https://ledgerparity.vercel.app/)**
(also available at [ledgerparity.github.io](https://ledgerparity.github.io/)) —
overview, concepts, quick start, evidence discipline, and roadmap.

## Why it exists

Stellar settles payments on-chain; operators keep their own payment records.
When a settlement notification is missed, an amount is off by a stroop, or a
record is duplicated, someone has to compare an application export against the
chain by hand. LedgerParity makes that comparison exact, auditable, and
replayable.

## Repositories

| Repository | Role |
|---|---|
| [ledger-parity-core](https://github.com/LedgerParity/ledger-parity-core) | Matching engine and read-only Horizon ingestion. Exact stroop amounts; explicit network, sender, recipient, asset and interval identity; the unproven always stays `UNKNOWN`. |
| [ledger-parity-connectors](https://github.com/LedgerParity/ledger-parity-connectors) | Validated import of application exports — JSON/CSV plus a release-pinned [SDP 7.0.0](https://github.com/LedgerParity/ledger-parity-connectors/blob/main/docs/SDP.md) payment CSV adapter. |
| [ledger-parity-cli](https://github.com/LedgerParity/ledger-parity-cli) | Runnable operator workflow: configure → reconcile → capture replayable evidence → verify byte-identical offline replays. Includes dashboard and report verification. |
| [-ledger-parity-contract](https://github.com/LedgerParity/-ledger-parity-contract) | Owner-authorized report hash registration; synthetic Protocol 28 testnet validation and a read-only lifetime monitor. Hash registration does not prove report correctness. |

Download [v0.3.1-preview](https://github.com/LedgerParity/ledger-parity-cli/releases/tag/v0.3.1-preview) for Windows, Linux or macOS, including checksums and the offline dashboard.

## Try it

From any repo checkout (Go 1.22.2+):

```sh
go test ./...
go vet ./...
```

The CLI offline SDP workflow requires no accounts, secrets, or network:

```sh
ledger-parity --config examples/sdp/config.json \
  --bundle evidence.json --out report.json
ledger-parity --replay evidence.json --out replayed.json
```

## What "parity" means here

- A match requires the same network passphrase, sender, recipient, asset
  type/code/issuer, amount, and time window — nothing is rounded or aliased.
- Observations without proof of coverage are reported, never silently assumed.
- Every decision, coverage limitation, and dependency pin is documented in each
  repository's `DECISIONS.md`, `PROJECT_HANDOFF.md`, `docs/backlog.md`, and
  `docs/GAP_ASSESSMENT.md`.

## Contributing

See [GOVERNANCE.md](GOVERNANCE.md), [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md),
and each repository's `CONTRIBUTING.md`. Security guidance lives in each
repository's `SECURITY.md`; treat exports and reports as sensitive data.

All repositories are MIT licensed.