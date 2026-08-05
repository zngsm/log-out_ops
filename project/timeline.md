# Timeline

## Document Meta

- version: 0.3
- pm agent: codex
- date: 2026-08-05
- status: confirmed - pending AI/API provider detail

## Delivery Milestones

| milestone | target outcome | required tasks | status |
| --- | --- | --- | --- |
| M1 | React 기반 게임 프로젝트 실행 가능 | feat-001 | done |
| M2 | Hermes OS 기본 UI, 3D 컴퓨터 배경, 상태 시스템 작동 | feat-002, feat-003, feat-004, feat-009 | done |
| M3 | 카테고리 A Act 1~3 증거 제출 루프 작동 | chore-001, feat-005, feat-006, feat-007 | blocked |
| M4 | MVP 플레이 감각과 종료 흐름 완성 | feat-008 | todo |
| M5 | QA 시나리오 수행 및 bug task 생성 | qa-001 | blocked |

## Task Timeline

| order | task id | title | dependency status | parallel group | expected handoff |
| --- | --- | --- | --- | --- | --- |
| 1 | feat-001 | Bootstrap Vite + React game project | clear | A | done |
| 2 | feat-002 | Build Hermes OS terminal shell | clear | B | done |
| 3 | feat-003 | Implement oxygen and power game state | clear | B | done |
| 4 | feat-004 | Build category A file system data | clear | B | done |
| 5 | feat-009 | Build R3F spaceship computer scene | clear | B | done |
| 6 | chore-001 | Align content fixtures with planning docs | clear after feat-004 | C | review approved |
| 7 | feat-006 | Implement Log Fixer recovery interaction | clear after feat-002, feat-004 | C | review approved |
| 8 | feat-005 | Implement evidence attachment and act progression | clear | D | review approved |
| 9 | feat-007 | Implement external AI ECHO rules for category A | waiting for Q11 | E | review approved |
| 10 | feat-008 | Add opening, ending, visual, and audio feedback | clear after feat-002, feat-003, feat-009 | E | review approved |
| 11 | qa-001 | Run MVP scenario QA and create bug tickets | waiting for MVP feature completion | F | QA report and bug task docs |

## Review / QA Gates

| gate | entry condition | output |
| --- | --- | --- |
| review gate 1 | each dev task implementation complete | review approve or max 2 rejection loop |
| PM clarification gate | blocked task references unresolved Q id | human answer and updated docs |
| QA gate 1 | M4 complete | scenario result, failed cases, bug task creation |

## Bottleneck Watchlist

- 외부 AI/API provider, model, env var, fallback 정책이 확정되지 않으면 `feat-007`을 완료할 수 없다.
- R3F 컴퓨터 배경은 MVP 범위로 확정되었으므로 `feat-009`를 `feat-002`와 병렬로 진행한다.
- 오래된 source 문서의 Act 3 예시가 task 문서와 충돌할 경우 `project/pm_questions.md`와 `project/tasks/*.md`를 우선한다.
