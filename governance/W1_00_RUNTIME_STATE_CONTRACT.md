# W1-00 — Runtime State Contract

Build: `RAHBIN-W1-BUILD-0.1.0`
Trace: `States_RBAC_V2.4.9`, `S26`

No critical surface may silently collapse Loading, Empty, Permission, Entitlement, Stale, Partial and Failure into one generic UI.

## Shared states

### Loading
- scoped fetch only
- skeleton for primary content
- no blank flash

### Empty
- means zero real records
- explain why it is empty
- offer the valid next action
- never seed fake production data

### No Permission
- deny safely
- no sensitive object-existence leak
- explain insufficient permission at the safe level

### No Entitlement
- distinguish from permission denial
- identify required capability/module outcome where allowed
- never unlock by client-side state only

### Expired / Limited Mode
- retain permitted history/data
- writes/AI/automation disabled per policy
- show persistent expiry state

### Stale Data
- last-known data may be shown only when safe
- visible timestamp/freshness warning
- never present stale as current

### Partial Data
- state missing sources/coverage
- calculations must expose limited confidence
- never silently interpolate business facts

### AI — No Evidence / Low Confidence
- no unsupported fact assertion
- evidence/confidence state visible
- no high-impact automatic action

### Human Approval Required
- pending action is not committed
- show effect/evidence/reason
- approve/reject/expire lifecycle

### Partial Provisioning Failure
- completed safe steps remain
- retry is idempotent
- never duplicate tenant/user/entitlement

## Error presentation rule

Every meaningful error communicates:

1. Problem
2. Impact
3. Recovery

A toast alone is not sufficient for a blocking or high-impact failure.

## Acceptance

- State is deterministic and testable.
- No success is shown before confirmed server state for sensitive operations.
- Widget-level failure does not crash unrelated dashboard surfaces.
- Freshness and confidence remain visible on decision-relevant data.

Status: `ACTIVE CONTRACT — IMPLEMENTATION REQUIRED`
