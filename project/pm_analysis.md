# PM Analysis

## Document Meta

- version: 2.0
- pm agent: codex
- date: 2026-08-10
- status: updated - 4가지 UI/UX 및 입력 제출 개선 요구사항 (feat-042) 반영 완료 (1. ECHO 입력창 186일 미보정 안내 문구 전면 삭제, 2. ECHO 입력창 Enter 키 제출 연동, 3. SCENE LOCK 팝업 전면 삭제, 4. Power Surge 팝업 지속시간 4초 상향)
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

플레이어는 3D 메인 메뉴에서 메타/개발용 카피(`CONTROL ROOM STANDBY`, `1인칭 통제실...`, `클릭 후 봉쇄 컷신...`)가 전면 삭제된 시작 화면을 확인하고 100% Full Screen 터미널 화면으로 전환된 후, 몰입을 방해하는 메타/개발용 텍스트(`🔒 READ-ONLY` 마크, "시스템 자동 인증이 완료되었습니다...", [출근] 하단 "Clock-in :: 2분할 업무 화면 진입" 등)가 완전 제거된 Diegetic 회사 인트라넷 화면에서 로그인 폼(`woojoo.kim`, `**********`)을 확인하고 [출근]한다. 

이후 헤르메스 Workstation 화면에서 개발용 용어("2분할 업무 화면", "라포 Phase" 등)와 보조 메타 문구("(다음 업무로 이동)" 괄호 텍스트 등)가 완전 제거되고 단순 `✓ [확인 완료]`로 버튼 텍스트가 통일 고정된 상태에서, 자연스러운 Diegetic 대사를 바탕으로 진행한다. ECHO가 우측 대화창에서 업무를 브리핑하고 좌측 하단 `✓ [확인 완료]` 버튼 클릭에 따라 업무 문서를 순차적으로 진행한다. 보고서 읽기 중 ECHO의 실시간 반응 대사(최대 2개), [확인 완료] 버튼 클릭 시 ECHO의 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 대사 안내 및 화면 전환, 업무 중 무작위 발생하는 동료 메신저 알림 팝업(좌측 업무 화면 경계 내 우상단)/앱 UI(좌측 업무 화면 내 드래그 자유 이동 Draggable UI) 및 축소 알림 버블(답장 전 축소 시 숫자 `1`, 답장 완료 후 축소 시 미노출; 리부팅 진행 동안 `rebootState !== 'idle'` 아이콘 완전 숨김), 점심 메뉴 질문(`"우주씨, 오늘 점심 뭐 드실래요?"`), 자유 텍스트 답장 후 동료 긍정 반응(`"그 메뉴 좋다!"`) 1회 수신(입력창 placeholder 내 `(자유 텍스트)` 보조 라벨 전면 삭제 ➔ `답장을 입력하세요...` 표기, 한글 IME 조합 및 전송 후 잔류/재입력 버그 원인 차단 및 완전 초기화 보장), 지원자 이력서 3명 후보 서사적 적격/부적격 판정(안내 배너 및 `서사적 판정 선택:` 라벨 전면 삭제, 텍스트 변경 없이 단순 `✓ [확인 완료]` 표기 고정 & 미선택 시 그레이 비활성화 `disabled={isResumeIncomplete}`로 필수 평가 유도, 퍼즐/엔딩 영향 없음 & 이력서 검토 단계 ECHO 대화/Q&A 전면 비활성화)을 거친다.

