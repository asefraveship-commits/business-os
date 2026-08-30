# RAHBIN W1-11 — Support Lifecycle / SLA Gate

Authority: CURRENT W1-FROZEN V2.4.9-r2
Workstream: W1-11 Post-Purchase / Expansion
Baseline required for source mutation: exact verified Build 0.3.1 / PATCH-21
Scope classification: W1 only

## Purpose

Close the next atomic W1-11 gate without touching Change Request, Commercial Amendment, Renewal, Offboarding, Next Best Actions, or any W2 module until Support lifecycle behavior is independently verified.

## Support Ticket lifecycle

Allowed states:

`OPEN -> TRIAGED -> IN_PROGRESS -> WAITING_CUSTOMER -> RESOLVED -> CLOSED`

Additional controlled transitions:
- `TRIAGED -> OPEN` only for explicit re-triage reset.
- `IN_PROGRESS -> TRIAGED` only when ownership/severity is formally reclassified.
- `WAITING_CUSTOMER -> IN_PROGRESS` when customer response is recorded.
- `RESOLVED -> IN_PROGRESS` on governed reopen before CLOSED.
- `CLOSED` is terminal; reopening requires a new linked Support Ticket, not mutation of the closed record.

Forbidden:
- state skipping directly from OPEN to RESOLVED/CLOSED;
- silent state mutation without actor/time/audit evidence;
- converting Support Ticket into Change Request or Expansion Order;
- any W2 entitlement activation through Support.

## Required fields

Every persisted Support Ticket must preserve:
- ticket_id
- purchase/session scope
- requester/persona scope
- subject and description
- severity: LOW | NORMAL | HIGH | CRITICAL
- state
- owner/queue identity when assigned
- created_at / updated_at
- first_response_due_at
- resolution_due_at when applicable
- first_responded_at nullable
- resolved_at nullable
- closed_at nullable
- waiting_customer_since nullable
- last_transition_at
- last_transition_actor
- audit/version counter

## SLA behavior

SLA values must be configuration-driven; no irreversible hard-coded Production promise is allowed in W1 demo/source. Tests may use deterministic fixtures.

Clock rules:
- first-response clock starts at ticket creation;
- first-response clock stops only on first governed response;
- resolution clock pauses while state is WAITING_CUSTOMER and resumes on customer response;
- RESOLVED stops active resolution clock;
- CLOSED is terminal;
- severity reclassification must recompute remaining SLA from governed configuration and be auditable; it must not erase prior breach evidence.

Breach state must be derived independently for first-response and resolution targets:
`ON_TRACK | WARNING | BREACHED | MET`

## RBAC / security gate

Minimum required negative tests:
1. unauthenticated caller cannot read or mutate Support Tickets;
2. one demo purchase/session cannot read or mutate another session's ticket;
3. ordinary employee persona cannot assign ownership to a privileged queue without permission;
4. customer/requester can add scoped response but cannot force RESOLVED/CLOSED;
5. only governed support/manager roles can change severity, owner, RESOLVED, or CLOSED;
6. CLOSED ticket cannot be mutated through direct API bypass;
7. W2 module identifiers cannot be used to create entitlement or expansion side effects through Support endpoints.

## Persistence / idempotency gate

- every transition is persisted to the Support Ticket object and survives refresh/restore;
- repeated identical transition request with the same idempotency key produces one transition only;
- stale version writes are rejected instead of overwriting a newer ticket;
- transition audit remains append-only or equivalently immutable in effective history;
- Support Ticket table/API type remains distinct from Change Request and Expansion Order.

## Required verification before freezing the next build

A new source build may be frozen only if all are true:
- exact Build 0.3.1 package hash matches the previously recorded SHA-256 `b17d9e41e1054fffefcdd35449c25506385d3058b217112ae89abf916cf61ca9` before patching;
- Support lifecycle pure/static tests pass;
- lifecycle positive/negative transition matrix passes;
- SLA pause/resume/reclassification/breach fixtures pass;
- session isolation and RBAC/security negative tests pass;
- refresh/restore persistence passes;
- idempotency + stale-write tests pass;
- previous PATCH-21 Expansion persistence contract still passes;
- Commercial Core remains regression-identical unless a separately governed cross-boundary change is explicitly required;
- TypeScript/TSX parser reports zero syntax errors;
- dependency-backed build/test is reported truthfully as PASS, FAIL after compile, or BLOCKED before compile; BLOCKED must never be called compile failure;
- no deployment occurs without explicit authorization.

## Freeze boundary

Passing this gate closes only `W1-11 / Support lifecycle + SLA`.
It does NOT close W1-11 as a whole and does NOT authorize work on W1-12 or W2.

Next permitted atomic gate after this one passes:
`Versioned Change Request impact -> approval -> publish`.
