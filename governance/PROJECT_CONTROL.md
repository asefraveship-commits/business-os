# RAHBIN Project Control

## Goal
Keep Wave 1 implementation aligned, traceable, reversible and impossible to silently drift from frozen decisions.

## Three-layer governance

### Google Sheet CURRENT
Authoritative for product decisions, frozen scope, pricing, design contract, decision IDs, source alignment and release gates.

### ClickUp
Authoritative for execution status, owner, task progress, blockers and delivery coordination.

### GitHub
Authoritative for code, branches, pull requests, build manifests, test evidence, diffs and release artifacts.

GitHub and ClickUp may mirror references, but neither may override Google Sheet CURRENT.

## Change protocol

Every implementation change follows:

1. Read current source / relevant Decision ID(s)
2. Classify change
3. Make minimal atomic implementation change
4. Validate
5. Read back / diff
6. Run focused tests
7. Attach evidence
8. Update ClickUp execution status
9. Update build manifest/checkpoint when materially changed

No change is considered complete without read-back/test evidence.

## Allowed change classifications

- `W1-P0 Fix`
- `W1-P1 Polish`
- `W2 Candidate`
- `Rejected / Duplicate`

## Scope freeze break conditions

Wave 1 scope may only be broken for:

1. Security / Privacy
2. Legal / Commercial blocker
3. Golden Scenario blocker
4. Hard technical dependency

## Drift stop conditions

Stop before merge when:

- a Decision ID conflicts with implementation,
- a proposed feature has no classification,
- current pricing cannot be traced,
- Wave 2 behavior is presented as active Wave 1 behavior,
- a dead/fake control is introduced,
- RBAC/privacy is bypassed,
- cross-module state diverges,
- existing approved demo baseline would be replaced rather than upgraded,
- a change cannot be reversed safely.

## Required checkpoint cadence

A checkpoint must be recorded after every material build block or major fix set in:

- GitHub build manifest / PR evidence,
- ClickUp task status/comment,
- Google Sheet execution register when status/build line changes.

## Release

No public/offline Stable build before S31 Release Certification PASS. P0 cannot be waived.
