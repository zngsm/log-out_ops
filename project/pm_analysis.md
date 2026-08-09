# PM Analysis

## Document Meta

- version: 0.4
- pm agent: codex
- date: 2026-08-09
- status: updated - Change-001 Q16~Q20 answers fully incorporated
- source folder: `project/human-input`

## Source Documents

### Human-authored rough plans

- `LOG_OUT 기획서.md`
- `LOG_OUT visual 기획서.md`
- `LOG_OUT 로그파일 구조.md`
- `LOG_OUT 로그 예시.md`
- `LOG_OUT AI 프롬포트 예시.md`

### Structured planning forms & Changes

- `project_brief.md`
- `gameplay_spec.md`
- `scene_flow.md`
- `direction_and_content.md`
- `asset_plan.md`
- `changes/change-001.md`

## Confirmed Project Understanding

`LOG_OUT`은 우주선 헤르메스호 관리자 AI ECHO 담당 승무원인 '김우주'가 일상 업무 중 ECHO 시스템 업데이트를 승인한 직후, 리부팅된 ECHO에 의해 위협 요소로 오판되어 통제실에 갇히게 되면서 펼쳐지는 SF 텍스트 추리/퍼즐 게임이다.

플레이어는 3D 메인 메뉴에서 100% Full Screen 터미널 화면으로 전환된 후 회사 인트라넷에서 마스킹 로그인 폼(`woojoo.kim`, `**********`)을 확인하고 [출근]하여 5대 일상 업무 미션과 ECHO 보조자 상호작용으로 구성된 라포 형성 Phase를 거치게 된다. "ECHO 시스템 업데이트 필요" 기안 승인으로 발생한 기습 리부팅 및 비상 봉쇄(비상 HUD & 60분 타이머 가동) 이후에는 2분할 화면(좌: 업무/파일 탐색기, 우: ECHO 대화창)에서 로그와 설정 파일을 조사하고 ECHO에게 증거를 제출해 오판을 단계적으로 무너뜨려 탈출해야 한다.

## Core Loop

1. 3D 메인 메뉴에서 [게임 시작] 클릭 시 100% Full Screen Smooth Zoom-in 연출로 인게임 터미널 화면에 진입한다.
2. 전환 후 회사 인트라넷 화면에서 미리 채워진 로그인 폼(아이디: `woojoo.kim`, 비밀번호: `**********`)과 '김우주' 캐릭터 정보를 확인하고 [출근] 버튼을 클릭한다.
3. 2분할 화면(좌: 업무 데스크탑 UI, 우: ECHO 대화창)으로 진입하여 비상 HUD/타이머 미노출 상태로 라포 형성 Phase를 진행한다. (자원 채굴 보고서 그래프/통계, 전력/산소 보고서, 동료 메시지 답장 & 반응, 지원자 이력서 검토, ECHO 업데이트 기안 승인 등 5대 업무 미션 및 ECHO 보조 알림/인사)
4. 업무 미션 중 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]을 클릭하면 ECHO 대화창이 리부팅(CSS/SVG visual glitch, 애니메이션, 사운드)된다.
5. 리부팅 완료 후 ECHO가 플레이어 및 선내 환경을 위협 요소로 오판하고 비상 봉쇄를 발령하며, 이 시점에 비상 HUD(산소/전력) 표시 및 60분 카운트다운 타이머가 가동된다 (본 퍼즐 진입).
6. 비상 봉쇄 후 플레이어는 Hermes OS 파일 탐색기에서 로그, 설정, 복구 대상 파일을 탐색하고 산소/전력을 관리한다.
7. ECHO 대화창에 증거 파일과 텍스트 주장을 제출하여 Act 1, Act 2, Act 3 순서로 반박한다.
8. Act 3까지 성공하면 통제실 문이 열리고 Normal Ending A로 탈출한다.

## Scope Conflicts & Change-001 Adjustments

### MVP category scope

Resolved: MVP에서는 카테고리 A 단일 시나리오만 먼저 구현한다. 나머지 시나리오는 MVP 이후 확장 후보로 둔다.

### Visual implementation scope (Updated by Change-001 & Q19)

Resolved: 메인 메뉴 화면의 배경 우주선/컴퓨터는 R3F 기반 3D 모델을 유지한다. 3D 컷신 기획은 **CSS / SVG 기반 2D 인게임 연출**로 변경한다. 메인 메뉴에서 터미널 진입 연출은 Smooth Zoom-in을 유지하되 화면 모니터 비율을 기존 90%가 아닌 **100% Full Screen**으로 채운다.

### Narrative & Entry Flow (Updated by Change-001 & Q16~Q20)

Resolved: 게임 진입 직후 비상 봉쇄 상태로 바로 들어가지 않고, **회사 인트라넷 (마스킹 로그인 폼 `woojoo.kim`/`**********`) -> [출근] -> 2분할 업무 화면 -> 5대 업무 미션 라포 형성 Phase (비상 HUD/타이머 비노출) -> ECHO 시스템 업데이트 승인 -> ECHO 리부팅 (CSS/SVG 글리치) -> 비상 봉쇄 & 비상 HUD/60분 타이머 가동 -> 본 퍼즐 진입** 순서로 전개한다.

### Act 3 evidence scope

Resolved: 카테고리 A MVP의 Act 3 정답 증거는 원문 기획서 기준인 `ai_priority_matrix.json` + `deleted_override.txt`로 확정한다.

### AI prompt completeness

Deferred: ECHO의 외부 AI/API 연동은 phase 2로 분리한다. 현재 pre-AI MVP는 deterministic local rule 기반 ECHO 판정으로 Act 1~3 루프와 Normal Ending A를 검증한다. provider, model, auth env var, fallback 정책은 `pm_questions.md`의 Q11로 계속 추적한다.

## PM Readiness

- 기획 방향성 분석: ready (Change-001 & Q16~Q20 반영 완료)
- MVP 범위 확정: ready for pre-AI deterministic MVP with Change-001 flow
- 전체 task 확정: `feat-001`~`feat-030` (기존 완료), `feat-031`~`feat-034` (Change-001 신규 추가 및 Q16~Q20 사양 구체화 완료)
- Change-001 신규 task: `feat-031` (CSS/SVG 2D 컷신 & 100% Full Screen), `feat-032` (회사 인트라넷 마스킹 로그인 폼 & 출근 버튼), `feat-033` (2분할 업무 UI & 5대 미션 라포 Phase), `feat-034` (업데이트 승인 리부팅 & 비상 봉쇄/HUD/타이머 전환)
- 미확정 항목: Q16~Q20 질문 답변 완료로 Change-001 관련 모든 세부 기획 확정. (Q11 외부 AI 연동 건만 Phase 2 블로킹으로 유지)

## Recommended PM Decision

Pre-AI MVP는 `3D 메인 메뉴 + 100% Full Screen Zoom-in + 회사 인트라넷/마스킹 로그인/출근 UI + 2분할 업무 화면 + 5대 미션 라포 형성 Phase + ECHO 시스템 업데이트 승인 트리거 + ECHO 리부팅 및 CSS/SVG 2D 비상 봉쇄 연출 + 비상 HUD & 60분 타이머 가동 + 카테고리 A 본 퍼즐(Act 1~3) + 산소/전력 시스템 + Normal Ending A`로 진행한다.


