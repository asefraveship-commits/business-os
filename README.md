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
- Active implementation build: `RAHBIN-W1-BUILD-0.3.10`
- Active checkpoint: `PATCH-30`
- W1-04 status: `SOURCE COMPLETE`
- Source ZIP SHA-256: `11e518cf5b8ace6ecdaf69b0a0da074013178cad558bd5dc8b790d203ee9b617`

## Latest source-verified checkpoint

`Build 0.3.10 / PATCH-30` closes the frozen W1-04 Onboarding & Integration Hub source scope.

Public-safe verification summary:

- S24/S25 decision source-contract audit: `40/40 PASS`
- PATCH-30 static closure: `19/19 PASS`
- PATCH-30 pure combined: `19 assertions PASS`
- Dependency-free regression: `115/115 PASS`
- Strict pure TypeScript: `PASS`
- TS/TSX parse: `146 files / 0 errors`
- Route gate: `271/271` unique, `1173/1173` tab round-trips, `271/271` fallback
- Protected operational + Commercial Core: `10/10 byte-identical` versus exact Build 0.3.9
- DB/API security audit: `15/15 PASS`
- CSS brace balance: `0`
- Source ZIP integrity: `PASS`

Dependency-backed release build is **NOT RE-VERIFIED**. `npm run build` exits `69` before application compilation because `vinext` is unavailable in the current runtime. This is recorded as an environment/dependency blocker, not a source compile failure and not a build PASS. No deployment or live provider connection is claimed.

Next frozen path: `W1-12 AI Video Producer Beta`, then `W1-13 Release Certification`.

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
