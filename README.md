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
- Active implementation build: `RAHBIN-W1-BUILD-0.3.15`
- Active checkpoint: `PATCH-35`
- W1-04 status: `SOURCE COMPLETE`
- W1-12 status: `SOURCE COMPLETE`
- W1-13 status: `RELEASE SECURITY SOURCE FREEZE VERIFIED / FINAL CERT BLOCKED`
- W1 release readiness roll-up: `90%` (source/security readiness; rendered/runtime/deployment gates remain open)
- Source ZIP SHA-256: `b17296cbcfcace58b7d15bb218a589f45d36825429e5ee790b88ce9089fefbe0`
- Rendered-cert kit SHA-256: `26bed15635f950c73db47231be3a42d13e3a8418ef64f0d3ec3ef38f0be4d231`
- RC runner bundle SHA-256: `4dc8ca4d942b50ecddc042aa79bfd19586f2dc2a2df8e6c039fe46f2c72abfcb`
- **DEPLOYMENT-VERIFIED: NO**

## Latest source-verified checkpoint

`Build 0.3.15 / PATCH-35` is a release-only W1-P0 security hardening patch on top of Build 0.3.14. It adds no product scope and does **not** issue the Final Release Certificate.

PATCH-35 removes raw unexpected backend exception messages from public 5xx API responses while preserving governed, user-safe 403/409 policy errors. No database schema, Drizzle model, domain library, product component, or Worker behavior was changed by this patch.

Public-safe verification summary:

- PATCH-35 release-security source verifier: `17/17 PASS`
- Source scope + rollback to exact Build 0.3.14: `410 assertions PASS`
- Offline Capability Manifest/source readiness: `22 assertions PASS`
- Golden source roll-up: `10/10 PASS` (`53 assertions`)
- Persona certification: `7/7 PASS` in deterministic source cases
- RBAC leakage: `0` in source positive/negative cases
- Persona/RBAC/Invariants suite: `88 assertions PASS`
- Security/source guards: `25/25 PASS`
- Runnable dependency-free Node tests in the current sandbox: `137/137 PASS`
- Dependency-backed tests currently unavailable in the sandbox: `9`, all blocked by missing `react` or `vite` packages rather than assertion failures
- Route gate: `271/271` unique, `1173/1173` tab round-trips, `271/271` fallback
- TS/TSX parse: `148 files / 0 errors`
- CSS brace balance: `0`
- Suspicious raw public 5xx exception-message scan: `0`
- Source ZIP integrity: `PASS`

## Build and runtime status

Dependency-backed release build is **NOT RE-VERIFIED on this exact SHA**. The current sandbox cannot resolve `registry.npmjs.org`; the exact lockfile references 831 registry tarballs while the available local cache covers only 44, leaving 787 unavailable. `npm run build` therefore exits `69` before application compilation because `vinext` is unavailable in this environment.

An independent user-provided diagnostic on an older Aug-29 source successfully installed `vinext@0.0.50` and completed the build in a network-capable environment. That supports an environment/network root-cause hypothesis, but it does not certify this exact 0.3.15 artifact.

The canonical local rendered-certification runtime for this source is `npm run dev` using Vite + `@cloudflare/vite-plugin` / workerd. Raw Node `vinext start` is not treated as the certification runtime.

A frozen sidecar rendered-cert kit and RC runner bundle are prepared for the exact 0.3.15 source. They verify source/kit identity before installation and are designed to collect rendered Golden, persona/RBAC/security, RTL/responsive/accessibility, cookie/header, screenshot, JSON and runtime evidence without mutating the frozen source.

Final Release Certificate remains **BLOCKED** pending: exact dependency-backed build, Cloudflare Vite/workerd rendered runtime, rendered Golden 10/10, rendered Persona 7/7 + security checks, RTL/Persian/responsive certification, automated + manual accessibility evidence, security-header review, Offline Artifact smoke, runtime rollback, and RC → Canary → Stable promotion of the same artifact without rebuild.

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
- Change classification
- Acceptance gate(s)
- Test evidence / regression impact
- Explicit statement that no pricing/scope/product decision was invented in GitHub

## Security note

This repository is currently public. Do **not** commit proprietary pricing tables, credentials, customer data, private RBAC details, secrets, private source documents or confidential Sheet exports here. Product truth remains in the private authoritative source.
