# Timeline

## Document Meta

- version: 0.4
- pm agent: codex
- date: 2026-08-05
- status: pre-AI MVP reinforcement plan confirmed

## Delivery Milestones

| milestone | target outcome | required tasks | status |
| --- | --- | --- | --- |
| M1 | React 기반 게임 프로젝트 실행 가능 | feat-001 | done |
| M2 | Hermes OS 기본 UI, 3D 컴퓨터 배경, 상태 시스템 작동 | feat-002, feat-003, feat-004, feat-009 | done |
| M3 | 카테고리 A Act 1~3 증거 제출 루프 작동 | chore-001, feat-005, feat-006 | done with deterministic ECHO rules |
| M4 | MVP 플레이 감각과 종료 흐름 완성 | feat-008 | done |
| M5 | pre-AI MVP 이해도, 콘텐츠 밀도, UX 보강 | feat-010, chore-002, feat-011 | done |
| M6 | deterministic MVP QA 시나리오 수행 및 bug task 생성 | qa-001 | done with failures |
| M7 | QA-discovered MVP blockers 수정 | bug-001, bug-002 | done |
| P2 | external AI ECHO integration | feat-007 | deferred |

## Task Timeline

| order | task id | title | dependency status | parallel group | expected handoff |
| --- | --- | --- | --- | --- | --- |
| 1 | feat-001 | Bootstrap Vite + React game project | clear | A | done |
| 2 | feat-002 | Build Hermes OS terminal shell | clear | B | done |
| 3 | feat-003 | Implement oxygen and power game state | clear | B | done |
| 4 | feat-004 | Build category A file system data | clear | B | done |
| 5 | feat-009 | Build R3F spaceship computer scene | clear | B | done |
| 6 | chore-001 | Align content fixtures with planning docs | clear after feat-004 | C | done |
| 7 | feat-006 | Implement Log Fixer recovery interaction | clear after feat-002, feat-004 | C | done |
| 8 | feat-005 | Implement evidence attachment and act progression | clear | D | done |
| 9 | feat-008 | Add opening, ending, visual, and audio feedback | clear after feat-002, feat-003, feat-009 | E | done |
| 10 | feat-010 | Implement intro narrative sequence | clear after feat-008 | F | done |
| 11 | chore-002 | Enrich MVP internal file contents | clear after chore-001, feat-005, feat-006 | F | done |
| 12 | feat-011 | Improve MVP player guidance and UX guardrails | clear after feat-005, feat-006, feat-008 | F | done |
| 13 | qa-001 | Run deterministic MVP scenario QA and create bug tickets | clear after M5 branch merge | G | done; created bug-001 and bug-002 |
| 14 | bug-001 | Connect oxygen timer to active gameplay session | clear after qa-001 | H | done |
| 15 | bug-002 | Enforce blackout interaction lock in gameplay UI | clear after qa-001 | H | done |
| 16 | feat-007 | Implement external AI ECHO rules for category A | deferred to phase 2; waiting for Q11 | P2 | AI integration PR |

## Review / QA Gates

| gate | entry condition | output |
| --- | --- | --- |
| review gate 1 | each dev task implementation complete | review approve or max 2 rejection loop |
| PM clarification gate | blocked task references unresolved Q id | human answer and updated docs |
| QA gate 1 | M5 complete and code PRs merged | deterministic scenario result, failed cases, bug task creation |
| bugfix gate 1 | bug-001 and bug-002 fixed | MVP can proceed to human review |
| phase 2 gate | human answers Q11 and accepts AI/API integration timing | feat-007 can move from deferred to todo |

## Bottleneck Watchlist

- 외부 AI/API provider, model, env var, fallback 정책이 확정되지 않으면 `feat-007`을 완료할 수 없지만, 이는 현재 deterministic MVP QA를 막지 않는다.
- R3F 컴퓨터 배경은 MVP 범위로 확정되었으므로 `feat-009`를 `feat-002`와 병렬로 진행한다.
- 오래된 source 문서의 Act 3 예시가 task 문서와 충돌할 경우 `project/pm_questions.md`와 `project/tasks/*.md`를 우선한다.
- 현재 pre-AI MVP의 가장 큰 리스크는 외부 AI 부재가 아니라 인트로 설명 부족, 내부 파일 콘텐츠 밀도 부족, UX 가이드 부족이다.
