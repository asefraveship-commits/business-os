# PATCH-01 — Persona + Policy Shell on Approved Demo

Build: `RAHBIN-W1-BUILD-0.1.0`
Classification: `W1-P0 Fix`
ClickUp: `86cbbmqex`
Decisions: `S06`, `S21`, `S26`, `S28`, `S29`

## Non-negotiable baseline rule

Apply this patch to the existing approved `rahbin-offline-source` only. Do not reproduce the workspace as a new parallel app.

## Known source targets from prior direct code review

- `components/premium-workspace.tsx`
- `lib/rewards.ts` — current demo people source
- `lib/workplace-demo.ts` — current workplace people / payslip demo source

Exact imports/line numbers must be re-read from the mounted source before editing.

## Shared persona model

One canonical fixture/store replaces parallel person arrays for demo identity/state consumption.

Required persona IDs/names:

1. `sara-ahmadi` — سارا احمدی — sales employee / default persona
2. `ali-rezaei` — علی رضایی — high performer sales
3. `yasaman-karimi` — یاسمن کریمی — new hire
4. `milad-ahmadi` — میلاد احمدی — performance recovery scenario
5. `negin-farahmand` — نگین فرهمند — sales manager
6. `maryam-hosseini` — مریم حسینی — HR/Payroll
7. `amirhossein-nouri` — امیرحسین نوری — CEO/Owner

Minimum shared fields:

- stable persona ID
- display name
- photo asset reference
- role / team / manager relation
- demo RBAC role + scopes
- permitted module/submodule surfaces
- default route/view
- task/notification references
- wallet/RB state
- performance/prestige/league state
- academy state
- leave/mission state
- private finance/payslip reference
- approval/manager actions where relevant
- scenario tags

Do not duplicate the same business object into independent per-screen mock datasets when a shared reference can be used.

## Switch behavior

Changing active persona must update in the same render/state transaction:

- avatar/name/title
- navigation visibility
- default workspace surface
- module/submodule access
- widgets
- notifications
- tasks
- wallet/RB
- Academy
- League/Prestige
- salary/private finance visibility
- reports/manager actions/approval actions

A fixed visible banner/label must state Demo Mode and the active view-as persona. Reset-to-default must be one action.

## Security / policy behavior

- Employee: own private data only + permitted work modules.
- Manager: team operational/summary scope; no automatic peer salary/private HR.
- HR/Payroll: HR/payroll scope according to policy.
- CEO/Owner: executive/aggregate view; sensitive individual detail still follows policy.
- AI/context retrieval uses active persona permission context.
- Demo persona switch is **not** production impersonation.

## Initial Sara fixture invariants

S06 locks Sara as the default scenario with these demo anchors:

- Performance 84
- League positions include #37 / role #8 context
- Prestige Epic
- Level 18
- RB 2,480
- title «قهرمان پیگیری»
- headphone goal
- Academy growth focus on closing

Numbers may be demo-configurable later, but cross-surface references must remain internally consistent within a snapshot.

## Demo-state invariants

- Manager action affecting an employee becomes visible in that employee view.
- Employee request becomes visible to the appropriate manager/HR view.
- No screen owns a separate conflicting copy of the same demo truth.
- Reset restores the complete snapshot, not only the current page.

## Required read-back before completion

After editing the mounted source, capture:

1. changed file list
2. diff/read-back for persona source and workspace integration
3. navigation/access tests for all 7 personas
4. private finance visibility tests
5. shared-state propagation test
6. reset test
7. regression check for existing module navigation and visual shell

Status: `READY FOR SOURCE PATCH — EDITABLE WORK SOURCE NOT MOUNTED IN CURRENT CONNECTOR SESSION`
