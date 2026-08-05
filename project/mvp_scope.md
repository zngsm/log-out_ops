# MVP Scope

## Document Meta

- version: 0.2
- pm agent: codex
- date: 2026-08-05
- status: confirmed - pre-AI deterministic MVP

## MVP Goal

플레이어가 Hermes OS에서 로그와 설정 파일을 조사하고 ECHO에게 올바른 증거를 제출해 Act 1~3을 통과한 뒤 통제실 문을 열고 탈출하는 최소 완성형 플레이 경험을 만든다.

## Proposed In Scope

- Vite + React + TypeScript 웹 게임
- R3F 기반 우주선/컴퓨터 3D 배경
- Hermes OS 메인 화면
- 좌측 파일 탐색기, 중앙/좌측 파일 뷰어, 우측 ECHO 대화창
- 산소/전력 HUD
- 오답 시 전력 -15%
- 전력 구간별 산소 소모 배율
- 전력 0% 블랙아웃 및 임시 복구
- 카테고리 A Bio-hazard Act 1~3 플레이 흐름
- Act 3 정답 증거: `ai_priority_matrix.json` + `deleted_override.txt`
- 파일 열람, 증거 첨부, 증거 제출
- `Log_Fixer.exe` 또는 대체 복구 액션
- deterministic local ECHO 판정 및 Act 전환
- Act별 정답/오답 피드백
- 파일 클릭 시 `@{로그파일명}` 태그를 입력창에 주입하는 첨부 UX
- 암호, 복구, 오프셋 계산을 포함한 실제 퍼즐
- 왜 통제실 봉쇄가 발생했는지 설명하는 skippable intro narrative
- 플레이 가능한 밀도의 Category A 내부 로그/문서 콘텐츠
- 첫 플레이어가 다음 행동을 이해할 수 있는 UX 가이드/soft-lock 방지 힌트
- Normal Ending A
- placeholder visual/audio asset
- 실제 60분 세션
- debug mode 15분 세션 및 컷신 스킵
- 실패 시 짧은 암전 연출

## Proposed Out Of Scope

- 10개 카테고리 procedural 생성
- 난이도별 seed 공유 시스템
- Ending B/C
- 전 승무원 구출 루트
- 최종 퀄리티의 실제 3D GLB asset 제작
- 1인칭 손 리깅 최종 컷씬
- 고품질 사운드/음악 최종 asset
- 외부 AI/API 기반 ECHO 응답 및 판정
- 자유 텍스트 입력 기반 힌트 대화

## Phase 2 Pending Decisions

- 외부 AI/API provider
- model
- API key env var 이름
- API 실패 시 fallback 정책
- AI/API 호출을 서버 경유로 할지 여부

## MVP Acceptance Criteria

- 사용자는 게임을 시작해 Hermes OS 화면에 진입할 수 있다.
- 사용자는 파일 탐색기에서 카테고리 A 관련 파일을 열람할 수 있다.
- 사용자는 Act 1, Act 2, Act 3에 맞는 증거를 제출할 수 있다.
- Act 3은 `ai_priority_matrix.json` + `deleted_override.txt` 조합으로 통과한다.
- 정답 제출 시 ECHO가 다음 Act로 상태를 전환한다.
- ECHO는 MVP에서 deterministic local rule로 증거 조합과 텍스트 intent를 판정한다.
- 외부 AI/API 기반 ECHO는 phase 2로 분리한다.
- 오답 제출 시 전력이 차감되고 산소 소모/위험 UI가 갱신된다.
- Act 3 성공 시 문 해제 상태와 Normal Ending이 표시된다.
- 산소가 0%가 되면 실패 상태가 표시된다.
