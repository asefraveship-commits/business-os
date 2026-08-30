# RAHBIN — Build Governance

This repository is used as a **public-safe code/build/evidence layer** for the RAHBIN project.

## Authority order
1. Google Sheet CURRENT — product decisions, frozen scope, design/release governance.
2. ClickUp — execution status and evidence routing.
3. GitHub — public-safe build/test/release evidence.

GitHub must never override Google Sheet CURRENT.

## Current baseline
- Architecture: `RAHBIN-ARCH-V2.4.9-r2`
- Frozen implementation release: `RAHBIN-W1-FREEZE-2026-08-29`
- Active build: `RAHBIN-W1-BUILD-0.3.15`
- Active checkpoint: `PATCH-35`
- W1 Release readiness: `90%`
- W2 Governance: `100%`
- W2 Implementation: `0%` until W1 Close
- Source ZIP SHA-256: `b17296cbcfcace58b7d15bb218a589f45d36825429e5ee790b88ce9089fefbe0`
- Matrix-aligned rendered-cert kit SHA-256: `50e6052c70c8ae44a461cfd6b59d3fe03366e7eec0830bcbba57960fa9a32022`
- RC runner bundle SHA-256: `080b363c31de183a096783295edc9257bd79f14893dfada881dd5fbdaf94bad5`
- Release promotion pack SHA-256: `fae8a676a8667aec06d7818f11b7eeca1668c56e44d0223ccb842e78b9e2c945`
- Built Artifact Packager SHA-256: `bfd3271242a43e756916c16a3265be4c4cbe38ff6df14cd7f0092b6be08f92e2`
- **DEPLOYMENT-VERIFIED: NO**

## Source-verified checkpoint
PATCH-35 is a release-only W1-P0 security hardening patch. Unexpected internal 5xx responses no longer expose raw backend exception messages; governed user-safe 403/409 errors remain preserved. It adds no product scope.

Public-safe source verification:
- PATCH-35 security verifier: `17/17 PASS`
- Scope/rollback to exact 0.3.14: `410 PASS`
- Offline source readiness: `22 PASS`
- Golden source roll-up: `10/10`, `53 assertions`
- Persona source certification: `7/7 PASS`
- RBAC leakage: `0`
- Persona/RBAC/Invariants: `88 PASS`
- Security/source guards: `25/25 PASS`
- Runnable dependency-free tests: `137/137 PASS`
- Routes: `271/271`, tab round-trip `1173/1173`, fallback `271/271`
- TS/TSX parse: `148/0`
- CSS balance: `0`
- suspicious raw public 5xx scan: `0`

## Matrix-aligned rendered certification sidecar
The sidecar was audited against the authoritative Release Certification Matrix. It now has explicit evidence gates in addition to Golden 10:
- `CERT-G1-CRITICAL-ACTION-SMOKE`
- `CERT-G13-COMMERCIAL-RECONCILIATION`
- `CERT-G14-FAILURE-RECOVERY`
- `CERT-RESET`

A dependency-free source/harness Matrix Contract Preflight is also run before npm installation. On exact 0.3.15 it is `10/10 PASS`.

The rebuilt RC Runner was executed in the current sandbox through identity verification, R01 exact artifact verification and R01.5 Matrix Contract Preflight. It still stops only at R02 because this sandbox cannot resolve `registry.npmjs.org`. This is an environment/network blocker; a source defect is not established.

Canonical rendered runtime after a successful exact build: `npm run dev` using Vite + `@cloudflare/vite-plugin` / workerd.

## Remaining Final CERT gates
1. Exact dependency-backed build.
2. Immutable built artifact SHA.
3. Cloudflare Vite/workerd runtime.
4. Rendered Golden 10 + explicit matrix sidecar gates.
5. Rendered Persona 7/7 + RBAC/security.
6. RTL/Persian/responsive + automated/manual accessibility and security-header review.
7. Offline Artifact smoke.
8. Runtime rollback.
9. Same built-artifact RC → Canary → Stable, no rebuild.
10. W1 Close.

## Security note
This repository is public. Do not commit proprietary pricing, private RBAC details, credentials, customer data, private source archives, secrets or confidential Sheet exports here.