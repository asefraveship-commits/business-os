# RAHBIN W1 — PATCH-17 Commercial Approval / Tax / Entitlement Contract

Status: IMPLEMENTATION CONTRACT / W1-10 ONLY / NO DEPLOYMENT

Authority: CURRENT Google Sheet `RAHBIN | Master Product Catalog & Governance | CURRENT W1-FROZEN — V2.4.9-r2`.
Primary frozen decision source: `Decision_S22_Commercial_Engine`.
Predecessor: Build 0.2.6 / PATCH-16 — versioned Quote/Proforma/Contract/Invoice lifecycle foundation.

## Scope boundary

PATCH-17 may only close the next unresolved W1-10 leg:
1. internal commercial approval transitions + auditable decision history;
2. effective tax source snapshot at invoice issue time;
3. signed Contract / confirmed Payment -> deterministic Entitlement activation;
4. reconciliation of Commercial Order, Contract, Invoice, Payment and Entitlement state.

It MUST NOT start W1-11, W1-12 or any W2 module. It MUST NOT deploy. It MUST NOT expose privileged commercial mutations to the public demo.

## Frozen commercial rules to preserve

- Checkout is the continuation of `معماری راه‌بین من`; the customer buys a versioned architecture/scope, not ad-hoc module toggles.
- Architecture is frozen/versioned before payment and that exact snapshot feeds Quote -> Contract -> Entitlement -> Implementation Scope.
- Quote/Proforma revisions are append-only revisions; prior revisions become superseded, never edit-in-place.
- Internal Deal Desk may require Salesperson -> Commercial Manager -> Technical Validation -> Finance -> Customer.
- Discount/margin-sensitive transitions require explicit approval policy; no implicit AI approval.
- Final Invoice comes from the exact Commercial Order snapshot and requires explicit effective tax rate/source at issue time; no hard-coded tax.
- Purchase -> Entitlement rule: active Contract/confirmed Payment -> Commercial Order -> Entitlement Engine -> purchased modules enabled; demo configuration becomes workspace configuration only after entitlement activation.
- Public demo may inspect commercial artifacts but may not approve spend, sign contract, issue final invoice, mark paid, or directly activate entitlement.

## Required state model

### Approval event
Each privileged decision is append-only and must record:
- `approval_event_id`
- `commercial_order_id`
- `architecture_version`
- `order_version`
- `document_type`
- `document_revision`
- `approval_stage`
- `decision` = APPROVED | REJECTED | RETURNED_FOR_REVIEW
- `actor_role`
- `actor_id`
- `reason_code`
- `comment`
- `created_at`
- `idempotency_key`

No current-status-only mutation is sufficient without an immutable event.

### Effective tax snapshot
Final invoice issue requires all of:
- `tax_rate_effective`
- `tax_source_type`
- `tax_source_ref`
- `tax_jurisdiction`
- `tax_effective_at`
- `tax_snapshot_version`

If any required field is absent, invoice remains Draft/Blocked. Tax is never inferred from demo constants.

### Payment confirmation
Payment confirmation must be separate from customer intent and contain:
- `payment_id`
- `commercial_order_id`
- `invoice_id`
- `amount_confirmed`
- `currency`
- `payment_method`
- `provider_or_bank_ref`
- `confirmed_by_role`
- `confirmed_by_actor_id`
- `confirmed_at`
- `idempotency_key`

Customer-side `I paid`/upload evidence cannot by itself transition to confirmed payment.

### Entitlement activation
Entitlement activation must be deterministic from the frozen order snapshot and must record:
- `entitlement_set_id`
- `organization_id`
- `commercial_order_id`
- `architecture_version`
- `order_version`
- `contract_id`
- `invoice_id`
- `payment_id`
- `activated_capabilities`
- `premium_entitlements`
- `effective_at`
- `activated_by`
- `activation_reason`
- `idempotency_key`

Activation must be idempotent. Replaying the same confirmed payment/contract event must not duplicate entitlements.

## Transition gates

### Contract
Allowed privileged path:
`Draft -> Pending Approval -> Approved -> Signed -> Active`

Rules:
- `Signed` requires approved current revision.
- Superseded revision can never be signed.
- public/demo actor cannot perform Approved/Signed/Active transitions.

### Invoice
Allowed path:
`Draft -> Issued -> Partially Paid | Paid | Overdue | Void | Credited | Refunded | Failed`

Rules:
- `Issued` requires current signed/active contract where contract is required, frozen Commercial Order snapshot, and complete effective tax snapshot.
- `Paid` requires confirmed payment record(s), not UI intent.

### Commercial lifecycle
Maintain vocabulary:
`Recommended -> Selected -> Quoted -> Contracted -> Provisioning -> Active -> Suspended -> Expired`

`Active` is forbidden unless entitlement activation succeeds and reconciles to the same architecture/order versions.

## RBAC / public boundary

Privileged mutations require internal capability checks. At minimum:
- Purchase Approver / designated billing authority: spend commitment approval.
- Commercial Review / Deal Desk: commercial approval/rejection/return.
- Finance/Billing authority: final invoice issue and payment confirmation.
- Authorized contract signer: contract signature transition.
- Entitlement engine/system role: activation after valid upstream state.

Public demo endpoints must return denied/not-available for the above privileged mutations. UI visibility must never imply mutation authority.

## Reconciliation invariants

The following must match before entitlement activation:
- organization
- commercial_order_id
- architecture_version
- order_version
- current contract revision
- issued invoice derived from same snapshot
- confirmed payment currency/amount policy

Any mismatch blocks activation and emits an auditable reconciliation failure; no silent repair.

## Required PATCH-17 verification matrix

Minimum contract tests:
1. public actor cannot approve spend;
2. public actor cannot sign contract;
3. public actor cannot issue final invoice;
4. public actor cannot mark payment confirmed/paid;
5. public actor cannot activate entitlement;
6. stale/superseded contract revision cannot be signed;
7. invoice issue blocked without tax source snapshot;
8. invoice issue blocked with tax rate but missing source reference;
9. customer payment intent alone does not mark Paid;
10. confirmed payment event is append-only/audited;
11. entitlement activation requires matching architecture/order versions;
12. entitlement activation is idempotent on replay;
13. mismatched invoice/order version blocks activation;
14. rejected Deal Desk stage cannot advance to Signed/Issued;
15. approved current revision can progress through valid contract path;
16. valid signed contract + valid invoice + confirmed payment activates exactly the purchased entitlement set;
17. W2 preview items never become active entitlements from W1 checkout;
18. Premium Manager remains entitlement, not a duplicate per-module product;
19. quote/proforma append-only revision behavior from PATCH-16 remains unchanged;
20. existing persona/RBAC, routes and six prior operational state libraries regress unchanged.

## Freeze criteria

PATCH-17 can be marked SOURCE VERIFIED only when:
- source/static/pure tests for all transition gates pass;
- RBAC negative tests pass;
- tax-source negative/positive tests pass;
- payment and entitlement idempotency tests pass;
- prior PATCH-16 document lifecycle regressions pass;
- route/submodule regressions pass;
- TS/TSX parser reports zero syntax errors;
- CSS structural check passes;
- source artifact integrity/hash is recorded.

Dependency-backed build status must be reported independently. If the package manager/compiler cannot start because `vinext` or registry/DNS is unavailable, report `BUILD NOT RE-VERIFIED — dependency/pre-compilation blocker`; do not mislabel it as an application compile failure.

No deployment is authorized by this contract.