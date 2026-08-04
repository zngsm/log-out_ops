# PM Analysis

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-04
- status: draft - pending human answers
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

`project_brief.md`는 MVP에서 대표 카테고리 A만 완성하고 10개 카테고리 동적 생성은 제외한다고 적고 있다. 반면 `scene_flow.md`는 10개 procedural 카테고리와 Ending B/C까지 상세히 정의한다.

PM 판단: MVP 범위는 사람 확인 전까지 확정하지 않는다.

### Visual implementation scope

`project_brief.md`는 복잡한 3D/고화질 시각 연출을 MVP 제외 범위로 둔다. 반면 `direction_and_content.md`와 `asset_plan.md`는 1인칭 3D 통제실, R3F, GLB 모델, 손 리깅, 3D 컷씬을 요구한다.

PM 판단: MVP에서 3D를 실제 구현할지, 2D/CSS placeholder로 대체할지 사람 확인이 필요하다.

### Act 3 evidence scope

원문 기획서와 로그 예시는 Act 3 핵심 증거로 `ai_priority_matrix.json`과 `deleted_override.txt`를 언급한다. 구조화된 `scene_flow.md`와 `gameplay_spec.md`는 카테고리 A의 Act 3 증거로 `auxiliary_capacitor.log`와 `emergency_grid_switch.conf`를 제시한다.

PM 판단: 카테고리 A MVP의 정식 Act 3 증거 조합을 확정해야 한다.

### AI prompt completeness

AI 프롬프트 예시는 현재 최종 MVP의 Act 1~3 흐름과 완전히 맞춰져 있는지 불명확하다. 특히 door unlock 조건과 Act 3 판정 schema가 기획서 전체와 동일한지 확인이 필요하다.

PM 판단: ECHO 판정 규칙은 구현 전 별도 확정이 필요하다.

## PM Readiness

- 기획 방향성 분석: ready
- MVP 범위 확정: blocked by human questions
- 전체 task 확정: draft only
- dev agent 실행 가능 task: `feat-002`, `feat-003`, `feat-004`는 질문 답변 전에도 기반 작업으로 진행 가능
- dev agent 실행 보류 task: Act 3 판정, 3D/연출 구현, Ending B/C, 10개 카테고리 동적 생성

## Recommended PM Decision

우선 MVP는 `카테고리 A 단일 시나리오 + 2D Hermes OS 터미널 UI + placeholder asset + Act 1~3 증거 제출 + 산소/전력 시스템 + Normal Ending`으로 제한하는 것이 가장 안전하다.

단, 위 결정은 PM agent의 자체 판단이 아니라 문서 간 충돌을 줄이기 위한 권장안이다. 실제 확정은 `pm_questions.md`의 답변 이후에만 가능하다.
