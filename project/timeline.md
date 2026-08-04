# Timeline

## Document Meta

- version: 0.2
- pm agent: codex
- date: 2026-08-04
- status: draft - pending answers in `project/pm_questions.md`

## Delivery Milestones

| milestone | target outcome | required tasks | status |
| --- | --- | --- | --- |
| M1 | React 기반 게임 프로젝트 실행 가능 | feat-001 | done |
| M2 | Hermes OS 기본 UI와 상태 시스템 작동 | feat-002, feat-003, feat-004 | todo |
| M3 | 카테고리 A Act 1~3 증거 제출 루프 작동 | chore-001, feat-005, feat-006, feat-007 | blocked |
| M4 | MVP 플레이 감각과 종료 흐름 완성 | feat-008 | blocked |
| M5 | QA 시나리오 수행 및 bug task 생성 | qa-001 | blocked |

## Task Timeline

| order | task id | title | dependency status | parallel group | expected handoff |
| --- | --- | --- | --- | --- | --- |
| 1 | feat-001 | Bootstrap Vite + React game project | clear | A | done |
| 2 | feat-002 | Build Hermes OS terminal shell | clear | B | review approved |
| 3 | feat-003 | Implement oxygen and power game state | clear | B | review approved |
| 4 | feat-004 | Build category A file system data | clear | B | review approved |
| 5 | chore-001 | Align content fixtures with planning docs | clear after feat-004 | C | review approved |
| 6 | feat-006 | Implement Log Fixer recovery interaction | clear after feat-002, feat-004 | C | review approved |
| 7 | feat-005 | Implement evidence attachment and act progression | waiting for Q4 | D | review approved |
| 8 | feat-007 | Implement ECHO response rules for category A | waiting for Q4, Q5 | E | review approved |
| 9 | feat-008 | Add opening, ending, visual, and audio feedback | waiting for Q2, Q3, Q7 | E | review approved |
| 10 | qa-001 | Run MVP scenario QA and create bug tickets | waiting for MVP feature completion | F | QA report and bug task docs |

## Review / QA Gates

| gate | entry condition | output |
| --- | --- | --- |
| review gate 1 | each dev task implementation complete | review approve or max 2 rejection loop |
| PM clarification gate | blocked task references unresolved Q id | human answer and updated docs |
| QA gate 1 | M4 complete | scenario result, failed cases, bug task creation |

## Bottleneck Watchlist

- 카테고리 A Act 3 증거 조합이 확정되지 않으면 `feat-005`, `feat-007`을 완료할 수 없다.
- 3D/R3F 포함 여부가 확정되지 않으면 `feat-008` 범위가 커질 수 있다.
- ECHO가 deterministic rule인지 외부 AI/API인지 확정되지 않으면 response architecture가 달라진다.