이후 메타 경고 문구("⚠️ [ECHO 시스템 업데이트 승인]...") 및 하단 문구가 전면 삭제된 "ECHO 시스템 업데이트 필요" 기안 승인으로 본 퍼즐(ECHO 패치 승인 클릭 후 rebooting 상태 2초 축소, lockdown 상태 2초 연장된 9초 컷신 연출, 비상 HUD & 60분 타이머 가동)로 진입한다. 본 퍼즐 진입 후 메인 터미널 UI 및 콘텐츠는 18가지 상세 정제 사양과 함께 다음 7가지 핵심 피드백 정제/버그 수정 사양, 비상 컷신 전후 터미널 UI 통일 사양, 5가지 UI/UX 개선 상세 사양, 4가지 로그 파일 텍스트 정제 사양 및 4가지 세부 개선 사양이 엄격히 준수된다:
1) 초기 ECHO 대사 전면 삭제 ("김우주 담당자님, 출근이 확인되었습니다..." 삭제)
2) 로그 파일 뷰어 헤더 컴팩트화 (h2, 경로, 분류 박스 폰트/여백 최소화하여 본문 `<pre>`가 영역 대부분을 차지하도록 레이아웃 조절)
3) CHECKPOINT HINT 삭제 ("첨부한 파일 조합이 현재 Act와 맞지 않습니다..." 힌트 문구 및 관련 안내 블록 전면 삭제)
4) 제출 전송 후 입력창/첨부 초기화 (메시지 전송 시 성공/실패 무관 `messageInput = ""`, `attachedFileIds = []` 즉시 초기화)
5) Log_Fixer 사용 후 자동 첨부 방지 (복구 완료 시 `selectFile`만 수행하고 자동 첨부 방지, 수동 [ECHO에 증거 첨부] 클릭 필요)
6) 휴지통(`/Recycle_Bin/`) 파일 Log_Fixer 복구 지원 (휴지통 내 손상/삭제 파일 선택 시 `[LOG_FIXER로 데이터 복구]` 버튼 활성화 & `recoveredFileIds` 복구 가능)
7. Act 2 클리어 후 Act 3 전이 및 엔딩 조기 발동 버그 수정 (Act 2 성공 시 엄격하게 Act 3로만 전이, Act 3 조합 증거 검증 완료 전 `door_unlocked` 또는 `ending-ready` 상태 전이 차단)
8) `quarantine_rules.conf` 파일 내용 내 오프셋 개발자 해설풍 주석(`<-- 치명적 오차: 약 2년 앞으로 밀림`) 전면 삭제 및 단순 `시간 오프셋 값: +17,520시간` 표기 고정
9) ECHO 대화창 내 SYSTEM 스피커 메시지 전면 제거 (오직 ECHO 대사 및 플레이어 제출 항목만 노출)
10) 메인 메뉴 시작 화면 메타 카피 전면 삭제 (`CONTROL ROOM STANDBY` 카 라벨, `1인칭 통제실 / 컴퓨터는 물리적 오브젝트입니다`, `클릭 후 봉쇄 컷신을 거쳐 모니터 내부 Hermes OS로 진입합니다` 전면 삭제)
11) 동료 메신저 입력창 placeholder 내 `(자유 텍스트)` 보조 라벨 전면 삭제 (`답장을 입력하세요...`)
12) 동료 메신저 한글 IME 조합/전송 시 마지막 단어 자동 잔류/재입력 버그 원인 차단 및 입력창 초기화 보장
13) ECHO 패치 기안문 하단 `본 비상 봉쇄 시퀀스로 진입합니다` 문구 삭제 상태 유지
14) 파일 탐색기 & 뷰어 비율 조절: FILE EXPLORER 영역 너비를 축소(약 180~200px 고정)하고 FILE VIEWER 영역 너비를 대폭 확장하여 로그 문서 가독성 극대화 (또는 탐색기 패널 360px 가독성 확보)
15) 버튼 텍스트 한국어 전면 전환: `ATTACH TO ECHO` ➔ `ECHO에 증거 첨부`, `COPY PATH`/`PATH COPIED` ➔ `경로 복사`/`경로 복사 완료`, `OPEN WITH LOG_FIXER` ➔ `LOG_FIXER로 데이터 복구`, `UNLOCK`/`OPEN` ➔ `해제`/`열기`, `CANCEL` ➔ `취소`, `SUBMIT` ➔ `증거 제출`, `START INVESTIGATION` ➔ `조사 시작`
16) 잠긴 파일 힌트 텍스트 전면 삭제: 잠긴 파일 열람/암호 폼의 `승무원 메일에서 발견된 직인 암호를 입력하십시오.` 및 영문 힌트 문구 전면 삭제
17) 비상 HUD 크기 확충 및 중앙 배치: `O₂ LEVEL`, `POWER GRID`, `REMAINING TIME` 비상 HUD 카드의 시각적 크기를 키우고 고대비 라벨과 함께 상단 헤더 중앙(Center Alignment)에 균형 배치
18) `ACT-1 ACTIVE` 라벨 삭제 & 비상 HUD 위치 적용: 좌측 패널 헤더의 `ACT-1 ACTIVE` (또는 `STEP 1 / 5`) 라벨을 전면 삭제하고 해당 중앙 공간에 비상 HUD를 매끄럽게 연동
19) 파일 뷰어 내 `<dt>증거성</dt>`, `<dt>상태</dt>` DL 항목 삭제
20) 우측 대화창/태스크 헤더의 `Act-1 Mission` 라벨 삭제
21) 대화창/작성기 헤더의 `Evidence 0/1` 트레이 삭제
22) Tool manual 보안 메모 삭제
23) 좌측 사이드바 `Log fixer mini program` 카드/폼 삭제 (파일 뷰어의 `[LOG_FIXER로 데이터 복구]` 버튼은 파일 복구 단일 진입점으로 유지)
24) 손상/삭제된 파일 내용 확인은 파일 복구(Log_Fixer) 이후에만 가능하도록 변경 (복구 전 내용 은폐)
25) `NEXT ACTION` 띠/바 전면 삭제 및 `HOW TO PLAY` 첫 목표/Open first file 버튼 삭제
26) Log Fixer 완료 시 `Available for act-2 evidence` 등 개발자풍 메타 문구 전면 삭제
27) 상단 타이머 HUD의 `NORMAL SESSION`, `Act-1` 라벨 문구 삭제
28) `power_grid_maint.note` 내용 디제틱 한국어 재작성 및 휴지통(`/Recycle_Bin/`) 파일 복구 전 첨부 불가 처리
29) Sensor diagram 개발자 프롬프트 잔재 삭제 및 디제틱 도면 교체
30) 파일 뷰어 `DIAGNOSTIC NOTE` 버튼 삭제 및 `O₂ LEVEL` HUD `drain x1.0x` 문구 삭제
31) `sensor_diagram.png` (sensor_diagram.txt) 본문 하단 열 감지 헤드 문구 전면 삭제
32) `crew_comms_buffer.log` 본문 대화 화자 표기를 알파벳 (A, B, C)에서 디제틱 승무원 이름(`박진수 (엔지니어)`, `이민아 (통신관)`, `최성현 (보안관)`)으로 전면 변경
33) `email_chain_july.txt` 본문 하단 김 박사 이전 답장 문구 전면 삭제
34) `tool_manual.txt` 드래그 앤 드롭 안내 텍스트를 실제 게임플레이 방식인 `텍스트 파일 열람 시 #404_CORRUPTED 표시가 뜨면 파일 뷰어 상단의 [LOG_FIXER로 데이터 복구] 버튼을 클릭하세요.`로 변경
35) 메신저 점심 대사를 기존 `"오늘 점심 메뉴 뭐먹을래?"`에서 존댓말 정제 카피인 `"우주씨, 오늘 점심 뭐 드실래요?"`로 변경
36) 오답 제출 시 나타나는 Power Surge 팝업 지속시간을 2초(2000ms)로 연장하고, 타이틀과 메시지("전력 서지 경고", "ECHO 경고: 잘못된 절차 주장은 헤르메스 전력 라인을 불안정하게 만듭니다.")를 한국어로 전환
37) 메인 탐색 터미널 상단 HUD 영역에 일시정지(`⏸️`) 버튼 추가
38) 일시정지(⏸️) 클릭 시 O₂ 감소 및 남은 시간 카운트다운 멈춤(Game Clock Freeze), 인게임 전체 화면 8px 블록 블러(`backdrop-filter: blur(8px)`) 처리, 화면 중앙 큼직한 `[PAUSED]` 텍스트 및 그 아래 약간 작은 사이즈의 `[RESUME]` 버튼 배치, RESUME 클릭 시 블러 해제 및 게임 재개
39) ECHO 입력창 영역의 '186일 미보정' 안내 문구(`오른쪽 ECHO 입력창에 '186일 미보정'과 '센서 보정 오차'를 짧게 적고 증거 제출을 하세요.`) 전면 삭제
40) ECHO 입력창(textarea) Enter 키(Shift+Enter 제외) 입력 시 [증거 제출] 즉시 발동 키 핸들러 연동
41) 증거 제출 및 씬 전환 과정의 [SCENE LOCK] 안내 피드백 팝업 전면 삭제 (블랙아웃 시에만 고유 안내 카드 노출)
42) 오답 제출 시 표시되는 Power Surge 경고 팝업 지속시간 4초(4000ms)로 상향.

