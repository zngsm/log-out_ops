# MVP Scope

## Document Meta

- version: 0.8
- pm agent: codex
- date: 2026-08-09
- status: confirmed - Cloudflare Worker Hermes NPC API 연동 (`feat-007`), 3초 타임아웃/100% 로컬 Fallback 및 답장 완료 후 축소 시 메신저 알림 버블(`1`) 미노출 사양 반영

## MVP Goal

플레이어가 3D 메인 메뉴에서 100% Full Screen 터미널로 진입하여, 메타 텍스트가 전면 제거된 Diegetic 회사 인트라넷에서 로그인 폼(`woojoo.kim`, `**********`)을 확인하고 [출근] 후, ECHO 대화 브리핑 및 좌측 문서 하단 [확인 완료] 버튼 전환에 따른 순차 업무 흐름(자원 채굴 보고서, 전력/산소 보고서, 동료 메신저 팝업(좌측 업무 화면 경계 내 우상단)/앱 UI(좌측 업무 화면 내 드래그 자유 이동 Draggable UI) 및 축소 알림 버블(답장 전 `1`, 답장 완료 후 미노출; 좌측 업무 화면 경계 내 우하단), 지원자 이력서 검토 서사 판정 및 ECHO Q&A, ECHO 시스템 업데이트 기안 승인)을 진행한다. 이후 [업데이트 승인]에 의한 기습 리부팅 및 오판 비상 봉쇄(비상 HUD & 60분 타이머 가동)가 발생하면, Hermes OS에서 로그와 설정 파일을 조사해 Act 1~3을 통과하고 통제실 문을 열어 탈출하는 최소 완성형 플레이 경험을 만든다. ECHO 및 동료 대화는 Cloudflare Worker NPC API(`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 연동하되, 3초 타임아웃 및 100% 로컬 Fallback 안전장치로 오프라인/장애 시에도 끊김 없는 플레이를 보장한다.

## Proposed In Scope

- Vite + React + TypeScript 웹 게임
- R3F 기반 우주선/컴퓨터 3D 메인 메뉴 배경 (유지)
- 3D 컷신 대신 **CSS / SVG 기반 2D 컷신 연출** 적용
- [게임 시작] 클릭 시 Smooth Zoom-in 연출 유지 및 **100% Full Screen** 터미널 전환
- **Diegetic UI 회사 인트라넷 화면**: `🔒 READ-ONLY` 마크, "시스템 자동 인증이 완료되었습니다...", [출근] 하단 "Clock-in :: 2분할 업무 화면 진입" 등 통제용/기획용 메타 텍스트가 완전 제거된 자연스러운 로그인 폼 UX (`woojoo.kim` / `**********`) + 단순 `[출근]` 버튼 (메타 카피 완전 제외)
- 은연중 전달되는 캐릭터 프로필 ('김우주', 헤르메스호 승무원 및 관리 AI ECHO 담당자)
- **Diegetic Workstation UI**: 헤더의 "HERMES 2-SPLIT DUAL PANEL WORK INTERFACE" 및 "라포 Phase" 등 개발용 용어 노출 완전 금지
- **ECHO 대화 브리핑 및 좌측 [확인 완료] 버튼 업무 전환 (탭 메뉴 제거)**:
  - 좌측 탭 메뉴를 제거하고, 우측 대화창에서 ECHO가 업무를 브리핑
  - ECHO 첫 안내 대사 중 "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요" 등 개발자 지침풍 텍스트를 전면 제거하고 자연스러운 Diegetic 대사(예: "오늘 확인하셔야 할 서류들을 좌측 화면에 준비해 두었습니다. 검토해 보시고 말씀해 주세요.")로 변경
  - 좌측 보고서 하단 버튼의 "(다음 업무로 이동)" 괄호 보조 텍스트를 제거하여 단순 `[확인 완료]`로만 표기
  - 버튼 클릭 시 ECHO 대사 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 출력과 함께 다음 업무 문서로 전환되는 방식
- **보고서 검토 중 ECHO 실시간 반응 대사**: 보고서 읽는 동안 보고서 내용 관련 반응 대사 최대 2개 출력 (예: 자원 채굴량 호조 시 긍정 반응)
- **동료 메신저 팝업 이벤트 / 별도 메신저 앱 UI (Draggable) / 축소 알림 버블 UX**:
  - 전력/산소 보고서 또는 이력서 검토 단계 중 전체 뷰포트나 우측 ECHO 영역이 아닌 **좌측 업무 화면(Desktop Workspace Panel / Left Panel) 경계 내부의 오른쪽 상단(Top-Right)** 무작위 메신저 알림 팝업 발생 (알림 SFX 포함)
  - 팝업 클릭 시 별도의 메신저/채팅 앱 창 인터페이스가 열리며, **좌측 업무 화면 경계 영역 안에서 플레이어가 자유롭게 드래그하여 위치 이동(Draggable UI)**이 가능함
  - 팝업/채팅창 축소(닫기) 시: 답장 전 축소 시에는 **좌측 업무 화면 경계 내부의 오른쪽 하단(Bottom-Right)**에 말풍선 아이콘 + 빨간색 신규 알림 버블(숫자 `1`) 노출(아이콘 클릭 시 메신저 앱 창 재개), 답장 완료 후 축소 시에는 축소된 말풍선 아이콘에 신규 메시지 알림 버블(숫자 `1`) 미노출
  - 동료 질문 카피: 항상 점심 메뉴를 묻는 질문 (예: `"오늘 점심 메뉴 뭐먹을래?"`)
  - 자유 텍스트 답장 및 동료 1회 긍정 반응 수신 (`"그 메뉴 좋다!"`), 답장 입력창 하단 몰입 방해 메타 문구 (`"※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다."`) 전면 제거 및 자연스러운 diegetic UX 유지 (추가 입력 시 `'읽지 않음(1)'` / `Unread` 상태 유지)
- **지원자 이력서 검토 기능 및 서사적 판정**: ECHO의 적합성 질의 안내 대사, 여러 명의 지원자 후보 프로필 제시, 후보별 '적격'/'부적격' 판정 선택 버튼 (퍼즐/엔딩 미영향 서사적 선택 요소), ECHO 대화창 지원자 적합성 Q&A
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
- [업데이트 승인] 클릭 시 ECHO 대화창 리부팅 (CSS/SVG 기반 visual glitch, 애니메이션, 사운드) 및 ECHO의 위협 요소 오판 / 비상 봉쇄 발령 연출
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
- 좌측 화면의 탭(Tab) 기반 자유 선택 메뉴
- ECHO 대화창 텍스트/키워드 인식 기반 업무 전환 (좌측 보고서 하단 단순 [확인 완료] 버튼으로 처리)
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

- NPC API specification: Cloudflare Worker Hermes NPC API (`https://royal-firefly-60c3.jwpark971219.workers.dev`, `npcId: echo | coworker`, TypeScript 타입 `src/types/npc.ts`, 3초 타임아웃 및 100% 로컬 Fallback 포함)로 확정되어 `feat-007` 진행 중.

## MVP Acceptance Criteria

- 사용자는 3D 메인 메뉴에서 [게임 시작] 클릭 시 Smooth Zoom-in 연출과 함께 **100% Full Screen** 터미널 화면으로 전환할 수 있다.
- 전환 후 사용자는 `🔒 READ-ONLY`, "시스템 자동 인증이 완료되었습니다...", "Clock-in :: 2분할 업무 화면 진입" 등 메타 텍스트가 전면 제거된 Diegetic 회사 인트라넷 화면에서 로그인 폼(`woojoo.kim` / `**********`)과 '김우주' 캐릭터 정보를 확인하고 단순 [출근] 버튼을 클릭할 수 있다.
- [출근] 클릭 시 탭 메뉴 및 개발용 용어가 제거된 Workstation 화면(좌: 업무 UI, 우: ECHO 대화창)으로 전환된다.
- ECHO가 우측 대화창에서 자연스러운 Diegetic 대사(개발자 지침풍 텍스트 전면 제거)로 업무를 브리핑하고 좌측 화면에 업무 문서(자원 채굴 보고서 ➔ 전력/산소 보고서 ➔ 이력서 검토 ➔ 업데이트 기안)를 제시하며, 보고서 읽기 중 ECHO의 실시간 반응 대사(최대 2개)가 출력된다.
- 플레이어가 좌측 보고서/문서 하단의 보조 텍스트("(다음 업무로 이동)")가 완전 제거된 단순 **[확인 완료]** 버튼을 클릭하면, 우측 ECHO 대화창에 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 대사가 출력되고 좌측 업무 화면이 다음 업무 문서로 전환된다.
- 전력/산소 보고서 또는 이력서 검토 중 전체 뷰포트나 우측 ECHO 영역이 아닌 **좌측 업무 화면(Desktop Workspace Panel / Left Panel) 경계 내부의 오른쪽 상단(Top-Right)**에 무작위 동료 메신저 알림 SFX/팝업이 발생한다.
- 사용자가 팝업을 클릭하면 별도의 메신저 앱 창이 열리고(**좌측 업무 화면 경계 영역 안에서 자유롭게 드래그 위치 이동 가능**), 점심 메뉴 질문(`"오늘 점심 메뉴 뭐먹을래?"`)을 확인하며 자유 텍스트로 답장할 수 있다. 답장 입력창 하단의 몰입 방해 메타 문구(`"※ 1회 답장 완료 후 메신저 채널은 읽지 않음(1) 상태로 유지됩니다."`)는 전면 제거되어 노출되지 않으며, 답장 후 동료가 긍정 반응 메시지(`"그 메뉴 좋다!"`)를 1회 보내오며, 이후 추가 입력 시 자연스러운 diegetic UX로 `'읽지 않음(1)'` 상태가 유지된다.
- 사용자가 메신저 팝업/채팅창을 축소(닫기)할 때, 답장 전 축소 시에는 **좌측 업무 화면(Desktop Workspace Panel / Left Panel) 경계 내부의 오른쪽 하단(Bottom-Right)**에 말풍선 채팅 앱 아이콘과 빨간색 신규 메시지 알림 버블(숫자 `1`)이 표시되며(아이콘 클릭 시 채팅 앱 창 재개), 답장 완료 후 축소 시에는 축소된 말풍선 아이콘에 신규 메시지 알림 버블(숫자 `1`)이 더 이상 노출되지 않는다.
- Cloudflare Worker NPC API (`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 통해 ECHO (`npcId: 'echo'`) 및 동료 메신저 (`npcId: 'coworker'`)에 외부 AI 응답을 제공하며, 3초 타임아웃 미수신 또는 네트워크 단절/에러 발생 시 100% 로컬 Fallback 대사/응답으로 대체되어 게임이 중단 없이 정상 진행된다.
- 이력서 검토 단계에서 사용자는 여러 명의 지원자 프로필을 확인하고 '적격'/'부적격' 평가 버튼을 누를 수 있으며(게임 진행/퍼즐/엔딩에는 미영향), ECHO 대화창으로 지원자 적합성에 대해 질의응답할 수 있다.
- 라포 Phase 동안 비상 HUD 및 60분 타이머는 노출/작동하지 않는다.
- 사용자가 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]을 클릭하면 ECHO 대화창이 리부팅된다.
- 리부팅 완료 후 ECHO가 플레이어/선내 환경을 위협 요소로 오판하여 비상 봉쇄를 발령하며, 이 시점에 비상 HUD(산소/전력)가 표시되고 60분 타이머 작동이 시작된다.
- 비상 봉쇄 후 카테고리 A 본 퍼즐(파일 탐색, Act 1~3 증거 제출, deterministic ECHO 판정, Normal Ending A)로 정상 진입한다.
- Act 3 성공 시 통제실 문 해제 상태와 Normal Ending이 표시된다.



