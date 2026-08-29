# W1-00 — Policy Enforcement Contract

Build: `RAHBIN-W1-BUILD-0.1.0`
Workstream: `W1-00`
Trace: `S21`, `S24`, `S25`, `S26`

This document defines the minimum implementation contract for the shared shell before deep module work. It is an execution contract, not a new product decision.

## Canonical request context

Every protected read/write/action must resolve these values before business data is returned or mutated:

- `identity_type`
- `identity_id`
- `organization_id`
- `membership_id`
- `entitlements`
- `roles`
- `requested_action`
- `resource_type`
- `resource_id` where applicable
- `scope_context`
- `field_sensitivity` where applicable
- `conditions`
- `correlation_id`

## Enforcement order

The order is fixed:

1. Authentication / valid identity
2. Active organization membership
3. Tenant boundary
4. Entitlement
5. Organization deny policy
6. Role permission
7. Scope
8. Condition
9. Field-level permission
10. Action permission
11. Step-up / approval gate when risk requires it

A later allow cannot override an earlier hard deny.

## Required outcomes

Policy evaluation returns a typed result instead of a boolean-only response:

- `ALLOW`
- `DENY_NO_MEMBERSHIP`
- `DENY_TENANT_BOUNDARY`
- `DENY_NO_ENTITLEMENT`
- `DENY_ORG_POLICY`
- `DENY_ROLE`
- `DENY_SCOPE`
- `DENY_CONDITION`
- `DENY_FIELD`
- `DENY_ACTION`
- `STEP_UP_REQUIRED`
- `HUMAN_APPROVAL_REQUIRED`

Each denied result must provide a safe user-facing reason without leaking sensitive object existence/content.

## AI rule

AI retrieval/tool calls are evaluated through the same policy path as the acting identity. AI cannot retrieve context that the user could not retrieve directly. Digital workers use their own identity and grants.

## Demo Persona rule

Persona Switch is a demo-only context switch. It may swap demo identity, navigation and state scope, but it must be visibly labeled as demo mode and must never be represented as production impersonation.

## Sensitive operations

Sensitive operations must be non-optimistic and require server-confirmed state. Examples include permission changes, payroll/finance operations, purchases, entitlement changes and high-risk AI actions.

## Audit minimum

Protected P0/P1 writes must emit an auditable record containing:

- actor identity/type
- organization
- action
- target reference
- result
- reason / approval reference when relevant
- occurred_at
- correlation_id
- idempotency_key for commit flows where relevant

## Acceptance tests

1. Same person, two organizations: no data/context crossover.
2. Valid login but no membership: workspace access denied.
3. Entitlement missing: feature blocked before role evaluation.
4. Organization deny + role allow: deny wins.
5. Entity access allowed but sensitive field denied: field remains unavailable.
6. Employee cannot obtain hidden salary/private data via AI.
7. Digital worker cannot inherit owner/admin privileges implicitly.
8. Temporary access expires deterministically.
9. Demo Persona switch changes navigation/data scope and shows demo banner.
10. API/action/export/report paths enforce policy even when UI control is hidden or bypassed.

Status: `ACTIVE CONTRACT — IMPLEMENTATION REQUIRED`
