# MVP Scope

## Document Meta

- version: 0.4
- pm agent: codex
- date: 2026-08-09
- status: confirmed - pre-AI deterministic MVP with Change-001 (Q16~Q20 answered: CSS/SVG 2D cutscenes, Full Screen terminal, Intranet pre-filled login, 5 work missions in Rapport Phase, ECHO reboot trigger, post-reboot HUD/timer activation)

## MVP Goal

플레이어가 3D 메인 메뉴에서 100% Full Screen 터미널로 진입하여 회사 인트라넷에서 마스킹된 로그인 폼(`woojoo.kim`, `**********`)을 확인하고 [출근] 후, 라포 형성 Phase(5대 업무 미션 & ECHO 보조자 상호작용)를 진행한다. 이후 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]에 의한 기습 리부팅 및 오판 비상 봉쇄(비상 HUD & 60분 타이머 가동)가 발생하면, Hermes OS에서 로그와 설정 파일을 조사해 Act 1~3을 통과하고 통제실 문을 열어 탈출하는 최소 완성형 플레이 경험을 만든다.

## Proposed In Scope

- Vite + React + TypeScript 웹 게임
- R3F 기반 우주선/컴퓨터 3D 메인 메뉴 배경 (유지)
- 3D 컷신 대신 **CSS / SVG 기반 2D 컷신 연출** 적용
- [게임 시작] 클릭 시 Smooth Zoom-in 연출 유지 및 **100% Full Screen** 터미널 전환
- 회사 인트라넷 형태의 첫 터미널 화면 및 아이디(`woojoo.kim`), 비밀번호 마스킹(`**********`)이 입력된 읽기 전용 로그인 폼 UX + [출근] 버튼 UI
- 은연중 전달되는 캐릭터 프로필 ('김우주', 헤르메스호 승무원 및 관리 AI ECHO 담당자)
- [출근] 클릭 후 2분할 화면 진입 (좌: 업무 데스크탑 UI, 우: ECHO 대화창)
- 라포 형성 Phase: 플레이어 미션 수행 기반 5대 일상 업무 미션 (1. 자원 채굴 현황 보고서, 2. 전력/산소 현황 보고서, 3. 동료 메시지 답장 & 반응 수신, 4. 지원자 이력서 검토, 5. ECHO 시스템 업데이트 기안 승인) 및 우측 ECHO 보조자 상호작용(지구 보고서 알림, 아침 인사, 브리핑, 스몰토크)
- **라포 형성 Phase 동안 비상 HUD(산소/전력) 및 60분 제한시간 타이머 미노출 / 미작동**
- 업무 미션 중 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인] 클릭 트리거 (유일/우선적 전환 조건)
- [업데이트 승인] 클릭 시 ECHO 대화창 리부팅 (CSS/SVG 기반 visual glitch, 애니메이션, 사운드) 및 ECHO의 위협 요소 오판 / 비상 봉쇄 발령 연출
- **비상 봉쇄 발령 완료 시점에 비상 HUD(산소 100% / 전력 100%) 표시 및 60분 타이머 작동 시작**
- 비상 봉쇄 발령 후 본 퍼즐 진입
- 카테고리 A Bio-hazard Act 1~3 플레이 흐름
- Act 3 정답 증거: `ai_priority_matrix.json` + `deleted_override.txt`
- Hermes OS 파일 탐색기, 파일 뷰어, 증거 첨부, ECHO 대화창 제출
- `Log_Fixer.exe` 또는 대체 복구 액션
- deterministic local ECHO 판정 및 Act 전환
- Normal Ending A
- placeholder visual/audio asset
- 실제 60분 세션 및 debug mode 15분 세션/컷신 스킵

## Proposed Out Of Scope

- 3D 컷신 및 3D 1인칭 손 리깅 컷신 (CSS/SVG 2D 컷신 연출로 대체)
- 90% 화면 비율의 모니터 테두리 레터박스 연출 (100% Full Screen으로 채움)
- 라포 형성 Phase 시간 경과에 의한 자동 봉쇄 전환 (업데이트 승인 클릭으로만 전환)
- 라포 형성 Phase 동안의 비상 HUD/타이머 노출 및 산소/전력 차감
- 라포 형성 Phase 외의 복잡한 오픈월드/샌드박스 업무 시스템 (정해진 5대 일상 업무 미션 중심)
- 10개 카테고리 procedural 생성 및 난이도별 seed 공유
- Ending B/C 및 전 승무원 구출 루트
- 외부 AI/API 기반 ECHO 응답 및 판정 (Phase 2로 분리)

## Phase 2 Pending Decisions

- 외부 AI/API provider, model, API key env var 이름 (Q11)
- API 실패 시 fallback 정책 및 서버 경유 호출 여부

## MVP Acceptance Criteria

- 사용자는 3D 메인 메뉴에서 [게임 시작] 클릭 시 Smooth Zoom-in 연출과 함께 **100% Full Screen** 터미널 화면으로 전환할 수 있다.
- 전환 후 사용자는 회사 인트라넷 화면에서 마스킹된 로그인 폼(`woojoo.kim` / `**********`)과 '김우주' 캐릭터 정보를 확인하고 [출근] 버튼을 클릭할 수 있다.
- [출근] 클릭 시 2분할 화면(좌: 업무 UI, 우: ECHO 대화창)으로 전환되며, 비상 HUD/타이머가 노출되지 않은 상태에서 5대 일상 업무 미션을 수행하고 ECHO 보조 상호작용을 진행할 수 있다.
- 사용자가 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]을 클릭하면 ECHO 대화창이 리부팅된다.
- 리부팅 완료 후 ECHO가 플레이어/선내 환경을 위협 요소로 오판하여 비상 봉쇄를 발령하며, 이 시점에 비상 HUD(산소/전력)가 표시되고 60분 타이머 작동이 시작된다.
- 비상 봉쇄 후 카테고리 A 본 퍼즐(파일 탐색, Act 1~3 증거 제출, deterministic ECHO 판정, Normal Ending A)로 정상 진입한다.
- Act 3 성공 시 통제실 문 해제 상태와 Normal Ending이 표시된다.


