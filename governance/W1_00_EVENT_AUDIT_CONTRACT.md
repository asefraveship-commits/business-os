# W1-00 — Event, Audit & Idempotency Contract

Build: `RAHBIN-W1-BUILD-0.1.0`
Trace: `Data_Event_Contract_V2.4.9`, `NFR-004`, `NFR-007`, `NFR-013`

## Shared event envelope

Every cross-module event must carry:

- `event_id`
- `schema_version`
- `event_type`
- `occurred_at`
- `organization_id`
- `actor_type`
- `actor_id`
- `subject_type`
- `subject_id`
- `source_module`
- `source_system` when external
- `correlation_id`
- `causation_id` when applicable
- `idempotency_key` for commit/retry-sensitive paths
- `sensitivity`
- `payload`
- `metadata`

## Rules

1. `event_id` is immutable.
2. Consumers of retryable events are idempotent.
3. A retry must not create duplicate payments, orders, entitlements, imports, approvals or other committed business objects.
4. Source-domain ownership is preserved. An event may project state into another module but cannot silently transfer source-of-truth ownership.
5. Sensitive writes are auditable and preserve actor, reason/approval and correlation.
6. Corrections use a new event/version/reversal path where the domain requires historical integrity; destructive overwrite is not the default.

## Observability

Critical flows expose enough structured telemetry to calculate:

- p50
- p95
- p99
- error rate
- retry count
- queue/pending depth where applicable
- last successful state/freshness

## Acceptance tests

- duplicate external event is processed once for business effect;
- repeated user submit with same idempotency key does not duplicate commit;
- correlation ID follows a multi-module scenario end-to-end;
- failed integration retry preserves original business intent and audit history;
- source-domain conflict is surfaced rather than silently overwritten;
- audit actor distinguishes Human, Digital Worker, System and Integration identities.

Status: `ACTIVE CONTRACT — IMPLEMENTATION REQUIRED`
