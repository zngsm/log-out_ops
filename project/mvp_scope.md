# MVP Scope

## Document Meta

- version: 0.1
- pm agent: codex
- date: 2026-08-04
- status: draft - pending answers in `project/pm_questions.md`

## MVP Goal

플레이어가 Hermes OS에서 로그와 설정 파일을 조사하고 ECHO에게 올바른 증거를 제출해 Act 1~3을 통과한 뒤 통제실 문을 열고 탈출하는 최소 완성형 플레이 경험을 만든다.

## Proposed In Scope

- Vite + React + TypeScript 웹 게임
- Hermes OS 메인 화면
- 좌측 파일 탐색기, 중앙/좌측 파일 뷰어, 우측 ECHO 대화창
- 산소/전력 HUD
- 오답 시 전력 -15%
- 전력 구간별 산소 소모 배율
- 전력 0% 블랙아웃 및 임시 복구
- 카테고리 A Bio-hazard Act 1~3 플레이 흐름
- 파일 열람, 증거 첨부, 증거 제출
- `Log_Fixer.exe` 또는 대체 복구 액션
- ECHO deterministic rule 기반 응답
- Normal Ending A
- placeholder visual/audio asset

## Proposed Out Of Scope

- 10개 카테고리 procedural 생성
- 난이도별 seed 공유 시스템
- Ending B/C
- 전 승무원 구출 루트
- 실제 3D GLB asset 제작
- 1인칭 손 리깅 컷씬
- 외부 LLM/API 기반 ECHO 판정
- 고품질 사운드/음악 최종 asset

## Pending Scope Decisions

- MVP 카테고리 범위
- MVP 엔딩 범위
- Act 3 증거 조합
- 3D/R3F 구현 여부
- ECHO 구현 방식
- timer debug mode 제공 여부
- placeholder asset 허용 범위

## MVP Acceptance Criteria

- 사용자는 게임을 시작해 Hermes OS 화면에 진입할 수 있다.
- 사용자는 파일 탐색기에서 카테고리 A 관련 파일을 열람할 수 있다.
- 사용자는 Act 1, Act 2, Act 3에 맞는 증거를 제출할 수 있다.
- 정답 제출 시 ECHO가 다음 Act로 상태를 전환한다.
- 오답 제출 시 전력이 차감되고 산소 소모/위험 UI가 갱신된다.
- Act 3 성공 시 문 해제 상태와 Normal Ending이 표시된다.
- 산소가 0%가 되면 실패 상태가 표시된다.
