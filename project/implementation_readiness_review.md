# Implementation Readiness Review

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-05
- status: reviewed - conditionally workable

## Verdict

현재 기획문서와 task 문서는 MVP 개발 착수가 가능하다. 다만 전체 MVP를 끝까지 완성하려면 `Q11. 외부 AI/API provider와 인증 방식` 답변이 필요하다.

`feat-002`, `feat-003`, `feat-004`, `feat-009`, `chore-001`, `feat-006`, `feat-005`, `feat-008`은 현재 문서만으로 진행 가능하다. `feat-007`과 `qa-001`은 외부 AI/API 세부 결정 이후 진행해야 한다.

## Confirmed Implementation Baseline

- MVP category: category A Bio-hazard only
- MVP ending: Normal Ending A only
- UI: R3F spaceship/computer scene plus 2D Hermes OS
- hand model: placeholder only
- Act 3 evidence: `ai_priority_matrix.json` + `deleted_override.txt`
- ECHO: external AI/API integration
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
| feat-007 | blocked | needs Q11 provider/model/env/fallback/API route answer |
| qa-001 | blocked | should run after playable loop and ECHO integration |

## Remaining Blocking Gap

### Q11. External AI/API contract

The ECHO task cannot be implemented safely until the following are confirmed:

- provider
- model
- API key env var name
- whether calls must go through a server route
- fallback behavior when API fails
- whether local deterministic validation is allowed as safety guard before/after AI response

## Risks To Watch

- Source docs still contain old Act 3 examples in some places. PM task docs and `pm_questions.md` are the source of truth for MVP implementation.
- R3F scene and 2D Hermes OS integration may affect layout sequencing. `feat-002` and `feat-009` should keep a clean interface boundary.
- External AI responses can be inconsistent unless `feat-007` defines a strict response schema and validation guard.
- Real puzzle implementation can expand scope if passwords, recovered files, and offset calculation are not kept to category A only.

## PM Recommendation

Proceed with the ready tasks in this order:

1. `feat-002`, `feat-003`, `feat-004`, `feat-009` in parallel after `feat-001`.
2. `chore-001` and `feat-006` after `feat-004`.
3. `feat-005` after `feat-002`, `feat-003`, and `feat-004`.
4. `feat-008` after `feat-002`, `feat-003`, and `feat-009`.
5. Answer Q11 before starting `feat-007`.
6. Run `qa-001` only after `feat-007` and `feat-008` are complete.
