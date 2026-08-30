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
- Active implementation build: `RAHBIN-W1-BUILD-0.3.11`
- Active checkpoint: `PATCH-31`
- W1-04 status: `SOURCE COMPLETE`
- W1-12 status: `SOURCE COMPLETE`
- Source ZIP SHA-256: `4582c317ed29ecdf0ccd5e9d4e02f7c5bfa95299c67206e24dbfe473546d3331`

## Latest source-verified checkpoint

`Build 0.3.11 / PATCH-31` closes the frozen W1-12 AI Video Producer Beta source scope at Autonomy L2. The W1 role uses a dedicated stateful pipeline from Brief and verified Product Truth through Asset Readiness, Creative Plan/Cost Preview, Storyboard, controlled generation, AI QC, Human Review/Approval, Export and a demo-only publish queue. Full M17 execution and M08/M09 execution remain outside Wave 1.

Public-safe verification summary:

- AI Video static contract: `20/20 PASS`
- AI Video pure state machine: `23 assertions PASS`
- S18 source-contract audit: `27/27 PASS`
- DB/API security audit: `15/15 PASS`
- Dependency-free runnable regression: `135/135 PASS`
- React/Vite-backed tests blocked by unavailable dependencies: `9` (not counted as PASS)
- Strict pure TypeScript: `PASS`
- TS/TSX parse: `149 files / 0 errors`
- Route gate: `271/271` unique, `1173/1173` tab round-trips, `271/271` fallback
- Protected operational + Commercial Core: `10/10 byte-identical` versus exact Build 0.3.10
- CSS brace balance: `0`
- Source ZIP integrity: `PASS`

Security and scope boundaries are explicit: public provider/model/credential injection, Product Truth injection, approval/budget override, L3/L4 autonomy and live external publishing are denied. No live video provider adapter is claimed connected.

Dependency-backed release build is **NOT RE-VERIFIED**. `npm run build` exits `69` before application compilation because `vinext` is unavailable in the current runtime. This remains an environment/dependency blocker, not a source compile failure and not a build PASS. No deployment is claimed.

Next frozen path: `W1-13 Release Certification` — 10 Golden Scenarios, RBAC leakage=0, P0 inconsistency=0, dead buttons=0, reset/failure recovery and release smoke QA.

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
