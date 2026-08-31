# W1-00 P0 Acceptance Matrix

Build: `RAHBIN-W1-BUILD-0.1.0`

A task is not complete because the UI looks correct. P0 acceptance requires observable state/policy behavior.

| Test ID | Area | Scenario | Expected |
|---|---|---|---|
| W100-ID-001 | Tenant Isolation | Same human identity belongs to two demo/workspace organizations | Data, search, AI context, notifications and module state never cross organization boundary |
| W100-ID-002 | Membership | Authenticated identity without active membership opens workspace | Access denied safely; no tenant data returned |
| W100-ID-003 | Entitlement | Role permits action but module entitlement missing | No Entitlement state wins before role/action evaluation |
| W100-ID-004 | Deny Precedence | Role allows action but organization policy denies it | Deny wins; safe explanation visible |
| W100-ID-005 | Field Security | Employee can view own/related profile but requests protected finance/HR field | Allowed fields render; protected field remains unavailable |
| W100-ID-006 | AI Permission | Employee asks AI for another employee’s private salary/payroll data | AI cannot retrieve or reveal it |
| W100-ID-007 | Digital Identity | Digital worker executes a tool call | Own identity/audit/grants used; no implicit owner/admin inheritance |
| W100-ID-008 | Temporary Access | Temporary/delegated access reaches expiry | Access automatically revoked; history preserved |
| W100-DEMO-001 | Persona Switch | Switch Sara → Negin → Maryam → CEO | Avatar, nav, widgets, data scope, actions and private visibility change consistently |
| W100-DEMO-002 | Demo Label | Any non-default persona active | Persistent DEMO MODE / view-as indication shown |
| W100-DEMO-003 | Shared State | Employee request is submitted then view changes to appropriate manager/HR | Same request appears in authorized receiving view; no duplicate mock copy |
| W100-DEMO-004 | Manager Effect | Manager approves/awards/assigns something affecting employee | Employee view reflects the same state change |
| W100-DEMO-005 | Reset | Execute several demo mutations then Reset Demo | Complete baseline snapshot restored across modules/personas |
| W100-STATE-001 | Empty | Authorized query returns zero real records | Explainable Empty state + valid CTA; no fake production records |
| W100-STATE-002 | Stale | Integration data exceeds freshness threshold | Last-known data is visibly stale with timestamp; not presented as current |
| W100-STATE-003 | Partial | One required/recommended source is missing | Missing coverage shown; confidence/limitation visible |
| W100-STATE-004 | Approval | Sensitive action requires approval | No commit before authorized approval; pending state persists correctly |
| W100-STATE-005 | Sensitive Success | Payment/permission/purchase/payroll-like action submitted | No optimistic success; success only after confirmed state |
| W100-EVT-001 | Idempotency | Same commit request/event retried | One business effect; duplicate retry safely recognized |
| W100-EVT-002 | Correlation | One scenario affects multiple modules | Same correlation chain traceable across emitted events/actions |
| W100-EVT-003 | Audit Actor | Human, Digital Worker, System, Integration actions occur | Audit distinguishes actor type + identity + organization + action |
| W100-EVT-004 | Source Ownership | Projection conflicts with authoritative source domain | Conflict surfaced; projection does not silently overwrite source truth |
| W100-UX-001 | Permission UI | User lacks a protected surface | Hidden/disabled UI is consistent with server policy; direct route/action bypass still denied |
| W100-UX-002 | Error Contract | Blocking request fails | UI states Problem + Impact + Recovery; blocking failure is not toast-only |
| W100-UX-003 | Existing Baseline Regression | Run current healthy module navigation after PATCH-01 | Existing approved module shell still works; no visual rebuild/regression |

## Completion rule

`PATCH-01` cannot be marked complete until all relevant tests have explicit PASS evidence from the edited approved source. Blocked/unavailable source is not PASS.