또한 비상 컷신 이후 진입하는 메인 퍼즐 터미널 UI(`App.tsx`: `terminal-frame`)는 비상 컷신 이전 워크스테이션 UI(`WorkInterface.tsx`: `work-split-container`, `work-header`, `work-split-body`, `work-left-panel`, `work-right-panel`)와 레이아웃, 헤더 스타일, 색상 테마 및 1.6fr : 1fr 2분할 바디 구조가 100% 동일하게 통일된다. 헤더 좌측에는 `HERMES WORKSTATION` 뱃지와 `HERMES SHIP SYSTEM COMMAND` 타이틀이, 중앙 공간에는 상단 헤더 중앙에 균형 배치된 확장 비상 HUD (`[O₂ Level]`, `[Power Grid]`, `[REMAINING TIME]`)가, 우측에는 `근무자: 김우주 (AI 관리 담당자)` 및 `● EMERGENCY LOCKDOWN ACTIVE` 비상 표시가 배치된다. 2분할 패널 바디는 좌측(`work-left-panel`) 파일 탐색기(약 180~200px 고정 너비) & 파일 뷰어(대폭 확장 너비) 통합 뷰포트, 우측(`work-right-panel` / `echo-chat-panel`) ECHO 대화 & 증거 제출 컴포저 통합 렌더링으로 연결되어 컷신 전후 화면 프레임, 패널 헤더 스타일, 스크롤바, 테두리 그라디언트, 폰트 크기가 100% 시각적으로 완벽하게 통일된다.

