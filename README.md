# RAHBIN — Build Governance

This repository is used as a **code/build/evidence layer** for the RAHBIN project.

## Authority order

1. Google Sheet CURRENT — product decisions, frozen scope, pricing, design contract, source alignment.
2. ClickUp — execution status, owners, task progress.
3. GitHub — code, branches, pull requests, build manifests, test evidence and release artifacts.

GitHub must **never override** the CURRENT Google Sheet.

## Current baseline

- Architecture: `RAHBIN-ARCH-V2.4.9-r2`
- Frozen implementation release: `RAHBIN-W1-FREEZE-2026-08-29`
- Active implementation build: `RAHBIN-W1-BUILD-0.3.12`
- Active checkpoint: `PATCH-32`
- W1-04 status: `SOURCE COMPLETE`
- W1-12 status: `SOURCE COMPLETE`
- W1-13 status: `SOURCE RELEASE-CERTIFICATION CLOSURE VERIFIED / FINAL CERT BLOCKED`
- Source ZIP SHA-256: `b91d5e7e15456b49c97c0ba6b01bd53d1c86bc206426447f871c74b1a22007ea`

## Latest source-verified checkpoint

`Build 0.3.12 / PATCH-32` closes source-verifiable W1-13 P0 drift and release-QA prerequisites. It does **not** issue the Final Release Certificate and does **not** certify a Stable/Public release.

Public-safe verification summary:

- Employee Experience pure: `62 assertions PASS`
- Security/source guards: `25/25 PASS`
- Golden E2E source roll-up: `10/10 PASS` (`53 assertions`)
- Persona certification: `7/7 PASS` in deterministic source cases
- RBAC leakage: `0` in source positive/negative cases
- Persona/RBAC/Invariants suite: `88 assertions PASS`
- Release source gates: `24 assertions PASS`
- Dependency-free runnable regression: `135/135 PASS`
- React/Vite-backed tests blocked by unavailable dependencies: `9` (not counted as PASS)
- Route gate: `271/271` unique, `1173/1173` tab round-trips, `271/271` fallback
- TS/TSX parse: `150 files / 0 errors`
- Protected unrelated operational + Commercial Core: `10/10 byte-identical` versus exact Build 0.3.11
- CSS brace balance: `0`
- Product-level dead-button source candidates: `0`
- Source ZIP integrity: `PASS`

Key W1-P0 closures include canonical Wallet/Ledger state across Employee Experience surfaces, closed-loop RB with public cash-out denied, peer Recognition producing Prestige evidence rather than spendable RB, employee-bound/idempotent verified Mission rewards, governed Store transaction lifecycle, Academy fail/retry/pass and 30/60/90 evidence flow, and earned Prestige remaining separate from purchased cosmetics.

Dependency-backed release build is **NOT RE-VERIFIED**. `npm run build` exits `69` before application compilation because `vinext` is unavailable in the current runtime. This remains an environment/dependency blocker, not a source compile failure and not a build PASS. No deployment is claimed.

Final Release Certificate remains **BLOCKED** pending dependency-backed build, rendered/manual Golden hybrid evidence, rendered RTL/Persian and responsive certification, WCAG 2.2 AA automated plus manual keyboard/screen-reader evidence, RC → Canary → Stable same-artifact evidence, Offline Capability Manifest PASS, and Rollback Drill PASS.

## Scope change classification

Every change must be classified as exactly one of:

- `W1-P0 Fix`
- `W1-P1 Polish`
- `W2 Candidate`
- `Rejected / Duplicate`

No feature may enter Wave 1 without the formal frozen-scope exception path.

## Mandatory traceability

Every implementation PR must include:

- Decision ID(s)
- Workstream ID
- ClickUp task ID
- Change classification
- Acceptance gate(s)
- Test evidence / regression impact
- Explicit statement that no pricing/scope/product decision was invented in GitHub

## Security note

This repository is currently public. Do **not** commit proprietary pricing tables, credentials, customer data, private RBAC details, secrets, private source documents or confidential Sheet exports here. Product truth remains in the private authoritative source.
