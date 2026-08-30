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
- Active implementation build: `RAHBIN-W1-BUILD-0.3.13`
- Active checkpoint: `PATCH-33`
- W1-04 status: `SOURCE COMPLETE`
- W1-12 status: `SOURCE COMPLETE`
- W1-13 status: `RELEASE P0 SOURCE FREEZE VERIFIED / FINAL CERT BLOCKED`
- Source ZIP SHA-256: `f61fc2dfc6e37d4caeec73b2f1bc9838043b93f5f6ae9baf10c560081c862ff0`

## Latest source-verified checkpoint

`Build 0.3.13 / PATCH-33` is a release-only W1-P0 fix on top of Build 0.3.12. It closes source-level Offline Capability Manifest and rollback-readiness blockers without changing product/domain behavior.

Public-safe verification summary:

- Offline Capability Manifest/source readiness: `25 assertions PASS`
- Source rollback drill to exact Build 0.3.12: `326 assertions PASS`
- Employee Experience pure: `62 assertions PASS`
- Security/source guards: `25/25 PASS`
- Golden E2E source roll-up: `10/10 PASS` (`53 assertions`)
- Persona certification: `7/7 PASS` in deterministic source cases
- RBAC leakage: `0` in source positive/negative cases
- Persona/RBAC/Invariants suite: `88 assertions PASS`
- Route gate: `271/271` unique, `1173/1173` tab round-trips, `271/271` fallback
- TS/TSX parse: `150 files / 0 errors`
- CSS brace balance: `0`
- Source ZIP integrity: `PASS`

PATCH-33 keeps remote demo persona photos for online presentation but every product rendering has a local `/persona-fallback.svg` when the network image fails. The machine-readable Offline Capability Manifest explicitly marks production OTP/SSO, real payment, live connectors, live AI provider execution and external publishing as unavailable or fixture-only offline. No DB, Drizzle, API route, entitlement, payment, session or domain-state source is changed by PATCH-33.

Dependency-backed release build is **NOT RE-VERIFIED**. `npm run build` exits `69` before application compilation because `vinext` is unavailable. A dependency-install attempt in the current runtime reached npm registry requests but repeatedly failed with `EAI_AGAIN` DNS/network resolution errors. This remains a runtime/network dependency blocker, not a source compile failure and not a build PASS.

Final Release Certificate remains **BLOCKED** pending dependency-backed build, rendered/manual Golden hybrid evidence, rendered RTL/Persian and responsive certification, WCAG 2.2 AA automated plus manual keyboard/screen-reader evidence, rendered Offline Artifact smoke using the same RC, RC → Canary → Stable same-artifact evidence, and a runtime rollback drill on the deployable candidate.

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
