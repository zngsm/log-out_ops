# feat-010 Implement intro narrative sequence

## Status

- status: done
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

- [x] The player can understand the premise before interacting with files.
- [x] The intro explicitly connects lockdown to ECHO's bio-hazard misclassification.
- [x] The intro points the player toward file investigation and ECHO evidence submission.
- [x] The intro remains skippable and does not block QA.
- [x] Final cinematic assets are not required.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | intro narrative sequence implementation started from latest main after feat-008 |
| 2026-08-05 | review-agent | review approved | no blocking findings; intro now explains role, lockdown, ECHO misclassification, error basis, and objective |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three in feat-009.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for skippable intro narrative sequence scope | closed |

## Deliverables

- code changes: `src/App.tsx`, `src/styles.css`
- branch: `feat-010-implement-intro-narrative-sequence`
- commit: `0aa46ec`
- tests: `npm run build`, `git diff --check`

## PR Draft

- pr title: FEAT-010 인트로 내러티브 시퀀스 구현
- pr description:
  - `## Summary`
  - 플레이어 역할, 통제실 봉쇄 원인, ECHO의 생체 감염 오판, 로그 조사 목표를 설명하는 skippable 단계형 인트로 시퀀스를 구현함
  - `## Changes`
  - `src/App.tsx`: 4단계 intro narrative data, intro step state, next/skip/start flow 추가
  - `src/App.tsx`: 기존 단일 opening overlay를 사건 발생, ECHO lockdown, 오판 근거, 플레이 목표 순서의 단계형 UI로 교체
  - `src/styles.css`: intro progress bar, signal chip, telemetry boot lines, primary/ghost intro action 스타일 추가