또한 `/System/Security` 제한 구역 클릭 시에는 힌트 문구 없이 한국어 암호 모달("보안 게이트 :: 제한 구역")이 호출되며, 전력 0% 차감으로 인한 블랙아웃 발생 시에는 화면 중앙 단일 강조 팝업(Center Modal)과 한국어 문구("⚠️ [전력 고갈] 주 전력 그리드 블랙아웃! OS 터미널 긴급 재부팅 중... (남은 시간: N초)")가 노출된다. ECHO 대화 및 동료 대화는 Cloudflare Worker NPC API(`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 연동하되, 3초 타임아웃 및 100% 로컬 Fallback 안전장치를 가동하여 오프라인/네트워크 단절 시에도 완전한 플레이를 보장한다.

## Core Loop

1. 3D 메인 메뉴에서 메타 카피(`CONTROL ROOM STANDBY` 카 라벨, 하단 메타 안내 문구 삭제)를 제거한 깔끔한 3D 환경에서 [게임 시작] 클릭 시 100% Full Screen Smooth Zoom-in 연출로 인게임 터미널 화면에 진입한다.
2. 전환 후 회사 인트라넷 화면에서 메타 문구가 제거된 자연스러운 로그인 폼(아이디: `woojoo.kim`, 비밀번호: `**********`)과 '김우주' 캐릭터 정보를 확인하고 [출근] 버튼을 클릭한다.
3. Hermes Workstation 화면(좌: 업무 화면, 우: ECHO 대화창)으로 진입하여 비상 HUD/타이머 미노출 상태로 ECHO 대화 브리핑 & `✓ [확인 완료]` 버튼 순차 업무 흐름(라포 Phase)을 진행한다:
   - 탭 메뉴가 제거된 좌측 화면에 ECHO가 우측 대화창을 통해 업무 문서를 순차적으로 출력한다.
   - **자원 채굴 보고서**: ECHO 브리핑 ➔ 좌측 출력 ➔ 보고서 검토 중 ECHO 실시간 반응(최대 2개) ➔ 좌측 하단 `✓ [확인 완료]` 버튼 클릭 ➔ ECHO 대사 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 출력 및 다음 업무 전환.
   - **전력/산소 보고서**: 좌측 출력 ➔ 자원 상태 데이터 확인 ➔ ECHO 실시간 반응(최대 2개) ➔ 좌측 하단 `✓ [확인 완료]` 버튼 클릭 ➔ 다음 업무 전환.
   - **동료 메신저 팝업 이벤트**: 전력/산소 보고서 또는 이력서 검토 중 무작위 발생 (좌측 업무 화면 경계 내 우상단 팝업 클릭 시 별도 메신저 앱 창 노출 & 좌측 업무 화면 내 드래그 자유 이동 Draggable UI, 축소/닫기 시 좌측 업무 화면 경계 내 우하단 말풍선 아이콘 + 신규 알림 버블(답장 전 축소 시 숫자 `1`, 답장 완료 후 축소 시 미노출; 리부팅 진행 동안 `rebootState !== 'idle'` 아이콘 완전 숨김), 점심 메뉴 정제 질문(`"우주씨, 오늘 점심 뭐 드실래요?"`), 자유 텍스트 답장(`(자유 텍스트)` placeholder 삭제 ➔ `답장을 입력하세요...`, 한글 IME 조합/전송 잔류 버그 원인 차단 및 초기화 보장), 동료 긍정 반응 1회 수신, 답장 입력창 하단 메타 문구 전면 제거 및 diegetic '읽지 않음(1)' 유지). 메신저 대화는 Cloudflare Worker NPC API (`npcId: 'coworker'`, 3초 타임아웃, 예외 시 100% 로컬 Fallback) 연동.
   - **지원자 이력서 검토**: 3명 후보 프로필 출력 ➔ 메타 안내 배너 및 `서사적 판정 선택:` 라벨 전면 삭제 ➔ 후보별 '적격'/'부적격' 판정 ➔ 버튼 텍스트 단순 `✓ [확인 완료]` 통일 고정 & 3명 중 미선택 이력서 존재 시 그레이 비활성화(`disabled={isResumeIncomplete}`)로 필수 평가 완수 유도 ➔ 퍼즐/엔딩 영향 없는 몰입용 서사적 선택 ➔ 우측 ECHO 대화창 및 Q&A 질의응답 입력 기능 비활성화 (ECHO 대화 불가능 처리) ➔ 3명 평가 완수 후 `✓ [확인 완료]` 클릭으로 업데이트 기안 전환.
   - **ECHO 업데이트 기안 승인**: 이력서 검토 후 제시되는 업데이트 승인 기안 (4번 미션 문서 내 메타/개발자 경고 문구 및 하단 문구 전면 삭제).
4. 업무 미션 중 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]을 클릭하면 ECHO 대화창이 리부팅(CSS/SVG visual glitch, 에러 경고, 사이렌, 데콤프레션, rebooting -2초/lockdown +2초 조절된 9초 컷신 연출)되며, 리부팅 중 우하단 동료 메신저 버블은 완전히 숨김 처리된다.
5. 리부팅 연출 완료 후 ECHO가 플레이어 및 선내 환경을 위협 요소로 오판하고 비상 봉쇄를 발령하며, 상단 헤더 중앙에 시각적으로 확충 배치된 비상 HUD(산소/전력) 표시 및 60분 카운트다운 타이머가 가동된다 (본 퍼즐 진입).
6. 비상 봉쇄 후 플레이어는 Hermes OS 파일 탐색기(약 180~200px 고정 너비)와 파일 뷰어(대폭 확장 너비)에서 한국어로 표기된 버튼(`ECHO에 증거 첨부`, `경로 복사`, `LOG_FIXER로 데이터 복구`, `해제`/`열기`, `취소`, `증거 제출`, `조사 시작`)을 활용하여 로그, 설정, 복구 대상 파일을 탐색하고 산소/전력을 관리한다 (`quarantine_rules.conf` 오프셋 해설 주석 삭제 (+17,520시간 표기), ECHO 대화창 SYSTEM 메시지 제거, 잠긴 파일 힌트 텍스트 전면 삭제, `ACT-1 ACTIVE` 라벨 삭제 및 비상 HUD 위치 연동, 복구 전 손상/삭제 파일 내용 은폐).
7. ECHO 대화창에서 186일 미보정 안내 문구가 삭제된 입력창에 증거 파일과 텍스트 주장을 입력 후 `[증거 제출]` 버튼 클릭 또는 textarea Enter 키(Shift+Enter 제외) 입력을 통해 Act 1, Act 2, Act 3 순서로 제출한다. (제출 처리 중 SCENE LOCK 팝업 미노출, ECHO 연동: `npcId: 'echo'`, Cloudflare Worker NPC API 3초 타임아웃 및 예외 발생 시 100% 로컬 Fallback 적용, SYSTEM 메시지 제외; 오답 제출 시 Power Surge 4초 지속)
8. Act 3까지 성공하면 통제실 문이 열리고 Normal Ending A로 탈출한다.

## Scope Conflicts & Change-001 Adjustments

### MVP category scope

Resolved: MVP에서는 카테고리 A 단일 시나리오만 먼저 구현한다. 나머지 시나리오는 MVP 이후 확장 후보로 둔다.

### Visual implementation scope (Updated by Change-001 & Q19, Q26, Q31, Q51, Q55, Q56~Q60, Q65)

Resolved: 메인 메뉴 화면의 배경 우주선/컴퓨터는 R3F 기반 3D 모델을 유지하되, 시작 화면 카드 라벨(`CONTROL ROOM STANDBY`) 및 하단 안내 문구 칸을 전면 삭제한다. 3D 컷신 기획은 **CSS / SVG 기반 2D 인게임 연출**로 변경한다. 메인 메뉴에서 터미널 진입 연출은 Smooth Zoom-in을 유지하되 화면 모니터 비율을 기존 90%가 아닌 **100% Full Screen**으로 채운다. `ECHO 패치 승인` 클릭 후 발동되는 rebooting/lockdown 컷신 연출 타임라인은 rebooting 상태를 2초 줄이고 lockdown 상태를 2초 연장한다. 리부팅 진행 동안(`rebootState !== 'idle'`) 우하단 동료 메신저 말풍선 버블 아이콘은 화면에서 완전히 숨김(미노출) 처리한다. 비상 컷신 이후 나오는 메인 퍼즐 터미널 UI(`App.tsx`: `terminal-frame`)는 컷신 이전 워크스테이션 UI(`WorkInterface.tsx`: `work-split-container`, `work-header`, `work-split-body`, `work-left-panel`, `work-right-panel`)와 레이아웃, 헤더, 색상 테마, 1.6fr 1fr 2분할 구조, 프레임, 스크롤바, 테두리 그라디언트, 폰트 크기가 100% 동일하게 통일 연결된다. 파일 탐색기 너비는 약 180~200px 고정으로 축소하고 파일 뷰어 너비를 대폭 확장하며, 주요 버튼 텍스트를 한국어로 전면 전환하고 잠긴 파일 힌트를 전면 삭제하며, 비상 HUD 시각적 크기를 확대하여 상단 헤더 중앙에 배치하고 `ACT-1 ACTIVE` 라벨을 삭제하여 매끄럽게 연동한다. SCENE LOCK 팝업은 전면 삭제되고 블랙아웃 시에만 고유 안내 카드가 노출된다.

### Narrative & Entry Flow (Updated by Change-001, Q16~Q65 User Feedback)

Resolved: 게임 진입 직후 비상 봉쇄 상태로 바로 들어가지 않고, **회사 인트라넷 (Diegetic 로그인 폼 `woojoo.kim`/`**********`, 메타 텍스트 전면 제거) -> [출근] -> Workstation (탭 제거, ECHO 업무 브리핑, 좌측 하단 단순 `✓ [확인 완료]` 버튼 업무 전환, 실시간 반응 대사, 동료 메신저 무작위 팝업(좌측 업무 화면 경계 내 우상단)/앱 UI(좌측 업무 화면 내 드래그 자유 이동 Draggable UI)/알림 버블(답장 전 `1`, 답장 완료 후 미노출; 리부팅 동안 완전 미노출; placeholder `(자유 텍스트)` 삭제 ➔ `답장을 입력하세요...`, IME 입력 전송 버그 수정), 이력서 안내 배너 및 '서사적 판정 선택:' 라벨 삭제, 버튼 표기 단순 `✓ [확인 완료]` 고정 & 미선택 이력서 존재 시 그레이 비활성화 필수 평가, 이력서 검토 중 ECHO 대화 비활성화) -> ECHO 시스템 업데이트 승인 (기안 내 메타 경고 문구 및 하단 문구 전면 삭제) -> ECHO 리부팅 (rebooting -2s/lockdown +2s 조절 컷신 연출 & 메신저 버블 숨김) -> 비상 봉쇄 & 확장 비상 HUD 중앙 배치/60분 타이머 가동 -> 통일된 뷰포트의 본 퍼즐 진입 (탐색기 180~200px/뷰어 대폭 확장, 버튼 한국어 전환, 잠긴 파일 힌트 삭제, `ACT-1 ACTIVE` 라벨 삭제 및 비상 HUD 위치 연동)** 순서로 전개한다.

### Act 3 evidence scope

Resolved: 카테고리 A MVP의 Act 3 정답 증거는 원문 기획서 기준인 `ai_priority_matrix.json` + `deleted_override.txt`로 확정한다.

### AI External NPC API Integration (Updated for feat-007)

Resolved: Cloudflare Worker 기반 Hermes NPC API 명세(`https://royal-firefly-60c3.jwpark971219.workers.dev`, `npcId: echo | coworker`, TypeScript 타입 `src/types/npc.ts`)를 연동한다. 3초 타임아웃(`AbortController`)과 예외/단절 발생 시 100% 로컬 Fallback 안전장치를 가동하여 오프라인/장애 시에도 끊김 없이 동작한다.

## PM Readiness

- 기획 방향성 분석: ready (Change-001 및 Q21~Q65 사용자 피드백, 5가지 추가 UI/UX 개선 사양, Cloudflare Worker NPC API 명세, 4가지 로그 파일 텍스트 정제 사양, 4가지 세부 개선 요구사항, 4가지 UI/UX 및 입력 제출 개선 요구사항 반영 완료)
- MVP 범위 확정: ready for Cloudflare Worker NPC API integrated MVP with Diegetic/ECHO-driven flow, 5 UI/UX refinements, 4 log file text refinements, 4 detail refinements, 4 UI/UX & input submission refinements (ECHO 186-day guide copy deletion, ECHO textarea Enter key submission handler, SCENE LOCK popup deletion, Power Surge 4s popup), and 100% local fallback
- 전체 task 확정: `feat-001`~`feat-042` (완료 - 4가지 UI/UX 및 입력 제출 개선 사양 feat-042 반영 완료)
- Active Task: `feat-042` (done)
- 미확정 항목: 없음 (Q1~Q65 전 항목 답변/명세 수립 완료)

## Recommended PM Decision

Cloudflare Worker NPC API 연동과 함께 3초 타임아웃 및 100% 로컬 Fallback 안전장치를 적용하는 `feat-007`을 완료하고, 비상 컷신 전후 터미널 UI 레이아웃/헤더/2분할 구조 100% 통일 사양(`feat-035`), 5가지 추가 UI/UX 개선 사양(`feat-036`), 4가지 세부 개선 사양(`feat-041`), 4가지 UI/UX 및 입력 제출 개선 사양(`feat-042`)을 포함한 상세 운영 명세를 운영 문서 전반에 적용하여 개발 및 QA 검증 표준으로 확정한다.
