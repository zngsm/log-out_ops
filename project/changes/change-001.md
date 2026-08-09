# Change-001: 2D 연출 전환, Full Screen 인트라넷 인트로 및 라포 형성 Phase 도입

## Document Meta

- version: 1.1
- author: PM Agent
- date: 2026-08-09
- status: confirmed - Q16~Q20 human answers incorporated
- target docs: `project/mvp_scope.md`, `project/pm_analysis.md`, `project/pm_questions.md`, `project/task_board.md`, `project/tasks/*.md`

## Background & Motivation

기존 기획의 3D 컷신 연출 및 직접적 비상 봉쇄 진입 흐름을 조정하여, CSS/SVG 기반 2D 연출과 함께 게임 시작 직후 플레이어가 AI 관리자로서 ECHO와 상호작용하는 라포 형성(Rapport Building) Phase를 도입한다.
이를 통해 캐릭터 정보('김우주')와 일상 업무 흐름을 은연중에 전달하고, ECHO 시스템 업데이트 승인에 따른 기습적 리부팅 및 오판 비상 봉쇄 연출로 본 퍼즐 진입의 서사적 몰입감을 극대화한다.

## Detailed Change Specifications

### 1. 3D 컷신 기획의 2D 전환 (CSS / SVG 기반, 메인 메뉴 3D 유지)
- 기존 3D 기반 연출/컷신을 **CSS / SVG 기반 인게임 연출**로 구현한다.
- 게임 시작 화면(메인 메뉴)의 R3F 3D 배경 우주선/통제실 모델링 연출은 기존대로 유지한다.

### 2. Full Screen 모니터 전환 연출 (100% 화면 전환)
- 메인 메뉴에서 [게임 시작] 버튼 클릭 시 인게임 터미널 화면으로 전환되는 Smooth Zoom-in 연출은 그대로 유지한다.
- 전환 후 모니터 출력 비율을 기존 90% (테두리/레터박스 노출)에서 **100% Full Screen**으로 채운다.

### 3. 회사 인트라넷 화면 및 로그인 폼 UX / [출근] 버튼 배치
- Zoom-in 전환 직후 노출되는 첫 화면을 헤르메스호 회사 인트라넷(Company Intranet) 형태의 화면으로 구성한다.
- **로그인 폼 UX**: 아이디와 비밀번호가 이미 채워져 있는 읽기 전용 폼(플레이어 조작/수정 불가)으로 구성한다.
  - 아이디: `woojoo.kim`
  - 비밀번호: 10자리 마스킹 처리 (`**********`)
- 인트라넷 화면을 통해 캐릭터 정보(이름: '김우주', 직책: '우주 자원 채굴선 헤르메스호 승무원 및 관리 AI ECHO 담당자')를 은연중에 전달한다.
- 로그인 폼 하단/주요 위치에 [출근] (Clock-in) 버튼을 배치한다.

### 4. 2분할 업무 화면 진입
- [출근] 버튼 클릭 시 2분할 화면(Split Layout)으로 전환된다.
  - **좌측**: 업무 화면 (데스크탑 UI - 보고서, 메시지, 이력서, 기안 문서 처리 등)
  - **우측**: ECHO 대화창 (AI 관리자 보조 UI)

### 5. 라포 형성 Phase (Rapport Building Phase)
- 본 퍼즐 진입 전에 플레이어가 AI 관리자로서 일상 업무를 처리하는 라포 형성 Phase를 진행한다 (진행 시간은 5분에 얽매이지 않고 업무 미션 수행에 맞춘 자율 진행).
- **라포 Phase 동안 비상 HUD(산소/전력) 및 60분 제한시간 타이머는 노출되지 않으며 차감 작동하지 않는다.**
- **좌측 업무 화면 (5대 업무 미션)**:
  1) **자원 채굴 현황 보고서 확인**: 추이 그래프, 통계 데이터 등 실제 보고서 UI로 구성
  2) **함선 전력/산소 현황 보고서 확인**: 함선 자원 상태 데이터 확인
  3) **동료 메시지 답장**: 일상적 소통 (예: "오늘 점심 메뉴 뭐먹을래?") ➔ 동료 반응 메시지 수신
  4) **김우주 동료 포지션 지원자 이력서 검토**: 신규 지원자 이력서 서류 확인
  5) **ECHO 시스템 업데이트 기안 승인**: 업데이트 승인 처리
- **우측 ECHO 대화창**: ECHO가 플레이어를 보조하는 역할을 수행한다 (지구 보고서 수신 알림, 아침 인사, 일상 스몰토크).

### 6. 본 퍼즐 진입 전환 계기 및 비상 HUD/타이머 가동
- 라포 형성 Phase의 업무 미션 중 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인] 클릭이 **유일/우선적인 전환 트리거**이다 (시간 경과에 의한 자동 전환 없음).
- 플레이어가 [업데이트 승인] 버튼을 클릭하면 ECHO 대화창 및 시스템이 리부팅(Reboot - Visual Glitch, 애니메이션, 사운드)된다.
- 리부팅 완료 직후 ECHO가 플레이어 및 선내 환경을 위협 요소(Bio-hazard 등)로 오판하며 비상 봉쇄를 발령한다.
- **비상 봉쇄 발령과 동시에 산소(100%)/전력(100%) 비상 HUD가 화면에 표시되고 60분 카운트다운 타이머가 작동을 시작한다.**
- 이후 기존 기획의 본 퍼즐(파일 탐색, 증거 제출, Act 1~3 반박)로 진입한다.

## Impact Analysis

- **`project/pm_analysis.md`**: Core Loop의 인트로 단계(인트라넷 로그인 폼 -> 출근 -> 라포 phase 5대 미션 -> ECHO 업데이트 승인 -> 리부팅 -> 비상 봉쇄 & HUD/타이머 가동 -> 본 퍼즐) 및 Visual Scope(CSS/SVG 2D 컷신, 100% Full Screen) 갱신.
- **`project/mvp_scope.md`**: MVP In Scope / Out of Scope 및 Acceptance Criteria에 로그인 폼(`woojoo.kim`, `**********`), 5대 업무 미션, [업데이트 승인] 전환 트리거, 비상 봉쇄 시점 HUD/타이머 가동 반영.
- **`project/pm_questions.md`**: Q16~Q20 질문에 대한 사용자 Answer 명확히 업데이트 완료.
- **`project/task_board.md`**: 신규 작업 `feat-031`~`feat-034` 상세 범위 및 의존성 업데이트.
- **`project/tasks/feat-031.md` ~ `feat-034.md`**: CSS/SVG 2D 연출, 로그인 폼 UI, 5대 업무 미션, [업데이트 승인] 리부팅 및 HUD/타이머 가동 시점을 각 task 상세 스펙에 최신화.

