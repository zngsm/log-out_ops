# PM Analysis

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-05
- status: updated - MVP scope mostly confirmed
- source folder: `project/human-input`

## Source Documents

### Human-authored rough plans

- `LOG_OUT 기획서.md`
- `LOG_OUT visual 기획서.md`
- `LOG_OUT 로그파일 구조.md`
- `LOG_OUT 로그 예시.md`
- `LOG_OUT AI 프롬포트 예시.md`

### Structured planning forms

- `project_brief.md`
- `gameplay_spec.md`
- `scene_flow.md`
- `direction_and_content.md`
- `asset_plan.md`

## Confirmed Project Understanding

`LOG_OUT`은 우주선 헤르메스호 통제실에 갇힌 플레이어가 선내 OS 파일 탐색기에서 로그와 설정 파일을 조사하고, ECHO AI와의 대화에서 증거를 제출해 격리 판단을 단계적으로 무너뜨리는 SF 텍스트 추리/퍼즐 게임이다.

플레이어의 핵심 목표는 ECHO의 오판 근거를 Act 1, Act 2, Act 3 순서로 반박해 통제실 문을 해제하고 탈출하는 것이다. 기본 플레이는 좌측 파일 탐색기와 우측 AI 대화창, 산소/전력 HUD를 중심으로 진행된다.

## Core Loop

1. 플레이어가 Hermes OS 파일 탐색기에서 로그, 설정, 복구 대상 파일을 탐색한다.
2. 관련 파일을 읽고 격리 판단의 결함을 추론한다.
3. ECHO 대화창에 증거 파일과 텍스트 주장을 제출한다.
4. 정답이면 다음 Act로 진행하고, 오답이면 전력이 차감되어 산소 소모가 가속된다.
5. Act 3까지 성공하면 통제실 문이 열리고 MVP 기준 탈출 엔딩으로 종료된다.

## MVP Candidates Found In Documents

- Vite + React + TypeScript 기반 웹 게임
- Hermes OS 스타일의 듀얼 패널 UI
- 파일 탐색기, 파일 뷰어, 증거 첨부, AI 대화창
- 산소 100%, 전력 100%, 오답 전력 -15%, 전력 구간별 산소 소모 가속
- Bio-hazard 카테고리 A의 Act 1~3 증거 흐름
- `Log_Fixer.exe` 또는 동등한 복구 상호작용
- ECHO의 단계별 응답 규칙
- MVP 완료 조건: Act 3 논리 해제 후 통제실 문 개방

## Scope Conflicts

### MVP category scope

Resolved: MVP에서는 카테고리 A 단일 시나리오만 먼저 구현한다. 나머지 시나리오는 MVP 이후 확장 후보로 둔다.

### Visual implementation scope

Resolved: MVP에서도 배경 우주선과 컴퓨터는 R3F 기반 3D 모델이 필요하다. 손 모델은 placeholder로 구현한다. Hermes OS는 3D 컴퓨터 화면과 어우러지는 2D UI로 구현한다.

### Act 3 evidence scope

Resolved: 카테고리 A MVP의 Act 3 정답 증거는 원문 기획서 기준인 `ai_priority_matrix.json` + `deleted_override.txt`로 확정한다.

### AI prompt completeness

Partially resolved: ECHO는 외부 AI/API 연동으로 구현한다. 다만 provider, model, auth env var, fallback 정책은 아직 필요하므로 `pm_questions.md`의 Q11로 추적한다.

## PM Readiness

- 기획 방향성 분석: ready
- MVP 범위 확정: mostly ready
- 전체 task 확정: ready except external AI/API detail
- dev agent 실행 가능 task: `feat-002`, `feat-003`, `feat-004`, `feat-005`, `feat-006`, `feat-008`, `feat-009`
- dev agent 실행 보류 task: `feat-007`은 Q11 답변 필요

## Recommended PM Decision

MVP는 `카테고리 A 단일 시나리오 + R3F 우주선/컴퓨터 배경 + 2D Hermes OS + placeholder 손/asset + 실제 퍼즐 + 외부 AI/API 기반 ECHO + Act 1~3 증거 제출 + 산소/전력 시스템 + Normal Ending A`로 진행한다.

외부 AI/API provider와 인증 방식만 추가 확인하면 ECHO task까지 실행 가능하다.
