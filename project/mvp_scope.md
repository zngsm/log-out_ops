# MVP Scope

## Document Meta

- version: 1.2
- pm agent: codex
- date: 2026-08-10
- status: confirmed - 사용자의 18가지 상세 게임플레이/UI/내용 정제 요청 사양 전면 반영 (1. 컷신 타임라인 rebooting -2s / lockdown +2s, 2. 메인 터미널 UI 정제 17종: 파일 뷰어 <dt>증거성</dt>/<dt>상태</dt> 삭제, Act-1 Mission 삭제, Evidence 0/1 삭제, Tool manual 보안 메모 삭제, 사이드바 Log fixer mini program 삭제 & 파일 뷰어 버튼 유지, 잠긴 파일/오입력 힌트 삭제, 손상/삭제 파일 복구 전 내용 은폐, NEXT ACTION 삭제, HOW TO PLAY 첫 목표/Open first file 삭제, Log Fixer 완료 메타 문구 삭제, 타이머 HUD NORMAL SESSION/Act-1 삭제, power_grid_maint.note 디제틱 한국어 재작성, Recycle_Bin 파일 복구 전 첨부 불가, Sensor diagram 프롬프트 삭제 및 명시 라벨 교체, DIAGNOSTIC NOTE 삭제, O₂ LEVEL drain x1.0x 삭제)

## MVP Goal

