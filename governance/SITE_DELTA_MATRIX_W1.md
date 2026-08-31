# RAHBIN W1 — Approved Site Delta Matrix

Build: `RAHBIN-W1-BUILD-0.1.0`
Baseline: approved `samanesh-interactive-demo...chatgpt.site` / prior direct code audit of `rahbin-offline-source`

## Status legend

- `VERIFIED_CODE` — observed in prior direct code review of the live demo source.
- `USER_APPROVED_BASELINE` — explicitly part of the approved site/version history, but not re-read from source in the current connector session.
- `FROZEN_TARGET` — required by CURRENT frozen decisions; does **not** mean currently implemented.
- `NEEDS_SOURCE_MOUNT` — cannot be truthfully marked implemented until editable source is mounted/read back.

| Surface | Baseline status | W1 target / delta | Primary trace |
|---|---|---|---|
| Premium RTL workspace shell | VERIFIED_CODE | Preserve; apply policy-aware shared shell | S21, S26 |
| Main module workspace | VERIFIED_CODE | Preserve modules; module Home becomes domain command center, not feature dump | S16 |
| Submodule content | VERIFIED_CODE | Currently inline/accordion; migrate to independent deep-linkable submodule surfaces with contextual tabs/states | S17 |
| Demo people | VERIFIED_CODE | Current parallel demo arrays must become one shared 7-person persona fixture/state model | S06, S21 |
| Persona switch | FROZEN_TARGET | Switch must change nav, default page, private data scope, avatar, alerts and module access; visibly DEMO MODE | S06, S21 |
| Payslip demo | VERIFIED_CODE | Current generic/static payslip becomes private per-person «مالی من» state | S19, S21 |
| Recognition / Hall of Honor | VERIFIED_CODE | Current partly hard-coded page becomes evidence/approval/history/personal archive driven; no negative public wall | S05/M15 decisions |
| League Basic | FROZEN_TARGET | Internal individual/role/team rank + League Score + trend/history/privacy/basic anti-gaming/share card | EXT-LEAGUE, S28 |
| Employee Reward Store | USER_APPROVED_BASELINE | Preserve desired premium store direction; connect to unified RB/wishlist/goal/equip state rather than standalone decorative screen | S01-S06, S28 |
| CRM | USER_APPROVED_BASELINE | Upgrade to stateful operational CRM with Lead→Deal→Won→Retention story and cross-module effects | S15, M04 |
| Manager OS | FROZEN_TARGET | W1 operational command/attention/approval/action experience | M02, S28 |
| Sales | FROZEN_TARGET | W1 seller execution integrated with CRM, not duplicate customer/opportunity truth | M05, S28 |
| Operations | FROZEN_TARGET | W1 process/systemization/continuity spine | M16, S28 |
| Reports & Analytics | FROZEN_TARGET | W1 shared freshness/evidence/metric/report experience | M18, S28 |
| Public Hero | USER_APPROVED_BASELINE | Preserve visual baseline; align final locked hero copy/CTA without redesign from scratch | S09, S26 |
| Story Scroll | USER_APPROVED_BASELINE | Final ~5-frame cinematic marketing story, accessible/reduced-motion fallback | S08, S26 |
| Three-path Solution Finder | FROZEN_TARGET | «می‌دانم چه می‌خواهم / نوع کسب‌وکار / راه‌بین تشخیص دهد» | S10 |
| Module/Submodule Builder | FROZEN_TARGET | Expandable panel below selected module row; no modal-only flow | S11 |
| Unified «معماری راه‌بین من» | FROZEN_TARGET | Selection + Impact + Coverage + Demo State + Dependency + Entitlement + Timeline + Integration + Price | S12 |
| Diagnostic 360 | FROZEN_TARGET | Evidence/confidence/why/impact/Now-Next-Later recommendation chain | S13 |
| Business Packages | FROZEN_TARGET | Starting blueprints, not rigid SKU lock-in | S14 |
| Commercial/Checkout | FROZEN_TARGET | Single catalog/commercial snapshot → quote/proforma/payment/invoice/entitlement; no fake success | S22, S28 |
| Login | FROZEN_TARGET | Remove ChatGPT login; Rahbin Identity entry paths | S21 |
| Onboarding | FROZEN_TARGET | Adaptive purchased-scope readiness flow, not large generic form | S24 |
| Integration Hub | FROZEN_TARGET | Shared platform layer with source ownership/freshness/health/retry/idempotency | S25 |
| AI Video Producer Beta | FROZEN_TARGET | L2 workflow; external publish only after human approval | S18, S28 |
| Demo Scenario Engine | FROZEN_TARGET | 7 personas + shared seed/state/reset + 10 Golden + cross-module effects | S27, S31 |
| W2 modules M08–M20 deep controls | FROZEN_TARGET | Explicit Preview/Roadmap/Custom-order only where not in W1; no fake/dead controls | S28 |

## Critical implementation rule

A row marked `FROZEN_TARGET` must never be shown as completed merely because the product decision is locked. Implementation completion requires source diff/read-back and test evidence.

## First patch sequence on the approved source

1. Shared persona/runtime identity + policy-aware shell.
2. Global runtime states + entitlement/permission/freshness states.
3. Event/audit/idempotency hooks.
4. Module Home / independent submodule navigation foundation.
5. Then public sellable vertical slice and W1 operational modules according to `Implementation_Pack_W1`.

Status: `BASELINE DELTA AUDIT COMPLETE — IMPLEMENTATION NOT IMPLIED`
