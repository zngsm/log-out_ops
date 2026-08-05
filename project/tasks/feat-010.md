# feat-010 Implement intro narrative sequence

## Status

- status: todo
- type: feat
- priority: 9
- owner agent: dev-agent
- branch: `feat-010-implement-intro-narrative-sequence`
- commit message: `feat-010 implement intro narrative sequence`

## Goal

Explain why the player is trapped, why ECHO is enforcing lockdown, and why the player must inspect logs before the main Hermes OS loop begins.

## Scope

- Replace the current minimal opening overlay with a clearer MVP intro sequence.
- Explain player role: Hermes ship AI-management crew member trapped in the control room.
- Explain incident start: emergency alarm, reduced power, forced door lockdown, ECHO classifying crew as risk.
- Explain ECHO's likely error basis: faulty sensor, stale calibration, clock/rule inconsistency, missing/deleted logs.
- Introduce the core objective: find files, attach evidence, and refute ECHO across Act 1~3.
- Keep the sequence skippable for debug/MVP testing.
- Do not implement final cinematic camera, rigged hands, or final voice acting.

## Dependencies

- before: `feat-008`
- after: `qa-001`

## Acceptance Criteria

- The player can understand the premise before interacting with files.
- The intro explicitly connects lockdown to ECHO's bio-hazard misclassification.
- The intro points the player toward file investigation and ECHO evidence submission.
- The intro remains skippable and does not block QA.
- Final cinematic assets are not required.