플레이어가 3D 메인 메뉴에서 100% Full Screen 터미널로 진입하여, 메타 텍스트가 전면 제거된 Diegetic 회사 인트라넷에서 로그인 폼(`woojoo.kim`, `**********`)을 확인하고 [출근] 후, ECHO 대화 브리핑 및 좌측 문서 하단 단순 `✓ [확인 완료]` 고정 버튼 전환에 따른 순차 업무 흐름(자원 채굴 보고서, 전력/산소 보고서, 동료 메신저 팝업(좌측 업무 화면 경계 내 우상단)/앱 UI(좌측 업무 화면 내 드래그 자유 이동 Draggable UI) 및 축소 알림 버블(답장 전 `1`, 답장 완료 후 미노출; 리부팅 중 완전 미노출), 지원자 이력서 검토 서사 판정(메타 배너/라벨 전면 삭제, 텍스트 변경 없이 단순 `✓ [확인 완료]` 표기 고정 & 미선택 시 그레이 비활성화 `disabled={isResumeIncomplete}` 필수 평가 유도, ECHO 대화 비활성화), 메타 경고 문구가 전면 삭제된 ECHO 시스템 업데이트 기안 승인)을 진행한다. 이후 [업데이트 승인]에 의한 기습 리부팅 (rebooting 상태 2초 축소 / lockdown 연장 조절 컷신 연출 & 리부팅 중 동료 메신저 버블 완전 숨김) 및 오판 비상 봉쇄(상단 title-bar `ECHO STATE / monitoring` 카드 및 `ACT-1 100%` 블록 전면 제거, 비상 HUD & 60분 타이머 가동)가 발생하면, Hermes OS에서 17가지 상세 정제 사양(파일 뷰어 `<dt>증거성</dt>`/`<dt>상태</dt>` 삭제, `Act-1 Mission` 삭제, `Evidence 0/1` 삭제, Tool manual 보안 메모 삭제, 사이드바 Log fixer mini program 삭제 & 파일 뷰어 버튼 유지, 잠긴 파일/오입력 힌트 삭제, 손상/삭제 파일 복구 전 내용 은폐, `NEXT ACTION` 삭제, `HOW TO PLAY` 첫 목표/Open first file 삭제, Log Fixer 완료 메타 문구 삭제, 타이머 HUD `NORMAL SESSION`/`Act-1` 삭제, `power_grid_maint.note` 디제틱 한국어 재작성, 휴지통 복구 전 첨부 불가, Sensor diagram 프롬프트 삭제 및 명시 라벨 교체, `DIAGNOSTIC NOTE` 삭제, `O₂ LEVEL` `drain x1.0x` 삭제), Security Gate 한국어 암호 모달, 블랙아웃 화면 중앙 단일 강조 팝업(Center Modal)을 확인하며 Act 1~3을 통과하고 통제실 문을 열어 탈출하는 최소 완성형 플레이 경험을 만든다. ECHO 및 동료 대화는 Cloudflare Worker NPC API(`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 연동하되, 3초 타임아웃 및 100% 로컬 Fallback 안전장치로 오프라인/장애 시에도 끊김 없는 플레이를 보장한다.

## Proposed In Scope

- Vite + React + TypeScript 웹 게임
- R3F 기반 우주선/컴퓨터 3D 메인 메뉴 배경 (유지)
- 3D 컷신 대신 **CSS / SVG 기반 2D 컷신 연출** 적용
- [게임 시작] 클릭 시 Smooth Zoom-in 연출 유지 및 **100% Full Screen** 터미널 전환
- **Diegetic UI 회사 인트라넷 화면**: `🔒 READ-ONLY` 마크, "시스템 자동 인증이 완료되었습니다...", [출근] 하단 "Clock-in :: 2분할 업무 화면 진입" 등 통제용/기획용 메타 텍스트가 완전 제거된 자연스러운 로그인 폼 UX (`woojoo.kim` / `**********`) + 단순 `[출근]` 버튼 (메타 카피 완전 제외)
- 은연중 전달되는 캐릭터 프로필 ('김우주', 헤르메스호 승무원 및 관리 AI ECHO 담당자)
- **Diegetic Workstation UI**: 헤더의 "HERMES 2-SPLIT DUAL PANEL WORK INTERFACE" 및 "라포 Phase" 등 개발용 용어 노출 완전 금지
- **ECHO 대화 브리핑 및 좌측 `✓ [확인 완료]` 버튼 업무 전환 (탭 메뉴 제거)**:
  - 좌측 탭 메뉴를 제거하고, 우측 대화창에서 ECHO가 업무를 브리핑
  - ECHO 첫 안내 대사 중 "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요" 등 개발자 지침풍 텍스트를 전면 제거하고 자연스러운 Diegetic 대사(예: "오늘 확인하셔야 할 서류들을 좌측 화면에 준비해 두었습니다. 검토해 보시고 말씀해 주세요.")로 변경
  - 좌측 보고서 하단 버튼의 보조 텍스트 없이 단순 `✓ [확인 완료]`로만 표기를 통일 고정
  - 버튼 클릭 시 ECHO 대사 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 출력과 함께 다음 업무 문서로 전환되는 방식
- **보고서 검토 중 ECHO 실시간 반응 대사**: 보고서 읽는 동안 보고서 내용 관련 반응 대사 최대 2개 출력 (예: 자원 채굴량 호조 시 긍정 반응)
- **동료 메신저 팝업 이벤트 / 별도 메신저 앱 UI (Draggable) / 축소 알림 버블 UX & 리부팅 시 버블 숨김**:
  - 전력/산소 보고서 또는 이력서 검토 단계 중 전체 뷰포트나 우측 ECHO 영역이 아닌 **좌측 업무 화면(Desktop Workspace Panel / Left Panel) 경계 내부의 오른쪽 상단(Top-Right)** 무작위 메신저 알림 팝업 발생 (알림 SFX 포함)
  - 팝업 클릭 시 별도의 메신저/채팅 앱 창 인터페이스가 열리며, **좌측 업무 화면 경계 영역 안에서 플레이어가 자유롭게 드래그하여 위치 이동(Draggable UI)**이 가능함
  - 팝업/채팅창 축소(닫기) 시: 답장 전 축소 시에는 **좌측 업무 화면 경계 내부의 오른쪽 하단(Bottom-Right)**에 말풍선 아이콘 + 빨간색 신규 알림 버블(숫자 `1`) 노출(아이콘 클릭 시 메신저 앱 창 재개), 답장 완료 후 축소 시에는 축소된 말풍선 아이콘에 신규 메시지 알림 버블(숫자 `1`) 미노출
  - **리부팅 동안 동료 메신저 버블 완전 숨김**: 리부팅 연출 진행 동안(`rebootState !== 'idle'`) 우하단 동료 메신저 말풍선 버블 아이콘을 화면에서 완전히 숨김(미노출) 처리
  - 동료 질문 카피: 항상 점심 메뉴를 묻는 질문 (예: `"오늘 점심 메뉴 뭐먹을래?"`)
  - 자유 텍스트 답장 및 동료 1회 긍정 반응 수신 (`"그 메뉴 좋다!"`), 답장 입력창 하단 몰입 방해 메타 문구 전면 제거 및 자연스러운 diegetic UX 유지 (추가 입력 시 `'읽지 않음(1)'` / `Unread` 상태 유지)
- **지원자 이력서 검토 기능 및 서사적 판정 (필수 평가 완수 & 버튼 고정 표기 & 그레이 비활성화)**:
  - 3명의 지원자 후보 프로필 제시, 후보별 '적격'/'부적격' 판정 선택 버튼 (퍼즐/엔딩 미영향 서사적 선택 요소)
  - **이력서 검토 단계 메타 안내 배너 전면 삭제**: `※ 안내: 본 이력서 적합성 판정은 서사적 몰입을 위한 인사 평가 선택 항목으로...` 배너 전면 삭제
  - **"서사적 판정 선택" 라벨 문구 전면 삭제**: 이력서 후보별 판정 버튼 앞의 `서사적 판정 선택:` 텍스트 전면 삭제
  - **단순 `✓ [확인 완료]` 버튼 표기 고정 & 그레이 비활성화 (필수 평가)**: 3명의 지원자 중 한 명이라도 판정이 미선택된 경우 버튼 텍스트 변경 없이 단순 `✓ [확인 완료]` 표기를 유지하고 그레이 비활성화 스타일(`disabled={isResumeIncomplete}`)을 적용하여 필수 평가 완수를 유도
  - **이력서 검토 단계 ECHO 대화 비활성화**: 우측 ECHO 대화창 및 Q&A 질의응답 입력 기능이 전면 제거되어 비활성화(ECHO 대화 불가능 처리)
- **ECHO 시스템 업데이트 기안 문서 내 메타 경고 문구 전면 삭제**: 4번 미션 문서 내 `"⚠️ [ECHO 시스템 업데이트 승인] 버튼 클릭 시 ECHO 패치가 적용되고 시스템 재부팅 후 본 비상 봉쇄 시퀀스로 진입합니다."` 메타/개발자 설명 문구 전면 삭제
- **상단 title-bar status HUD 중 `ECHO STATE / monitoring` 카드 및 `ACT-1 100%` (`mission-clock`) 블록 전면 제거**: 상단 status bar에서 `ECHO STATE / monitoring` 카드와 `ACT-1 100%` 블록을 전면 제거
- **메인 터미널 UI/UX 및 콘텐츠 상세 정제 17종 사양**:
  - (1) 파일 뷰어 내 `<dt>증거성</dt>`, `<dt>상태</dt>` DL 항목 전면 삭제
  - (2) 우측 대화창/태스크 헤더의 `Act-1 Mission` 라벨 전면 삭제
  - (3) 대화창/작성기 헤더의 `Evidence 0/1` 트레이 전면 삭제
  - (4) Tool manual 보안 메모 전면 삭제
  - (5) 좌측 사이드바 `Log fixer mini program` 카드/폼 삭제 (파일 뷰어의 `[OPEN WITH LOG_FIXER]` 버튼은 파일 복구 단일 진입점으로 유지)
  - (6) 잠긴 파일 비밀번호 위치 힌트 문구 전면 삭제
  - (7) 비밀번호 잘못 입력 시 위치 알려주는 힌트 문구 전면 삭제
  - (8) 손상/삭제된 파일 내용 확인은 파일 복구(Log_Fixer) 이후에만 가능하도록 변경 (복구 전 내용 은폐)
  - (9) `NEXT ACTION` 띠/바 전면 삭제
  - (10) `HOW TO PLAY` 창의 '첫 목표' 칸 및 'Open first file' 버튼 전면 삭제
  - (11) Log Fixer 완료 시 `Available for act-2 evidence` 등 개발자풍 메타 문구 전면 삭제
  - (12) 상단 타이머 HUD의 `NORMAL SESSION`, `Act-1` 라벨 문구 전면 삭제
  - (13) `power_grid_maint.note` 내용 자연스러운 디제틱 한국어 설명으로 전면 재작성
  - (14) 휴지통(`/Recycle_Bin/`) 파일은 복구 전 첨부 불가 처리 (복구 후 첨부 가능)
  - (15) Sensor diagram 개발자 프롬프트 잔재 삭제 및 명시된 라벨(`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점` 등) 디제틱 도면으로 교체
  - (16) 파일 뷰어의 `DIAGNOSTIC NOTE` 버튼 전면 삭제
  - (17) `O₂ LEVEL` HUD 카드 하단 `drain x1.0x` 문구 전면 삭제
- **Security Gate (암호 모달) 한국어 표기**:
  - `/System/Security` 제한 구역 클릭 시 암호 모달 영문 텍스트를 자연스러운 한국어 표기("보안 게이트 :: 제한 구역", "/System/Security 디렉터리는 김 박사의 비상 격리 프로토콜에 의해 잠겨 있습니다. 승무원 메일에서 발견된 직인 암호를 입력하십시오.")로 변경
- **Blackout 팝업 단일화 & 화면 중앙 배치 & 한국어 표기**:
  - 전력 0% 블랙아웃 발생 시 단 1개의 팝업만 노출 (Power Surge 팝업 중복 노출 차단)
  - 팝업 위치를 기존 우상단에서 **화면 중앙(Center Modal)**으로 변경하고 강조 스타일 적용
  - 한국어 경고 문구 표기 ("⚠️ [전력 고갈] 주 전력 그리드 블랙아웃! OS 터미널 긴급 재부팅 중... (남은 시간: N초)")
- **Cloudflare Worker 기반 Hermes NPC API 연동 및 100% 로컬 Fallback 안전장치 (`feat-007`)**:
  - `https://royal-firefly-60c3.jwpark971219.workers.dev` endpoint 연동
  - `npcId: 'echo'` (ECHO 대화 및 증거 제출 판정) / `npcId: 'coworker'` (동료 메신저 대화) 연동
  - TypeScript 타입 정의 (`src/types/npc.ts`: `NpcRequestPayload`, `EchoNpcResponse`, `CoworkerNpcResponse`, `ApiErrorResponse`)
  - API Client (`src/api/npcApiClient.ts`): `fetch` POST 요청, 3초 타임아웃 (`AbortController`)
  - 네트워크 단절, HTTP 에러, 타임아웃, 예외 발생 시 100% 로컬 Fallback 대사/응답 반환 기능으로 끊김 없는 플레이 보장
  - `WorkInterface.tsx` 동료 메신저 연동 (`npcId: 'coworker'`) & 로딩 타이핑 연출
  - `evidenceSubmission.ts` 및 `App.tsx` ECHO API 연동 (`npcId: 'echo'`, `currentStage`, `history` 전달 및 `next_stage`, `door_unlocked`, `ending_b_triggered` 수신 전이)
- **라포 형성 Phase 동안 비상 HUD(산소/전력) 및 60분 제한시간 타이머 미노출 / 미작동**
- 업무 미션 중 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인] 클릭 트리거 (유일/우선적 전환 조건)
- [업데이트 승인] 클릭 시 ECHO 대화창 리부팅 (CSS/SVG 기반 visual glitch, 에러 경고, 사이렌, 데콤프레션, **rebooting 연출 상태 2초 축소 / lockdown 연출 상태 2초 연장 조절 컷신 연출**, 리부팅 중 동료 메신저 버블 완전 숨김) 및 ECHO의 위협 요소 오판 / 비상 봉쇄 발령 연출
- **비상 봉쇄 발령 완료 시점에 비상 HUD(산소 100% / 전력 100%) 표시 및 60분 타이머 작동 시작**
- 비상 봉쇄 발령 후 본 퍼즐 진입
- 카테고리 A Bio-hazard Act 1~3 플레이 흐름
- Act 3 정답 증거: `ai_priority_matrix.json` + `deleted_override.txt`
- Hermes OS 파일 탐색기, 파일 뷰어, 증거 첨부, ECHO 대화창 제출
- `Log_Fixer.exe` 또는 대체 복구 액션
- deterministic local ECHO 판정 및 Act 전환 (API 예외 발생 시 Fallback 가동)
- Normal Ending A
- placeholder visual/audio asset
- 실제 60분 세션 및 debug mode 15분 세션/컷신 스킵

