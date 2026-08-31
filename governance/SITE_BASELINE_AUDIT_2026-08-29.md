# RAHBIN Site Baseline Audit — 2026-08-29

## Purpose

Record the actual approved website/demo baseline before Build 0.1.0 changes. This is an execution reference only; product truth remains in Google Sheet CURRENT.

## Approved baseline

- Public demo reference: `https://samanesh-interactive-demo.firdos09867.chatgpt.site`
- Source identifier used in prior direct code review: `rahbin-offline-source`
- Key workspace file observed in direct code review: `components/premium-workspace.tsx`
- Rule: upgrade this approved baseline; do not rebuild or visually replace it from scratch.

## What is already present in the baseline

- Premium RTL customer workspace shell
- Main module navigation
- Module pages with submodule data
- Employee/workplace demo data
- Reward / recognition surfaces
- Private payslip demo surface
- Module-aware workspace behavior

## Known baseline gaps found by direct code review

1. **Persona state is not unified yet.** Workspace identity is effectively single-user while demo people live in separate data arrays. Persona switch must change navigation, avatar, default view and data scope — not only display name.
2. **Submodules are not independent product pages yet.** Current module page renders submodules inline/accordion-style. Frozen architecture requires independent deep-linkable submodule surfaces with contextual tabs/states.
3. **Recognition / Hall of Honor is partly hard-coded.** Period recognition, personal archive, nomination/evidence/approval/correction flow and state-driven history need to be connected to the shared demo state.
4. **Later frozen decisions exceed the current live code.** Decisions covering Diagnostic → Architecture → Checkout, stateful CRM, seven personas, employee finance, League Basic, Integration Hub, onboarding, and S31 QA are implementation targets, not evidence that the current site already implements them.

## Build interpretation

The gap between the existing site and frozen CURRENT source is **not** permission to redesign. It is the Build 0.1.x patch backlog.

Implementation must preserve:

- visual baseline and design language,
- existing healthy interactions,
- module/submodule catalog identity,
- RTL/premium character,
- prior user-approved site structure where not superseded by an explicit locked Decision ID.

## Source availability note

The editable `rahbin-offline-source` artifact is not currently mounted in the connected GitHub/Drive/File Library sources. A prior direct code audit provides verified file-level evidence of its current structure. Do not create a parallel replacement codebase merely because the Work artifact is not mounted in this tool session.

## Next execution gate

1. Complete W1-00 shared contract/foundation mapping.
2. Patch the same approved source when the editable Work artifact is available in the active workspace.
3. First integrated UI/state patch should establish shared persona/runtime state and policy-aware shell before deep module-specific changes.
4. Every patch requires Decision ID + ClickUp + test/read-back evidence.
