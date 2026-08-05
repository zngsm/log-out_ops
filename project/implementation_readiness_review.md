# Implementation Readiness Review

## Document Meta

- version: 0.2
- pm agent: codex
- date: 2026-08-05
- status: reviewed - pre-AI MVP reinforcement required

## Verdict

현재 feat-007 이전 deterministic MVP는 핵심 게임 루프 검증이 가능하다. 외부 AI/API는 MVP QA의 blocker가 아니라 phase 2 확장으로 분리한다.

다만 사람 관점에서 플레이 가능한 MVP로 보이려면 `feat-010`, `chore-002`, `feat-011` 보강이 필요하다. 이 세 작업 이후 `qa-001`은 외부 AI 없이 deterministic ECHO 기준으로 진행할 수 있다.

## Confirmed Implementation Baseline

- MVP category: category A Bio-hazard only
- MVP ending: Normal Ending A only
- UI: R3F spaceship/computer scene plus 2D Hermes OS
- hand model: placeholder only
- Act 3 evidence: `ai_priority_matrix.json` + `deleted_override.txt`
- ECHO: deterministic local validation for pre-AI MVP
- file attach UX: clicking a file injects removable `@{로그파일명}` context tag into chat input
- puzzle depth: password, recovery, and offset calculation are real puzzle interactions
- session length: 60-minute normal mode, 15-minute debug mode
- debug features: cutscene skip
- failure UX: short blackout presentation

## Workability By Task

| task id | readiness | reason |
| --- | --- | --- |
| feat-001 | ready | already done |
| feat-002 | ready | 2D Hermes OS shell can be built independently |
| feat-003 | ready | resource/timer rules are defined |
| feat-004 | ready | category A file/evidence list is now explicit in task |
| feat-009 | ready | placeholder R3F scene scope is clear |
| chore-001 | ready | fixture alignment can run after feat-004 |
| feat-006 | ready | Log Fixer interaction is defined enough for MVP |
| feat-005 | ready | evidence tag UX and Act progression are now explicit |
| feat-008 | ready | visual/audio feedback scope is clear with placeholders |
| feat-010 | ready | intro narrative is required for player comprehension before AI work |
| chore-002 | ready | internal file content density is required for playable investigation feel |
| feat-011 | ready | UX guardrails are required so deterministic MVP is playable without AI hints |
| qa-001 | ready after reinforcement | can run after feat-010, chore-002, and feat-011 |
| feat-007 | deferred | phase 2 external AI work; needs Q11 provider/model/env/fallback/API route answer |

## Deferred Gap

### Q11. External AI/API contract

The ECHO AI integration task cannot be implemented safely until the following are confirmed:

- provider
- model
- API key env var name
- whether calls must go through a server route
- fallback behavior when API fails
- whether local deterministic validation is allowed as safety guard before/after AI response

## Risks To Watch

- Source docs still contain old Act 3 examples in some places. PM task docs and `pm_questions.md` are the source of truth for MVP implementation.
- R3F scene and 2D Hermes OS integration may affect layout sequencing. `feat-002` and `feat-009` should keep a clean interface boundary.
- Intro, content density, and UX guidance are more likely than AI absence to block a useful first playtest.
- External AI responses can be inconsistent unless `feat-007` defines a strict response schema and validation guard in phase 2.
- Real puzzle implementation can expand scope if passwords, recovered files, and offset calculation are not kept to category A only.

## PM Recommendation

Proceed with the ready tasks in this order:

1. `feat-002`, `feat-003`, `feat-004`, `feat-009` in parallel after `feat-001`.
2. `chore-001` and `feat-006` after `feat-004`.
3. `feat-005` after `feat-002`, `feat-003`, and `feat-004`.
4. `feat-008` after `feat-002`, `feat-003`, and `feat-009`.
5. Run `feat-010`, `chore-002`, and `feat-011` before QA.
6. Run `qa-001` against deterministic MVP behavior.
7. Answer Q11 before moving `feat-007` out of deferred phase 2.