## Proposed Out Of Scope

- 인트라넷 로그인 폼, 출근 버튼, 업무 헤더, 보고서 버튼, 동료 채팅방 답장 입력창 하단의 개발용/기획용/시스템 메타 텍스트 (`🔒 READ-ONLY`, "시스템 자동 인증이 완료되었습니다...", "Clock-in :: 2분할 업무 화면 진입", "(다음 업무로 이동)", 개발자 지침풍 ECHO 대사, "HERMES 2-SPLIT DUAL PANEL", "라포 Phase", "※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다." 등)
- **파일 뷰어 내 `<dt>증거성</dt>`, `<dt>상태</dt>` DL 메타 항목**
- **우측 대화창/태스크 헤더의 `Act-1 Mission` 라벨**
- **대화창/작성기 헤더의 `Evidence 0/1` 트레이**
- **Tool manual 보안 메모 (`[보안 메모]` 등)**
- **좌측 사이드바 `Log fixer mini program` 카드/폼**
- **잠긴 파일 비밀번호 위치 힌트 문구 및 잘못 입력 시 비밀번호 위치 노출 힌트 문구**
- **파일 복구(Log_Fixer) 전 손상/삭제 파일 내용 확인/노출**
- **`NEXT ACTION` 띠/바**
- **`HOW TO PLAY` 창의 '첫 목표' 칸 및 'Open first file' 버튼**
- **Log Fixer 완료 시 `Available for act-2 evidence` 등 개발자풍 메타 문구**
- **상단 타이머 HUD의 `NORMAL SESSION`, `Act-1` 라벨 문구**
- **`power_grid_maint.note` 개발자풍/비디제틱 설명 텍스트**
- **휴지통(`/Recycle_Bin/`) 파일의 복구 전 ECHO 증거 첨부 기능**
- **Sensor diagram 내 개발자 프롬프트 잔재 텍스트**
- **파일 뷰어 내 `DIAGNOSTIC NOTE` 버튼**
- **`O₂ LEVEL` HUD 카드 하단 `drain x1.0x` 배율 문구**
- **이력서 검토 단계 메타 안내 배너** (`※ 안내: 본 이력서 적합성 판정은 서사적 몰입을 위한 인사 평가 선택 항목으로, 게임 퍼즐/엔딩에는 영향을 주지 않습니다.`)
- **이력서 후보별 판정 버튼 앞 "서사적 판정 선택:" 라벨 문구**
- **이력서 적격/부적격 미선택 지원자 존재 시 [확인 완료] 버튼 클릭 및 다음 업무 진입** (전면 비활성화 처리)
- **이력서 미선택 지원자 존재 시 버튼 텍스트 변경** (단순 `✓ [확인 완료]` 표기 고정 & 그레이 비활성화 처리)
- **4번 미션 문서 내 메타 경고 문구** (`"⚠️ [ECHO 시스템 업데이트 승인] 버튼 클릭 시 ECHO 패치가 적용되고 시스템 재부팅 후 본 비상 봉쇄 시퀀스로 진입합니다."`)
- **상단 title-bar status HUD 중 `ECHO STATE / monitoring` 카드 및 `ACT-1 100%` (`mission-clock`) 블록**
- **로그파일 뷰어 하단 `<dt>출처</dt>` source 항목 텍스트**
- **ECHO 리부팅 진행 동안(`rebootState !== 'idle'`)의 동료 메신저 말풍선 버블 아이콘 노출**
- **블랙아웃 발생 시 Power Surge 팝업 중복 노출 및 우상단 위치 팝업** (화면 중앙 단일 강조 팝업으로 대체)
- **지원자 이력서 검토 단계의 ECHO 대화창 및 Q&A 질의응답 입력 기능** (전면 비활성화 처리)
- 좌측 화면의 탭(Tab) 기반 자유 선택 메뉴
- ECHO 대화창 텍스트/키워드 인식 기반 업무 전환 (좌측 보고서 하단 단순 `✓ [확인 완료]` 버튼으로 처리)
- 지원자 이력서 '적격'/'부적격' 판정에 따른 게임 진행/퍼즐/엔딩 분기 (단순 몰입용 서사 요소)
- 프리셋 선택지 방식의 동료 메신저 답장 (자유 텍스트 직접 입력 방식 적용)
- 동료 메신저 무한 대화 (1회 긍정 반응 수신 후 추가 입력은 '읽지 않음(1)'으로 고정)
- 3D 컷신 및 3D 1인칭 손 리깅 컷신 (CSS/SVG 2D 컷신 연출로 대체)
- 90% 화면 비율의 모니터 테두리 레터박스 연출 (100% Full Screen으로 채움)
- 라포 형성 Phase 시간 경과에 의한 자동 봉쇄 전환 (업데이트 승인 클릭으로만 전환)
- 라포 형성 Phase 동안의 비상 HUD/타이머 노출 및 산소/전력 차감
- 10개 카테고리 procedural 생성 및 난이도별 seed 공유
- Ending B/C 및 전 승무원 구출 루트
- Fallback 안전장치가 없거나 클라이언트에 direct API key를 노출하는 미검증 외부 연동 방식 (Cloudflare Worker NPC API + 3초 타임아웃 + 100% 로컬 Fallback 연동으로 확정 적용)

