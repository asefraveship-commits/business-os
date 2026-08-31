# RAHBIN W1 Build Manifest

## Identity

- Architecture baseline: `RAHBIN-ARCH-V2.4.9-r2`
- Frozen implementation release: `RAHBIN-W1-FREEZE-2026-08-29`
- Active implementation build: `RAHBIN-W1-BUILD-0.1.0`
- Active branch: `build/rahbin-w1-0.1.0`

## Authority

- Product decisions / scope / pricing: Google Sheet CURRENT only.
- Execution / task status: ClickUp.
- Code / PR / build / test evidence: GitHub.

## Current execution block

`W1-00 — Governance & Platform Foundation`

Primary trace sources: `S21`, `S24`, `S25`, `S26`, `S28`, `S29`.

## Required next build order

1. W1-00 Foundation
2. Existing approved demo/site baseline integration
3. Public sellable vertical slice
4. Activation/onboarding/integration
5. Operational modules
6. Employee experience/continuity
7. Expansion/AI beta
8. Golden QA / S31 release certification

## Drift rules

Stop implementation and classify before merge if a proposed change:

- contradicts a locked Decision ID,
- changes Wave 1 scope,
- introduces pricing not present in the current commercial source,
- creates a dead/fake control,
- rebuilds the approved demo from scratch,
- bypasses RBAC/privacy/security rules,
- causes cross-module state inconsistency.

## Release gate

No Stable release until the S31 certification matrix passes. P0 cannot be waived.