## Phase 2 Pending Decisions

- NPC API specification: Cloudflare Worker Hermes NPC API (`https://royal-firefly-60c3.jwpark971219.workers.dev`, `npcId: echo | coworker`, TypeScript 타입 `src/types/npc.ts`, 3초 타임아웃 및 100% 로컬 Fallback 포함)로 확정되어 `feat-007` 완료.

## MVP Acceptance Criteria

- 사용자는 3D 메인 메뉴에서 [게임 시작] 클릭 시 Smooth Zoom-in 연출과 함께 **100% Full Screen** 터미널 화면으로 전환할 수 있다.
- 전환 후 사용자는 `🔒 READ-ONLY`, "시스템 자동 인증이 완료되었습니다...", "Clock-in :: 2분할 업무 화면 진입" 등 메타 텍스트가 전면 제거된 Diegetic 회사 인트라넷 화면에서 로그인 폼(`woojoo.kim` / `**********`)과 '김우주' 캐릭터 정보를 확인하고 단순 [출근] 버튼을 클릭할 수 있다.
- [출근] 클릭 시 탭 메뉴 및 개발용 용어가 제거된 Workstation 화면(좌: 업무 UI, 우: ECHO 대화창)으로 전환된다.
- ECHO가 우측 대화창에서 자연스러운 Diegetic 대사(개발자 지침풍 텍스트 전면 제거)로 업무를 브리핑하고 좌측 화면에 업무 문서(자원 채굴 보고서 ➔ 전력/산소 보고서 ➔ 이력서 검토 ➔ 업데이트 기안)를 제시하며, 보고서 읽기 중 ECHO의 실시간 반응 대사(최대 2개)가 출력된다.
- 플레이어가 좌측 보고서/문서 하단의 보조 텍스트("(다음 업무로 이동)")가 완전 제거된 단순 **`✓ [확인 완료]`** 버튼을 클릭하면, 우측 ECHO 대화창에 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 대사가 출력되고 좌측 업무 화면이 다음 업무 문서로 전환된다.
- 전력/산소 보고서 또는 이력서 검토 중 전체 뷰포트나 우측 ECHO 영역이 아닌 **좌측 업무 화면(Desktop Workspace Panel / Left Panel) 경계 내부의 오른쪽 상단(Top-Right)**에 무작위 동료 메신저 알림 SFX/팝업이 발생한다.
- 사용자가 팝업을 클릭하면 별도의 메신저 앱 창이 열리고(**좌측 업무 화면 경계 영역 안에서 자유롭게 드래그 위치 이동 가능**), 점심 메뉴 질문(`"오늘 점심 메뉴 뭐먹을래?"`)을 확인하며 자유 텍스트로 답장할 수 있다. 답장 입력창 하단의 몰입 방해 메타 문구(`"※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다."`)는 전면 제거되어 노출되지 않으며, 답장 후 동료가 긍정 반응 메시지(`"그 메뉴 좋다!"`)를 1회 보내오며, 이후 추가 입력 시 자연스러운 diegetic UX로 `'읽지 않음(1)'` 상태가 유지된다.
- 사용자가 메신저 팝업/채팅창을 축소(닫기)할 때, 답장 전 축소 시에는 **좌측 업무 화면(Desktop Workspace Panel / Left Panel) 경계 내부의 오른쪽 하단(Bottom-Right)**에 말풍선 채팅 앱 아이콘과 빨간색 신규 메시지 알림 버블(숫자 `1`)이 표시되며, 답장 완료 후 축소 시에는 축소된 말풍선 아이콘에 신규 메시지 알림 버블(숫자 `1`)이 더 이상 노출되지 않으며, **ECHO 리부팅 진행 동안(`rebootState !== 'idle'`) 말풍선 버블 아이콘이 화면에서 완전히 숨김(미노출)** 처리된다.
- Cloudflare Worker NPC API (`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 통해 ECHO (`npcId: 'echo'`) 및 동료 메신저 (`npcId: 'coworker'`)에 외부 AI 응답을 제공하며, 3초 타임아웃 미수신 또는 네트워크 단절/에러 발생 시 100% 로컬 Fallback 대사/응답으로 대체되어 게임이 중단 없이 정상 진행된다.
- 이력서 검토 단계에서 사용자는 `※ 안내: 본 이력서 적합성 판정은...` 메타 배너와 `서사적 판정 선택:` 라벨이 전면 삭제된 Diegetic 이력서 화면에서 3명의 지원자 프로필을 확인하고 적격/부적격 평가 버튼을 누를 수 있다.
- 이력서 검토 단계(`activeStep === 'resume'`)에서 3명의 지원자 중 한 명이라도 적격/부적격 판정이 미선택된 경우 버튼 텍스트 변경 없이 단순 **`✓ [확인 완료]`** 표기를 유지하고 그레이 비활성화 스타일(`disabled={isResumeIncomplete}`)이 적용되어 필수 평가 완수가 유도되며, 3명 전원 선택 시 `✓ [확인 완료]` 버튼이 활성화된다. 이력서 검토 단계 동안 우측 ECHO 대화창 및 Q&A 질의응답 입력 기능은 전면 비활성화되어 동작하지 않는다 (ECHO 대화 불가능 처리).
- "ECHO 시스템 업데이트 필요" 4번 미션 문서 내 `"⚠️ [ECHO 시스템 업데이트 승인] 버튼 클릭 시 ECHO 패치가 적용되고 시스템 재부팅 후 본 비상 봉쇄 시퀀스로 진입합니다."` 메타/개발자 설명 문구가 전면 삭제되어 노출되지 않는다.
- 상단 title-bar status HUD 중 `ECHO STATE / monitoring` 카드 및 `ACT-1 100%` (`mission-clock`) 블록이 전면 제거되어 노출되지 않는다.
- 메인 터미널 UI/UX는 17가지 상세 정제 사양이 완벽히 적용된다:
  1) 파일 뷰어 내 `<dt>증거성</dt>`, `<dt>상태</dt>` DL 항목 삭제
  2) 우측 대화창/태스크 헤더의 `Act-1 Mission` 라벨 삭제
  3) 대화창/작성기 헤더의 `Evidence 0/1` 트레이 삭제
  4) Tool manual 보안 메모 삭제
  5) 좌측 사이드바 `Log fixer mini program` 카드/폼 삭제 (파일 뷰어의 `[OPEN WITH LOG_FIXER]` 버튼 유지)
  6) 잠긴 파일 비밀번호 위치 힌트 문구 전면 삭제
  7) 비밀번호 잘못 입력 시 위치 알려주는 힌트 문구 전면 삭제
  8) 손상/삭제된 파일 내용 확인은 파일 복구(Log_Fixer) 이후에만 가능하도록 변경 (복구 전 내용 은폐)
  9) `NEXT ACTION` 띠/바 전면 삭제
  10) `HOW TO PLAY` 창의 '첫 목표' 칸 및 'Open first file' 버튼 삭제
  11) Log Fixer 완료 시 `Available for act-2 evidence` 등 개발자풍 메타 문구 전면 삭제
  12) 상단 타이머 HUD의 `NORMAL SESSION`, `Act-1` 라벨 문구 삭제
  13) `power_grid_maint.note` 내용 자연스러운 디제틱 한국어 설명으로 전면 재작성
  14) 휴지통(`/Recycle_Bin/`) 파일은 복구 전 첨부 불가 처리 (복구 후 첨부 가능)
  15) Sensor diagram 개발자 프롬프트 잔재 삭제 및 명시된 라벨(`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점` 등) 디제틱 도면으로 교체
  16) 파일 뷰어의 `DIAGNOSTIC NOTE` 버튼 삭제
  17) `O₂ LEVEL` HUD 카드 하단 `drain x1.0x` 문구 삭제.
- `/System/Security` 제한 구역 클릭 시 암호 모달이 자연스러운 한국어 표기("보안 게이트 :: 제한 구역", "/System/Security 디렉터리는 김 박사의 비상 격리 프로토콜에 의해 잠겨 있습니다. 승무원 메일에서 발견된 직인 암호를 입력하십시오.")로 노출된다.
- 전력 0% 블랙아웃 발생 시 단 1개의 화면 중앙 강조 팝업(Center Modal)이 한국어 경고 문구("⚠️ [전력 고갈] 주 전력 그리드 블랙아웃! OS 터미널 긴급 재부팅 중... (남은 시간: N초)")와 함께 노출되며 Power Surge 팝업 중복 노출이 차단된다.
- 라포 Phase 동안 비상 HUD 및 60분 타이머는 노출/작동하지 않는다.
- 사용자가 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]을 클릭하면 ECHO 대화창이 리부팅된다.
- `ECHO 패치 승인` 클릭 후 발동되는 CSS/SVG 글리치, 시스템 에러 경고, 비상 사이렌, 데콤프레션 및 통제실 Lockdown 선언 컷신 연출 타임라인 중 rebooting 연출 상태가 2초 축소되고 lockdown 연출 상태가 2초 연장되어 재생된 후 비상 봉쇄 상태로 진입한다.
- 리부팅 연출 완료 후 ECHO가 플레이어/선내 환경을 위협 요소로 오판하여 비상 봉쇄를 발령하며, 이 시점에 비상 HUD(산소/전력)가 표시되고 60분 타이머 작동이 시작된다.
- 비상 봉쇄 후 카테고리 A 본 퍼즐(파일 탐색, Act 1~3 증거 제출, deterministic ECHO 판정, Normal Ending A)로 정상 진입한다.
- Act 3 성공 시 통제실 문 해제 상태와 Normal Ending이 표시된다.



