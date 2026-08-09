# PM Analysis

## Document Meta

- version: 1.2
- pm agent: codex
- date: 2026-08-10
- status: updated - 18가지 상세 게임플레이/UI/내용 정제 요청 사양 (1. 컷신 타임라인 rebooting -2s / lockdown +2s, 2. 메인 터미널 UI 정제 17종: 파일 뷰어 <dt>증거성</dt>/<dt>상태</dt> 삭제, Act-1 Mission 삭제, Evidence 0/1 삭제, Tool manual 보안 메모 삭제, 사이드바 Log fixer mini program 삭제 & 파일 뷰어 버튼 유지, 잠긴 파일/오입력 힌트 삭제, 손상/삭제 파일 복구 전 내용 은폐, NEXT ACTION 삭제, HOW TO PLAY 첫 목표/Open first file 삭제, Log Fixer 완료 메타 문구 삭제, 타이머 HUD NORMAL SESSION/Act-1 삭제, power_grid_maint.note 디제틱 한국어 재작성, Recycle_Bin 파일 복구 전 첨부 불가, Sensor diagram 프롬프트 삭제 및 명시 라벨 교체, DIAGNOSTIC NOTE 삭제, O₂ LEVEL drain x1.0x 삭제) 반영 완료
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

플레이어는 3D 메인 메뉴에서 100% Full Screen 터미널 화면으로 전환된 후, 몰입을 방해하는 메타/개발용 텍스트(`🔒 READ-ONLY` 마크, "시스템 자동 인증이 완료되었습니다...", [출근] 하단 "Clock-in :: 2분할 업무 화면 진입" 등)가 완전 제거된 Diegetic 회사 인트라넷 화면에서 로그인 폼(`woojoo.kim`, `**********`)을 확인하고 [출근]한다. 

이후 헤르메스 Workstation 화면에서 개발용 용어("2분할 업무 화면", "라포 Phase" 등)와 보조 메타 문구("(다음 업무로 이동)" 괄호 텍스트 등)가 완전 제거되고 단순 `✓ [확인 완료]`로 버튼 텍스트가 통일 고정된 상태에서, 자연스러운 Diegetic 대사를 바탕으로 진행한다. ECHO가 우측 대화창에서 업무를 브리핑하고 좌측 하단 `✓ [확인 완료]` 버튼 클릭에 따라 업무 문서를 순차적으로 진행한다. 보고서 읽기 중 ECHO의 실시간 반응 대사(최대 2개), [확인 완료] 버튼 클릭 시 ECHO의 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 대사 안내 및 화면 전환, 업무 중 무작위 발생하는 동료 메신저 알림 팝업(좌측 업무 화면 경계 내 우상단)/앱 UI(좌측 업무 화면 내 드래그 자유 이동 Draggable UI) 및 축소 알림 버블(답장 전 축소 시 숫자 `1`, 답장 완료 후 축소 시 미노출; 리부팅 진행 동안 `rebootState !== 'idle'` 아이콘 완전 숨김), 점심 메뉴 질문(`"오늘 점심 메뉴 뭐먹을래?"`), 자유 텍스트 답장 후 동료 긍정 반응(`"그 메뉴 좋다!"`) 1회 수신, 지원자 이력서 3명 후보 서사적 적격/부적격 판정(안내 배너 및 `서사적 판정 선택:` 라벨 전면 삭제, 텍스트 변경 없이 단순 `✓ [확인 완료]` 표기 고정 & 미선택 시 그레이 비활성화 `disabled={isResumeIncomplete}`로 필수 평가 유도, 퍼즐/엔딩 영향 없음 & 이력서 검토 단계 ECHO 대화/Q&A 전면 비활성화)을 거친다.

이후 메타 경고 문구가 전면 삭제된 "ECHO 시스템 업데이트 필요" 기안 승인으로 본 퍼즐(ECHO 패치 승인 클릭 후 rebooting 상태 2초 축소, lockdown 상태 2초 연장된 9초 컷신 연출, 비상 HUD & 60분 타이머 가동)로 진입한다. 본 퍼즐 진입 후 메인 터미널 UI는 다음 17가지 정제 사양이 엄격히 준수된다:
1) 파일 뷰어 내 `<dt>증거성</dt>`, `<dt>상태</dt>` DL 항목 삭제
2) 우측 대화창/태스크 헤더의 `Act-1 Mission` 라벨 삭제
3) 대화창/작성기 헤더의 `Evidence 0/1` 트레이 삭제
4) Tool manual 보안 메모 삭제
5) 좌측 사이드바 `Log fixer mini program` 카드/폼 삭제 (파일 뷰어의 `[OPEN WITH LOG_FIXER]` 버튼은 파일 복구 단일 진입점으로 유지)
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

또한 `/System/Security` 제한 구역 클릭 시에는 한국어 암호 모달("보안 게이트 :: 제한 구역", "/System/Security 디렉터리는 김 박사의 비상 격리 프로토콜에 의해 잠겨 있습니다. 승무원 메일에서 발견된 직인 암호를 입력하십시오.")이 호출되며, 전력 0% 차감으로 인한 블랙아웃 발생 시에는 화면 중앙 단일 강조 팝업(Center Modal)과 한국어 문구("⚠️ [전력 고갈] 주 전력 그리드 블랙아웃! OS 터미널 긴급 재부팅 중... (남은 시간: N초)")가 노출된다. ECHO 대화 및 동료 대화는 Cloudflare Worker NPC API(`https://royal-firefly-60c3.jwpark971219.workers.dev`)를 연동하되, 3초 타임아웃 및 100% 로컬 Fallback 안전장치를 가동하여 오프라인/네트워크 단절 시에도 완전한 플레이를 보장한다.

## Core Loop

1. 3D 메인 메뉴에서 [게임 시작] 클릭 시 100% Full Screen Smooth Zoom-in 연출로 인게임 터미널 화면에 진입한다.
2. 전환 후 회사 인트라넷 화면에서 메타 문구가 제거된 자연스러운 로그인 폼(아이디: `woojoo.kim`, 비밀번호: `**********`)과 '김우주' 캐릭터 정보를 확인하고 [출근] 버튼을 클릭한다.
3. Hermes Workstation 화면(좌: 업무 화면, 우: ECHO 대화창)으로 진입하여 비상 HUD/타이머 미노출 상태로 ECHO 대화 브리핑 & `✓ [확인 완료]` 버튼 순차 업무 흐름(라포 Phase)을 진행한다:
   - 탭 메뉴가 제거된 좌측 화면에 ECHO가 우측 대화창을 통해 업무 문서를 순차적으로 출력한다.
   - **자원 채굴 보고서**: ECHO 브리핑 ➔ 좌측 출력 ➔ 보고서 검토 중 ECHO 실시간 반응(최대 2개) ➔ 좌측 하단 `✓ [확인 완료]` 버튼 클릭 ➔ ECHO 대사 `"다음 업무는 [다음 업무명]입니다. 보여드릴게요."` 출력 및 다음 업무 전환.
   - **전력/산소 보고서**: 좌측 출력 ➔ 자원 상태 데이터 확인 ➔ ECHO 실시간 반응(최대 2개) ➔ 좌측 하단 `✓ [확인 완료]` 버튼 클릭 ➔ 다음 업무 전환.
   - **동료 메신저 팝업 이벤트**: 전력/산소 보고서 또는 이력서 검토 중 무작위 발생 (좌측 업무 화면 경계 내 우상단 팝업 클릭 시 별도 메신저 앱 창 노출 & 좌측 업무 화면 내 드래그 자유 이동 Draggable UI, 축소/닫기 시 좌측 업무 화면 경계 내 우하단 말풍선 아이콘 + 신규 알림 버블(답장 전 축소 시 숫자 `1`, 답장 완료 후 축소 시 미노출; 리부팅 진행 동안 `rebootState !== 'idle'` 아이콘 완전 숨김), 점심 메뉴 질문, 자유 텍스트 답장, 동료 긍정 반응 1회 수신, 답장 입력창 하단 메타 문구 전면 제거 및 diegetic '읽지 않음(1)' 유지). 메신저 대화는 Cloudflare Worker NPC API (`npcId: 'coworker'`, 3초 타임아웃, 예외 시 100% 로컬 Fallback) 연동.
   - **지원자 이력서 검토**: 3명 후보 프로필 출력 ➔ 메타 안내 배너 및 `서사적 판정 선택:` 라벨 전면 삭제 ➔ 후보별 '적격'/'부적격' 판정 ➔ 버튼 텍스트 단순 `✓ [확인 완료]` 통일 고정 & 3명 중 미선택 이력서 존재 시 그레이 비활성화(`disabled={isResumeIncomplete}`)로 필수 평가 완수 유도 ➔ 퍼즐/엔딩 영향 없는 몰입용 서사적 선택 ➔ 우측 ECHO 대화창 및 Q&A 질의응답 입력 기능 비활성화 (ECHO 대화 불가능 처리) ➔ 3명 평가 완수 후 `✓ [확인 완료]` 클릭으로 업데이트 기안 전환.
   - **ECHO 업데이트 기안 승인**: 이력서 검토 후 제시되는 업데이트 승인 기안 (4번 미션 문서 내 메타/개발자 경고 문구 전면 삭제).
4. 업무 미션 중 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인]을 클릭하면 ECHO 대화창이 리부팅(CSS/SVG visual glitch, 에러 경고, 사이렌, 데콤프레션, rebooting -2초/lockdown +2초 조절된 9초 컷신 연출)되며, 리부팅 중 우하단 동료 메신저 버블은 완전히 숨김 처리된다.
5. 리부팅 연출 완료 후 ECHO가 플레이어 및 선내 환경을 위협 요소로 오판하고 비상 봉쇄를 발령하며, 비상 HUD(산소/전력) 표시 및 60분 카운트다운 타이머가 가동된다 (본 퍼즐 진입).
6. 비상 봉쇄 후 플레이어는 Hermes OS 파일 탐색기에서 로그, 설정, 복구 대상 파일을 탐색하고 산소/전력을 관리한다 (파일 뷰어 `<dt>증거성</dt>`/`<dt>상태</dt>` 삭제, `Act-1 Mission` 라벨 삭제, `Evidence 0/1` 트레이 삭제, Tool manual 보안 메모 삭제, 사이드바 `Log fixer mini program` 삭제, 잠긴 파일/오입력 힌트 삭제, 손상/삭제 파일 복구 전 내용 은폐, `NEXT ACTION` 띠 삭제, `HOW TO PLAY` 첫 목표/Open first file 삭제, Log Fixer 완료 메타 문구 삭제, 타이머 HUD `NORMAL SESSION`/`Act-1` 삭제, `power_grid_maint.note` 디제틱 한국어 재작성, 휴지통 복구 전 첨부 불가, Sensor diagram 프롬프트 삭제 및 명시 라벨 교체, `DIAGNOSTIC NOTE` 삭제, `O₂ LEVEL` `drain x1.0x` 삭제).
7. ECHO 대화창에 증거 파일과 텍스트 주장을 제출하여 Act 1, Act 2, Act 3 순서로 반박한다. (ECHO 연동: `npcId: 'echo'`, Cloudflare Worker NPC API 3초 타임아웃 및 예외 발생 시 100% 로컬 Fallback 적용)
8. Act 3까지 성공하면 통제실 문이 열리고 Normal Ending A로 탈출한다.

## Scope Conflicts & Change-001 Adjustments

### MVP category scope

Resolved: MVP에서는 카테고리 A 단일 시나리오만 먼저 구현한다. 나머지 시나리오는 MVP 이후 확장 후보로 둔다.

### Visual implementation scope (Updated by Change-001 & Q19, Q26, Q31)

Resolved: 메인 메뉴 화면의 배경 우주선/컴퓨터는 R3F 기반 3D 모델을 유지한다. 3D 컷신 기획은 **CSS / SVG 기반 2D 인게임 연출**로 변경한다. 메인 메뉴에서 터미널 진입 연출은 Smooth Zoom-in을 유지하되 화면 모니터 비율을 기존 90%가 아닌 **100% Full Screen**으로 채운다. `ECHO 패치 승인` 클릭 후 발동되는 rebooting/lockdown 컷신 연출 타임라인은 rebooting 상태를 2초 줄이고 lockdown 상태를 2초 연장한다. 리부팅 진행 동안(`rebootState !== 'idle'`) 우하단 동료 메신저 말풍선 버블 아이콘은 화면에서 완전히 숨김(미노출) 처리한다.

### Narrative & Entry Flow (Updated by Change-001, Q16~Q48 User Feedback)

Resolved: 게임 진입 직후 비상 봉쇄 상태로 바로 들어가지 않고, **회사 인트라넷 (Diegetic 로그인 폼 `woojoo.kim`/`**********`, 메타 텍스트 전면 제거) -> [출근] -> Workstation (탭 제거, ECHO 업무 브리핑, 좌측 하단 단순 `✓ [확인 완료]` 버튼 업무 전환, 실시간 반응 대사, 동료 메신저 무작위 팝업(좌측 업무 화면 경계 내 우상단)/앱 UI(좌측 업무 화면 내 드래그 자유 이동 Draggable UI)/알림 버블(답장 전 `1`, 답장 완료 후 미노출; 리부팅 동안 완전 미노출), 이력서 안내 배너 및 '서사적 판정 선택:' 라벨 삭제, 버튼 표기 단순 `✓ [확인 완료]` 고정 & 미선택 이력서 존재 시 그레이 비활성화 필수 평가, 이력서 검토 중 ECHO 대화 비활성화) -> ECHO 시스템 업데이트 승인 (기안 내 메타 경고 문구 전면 삭제) -> ECHO 리부팅 (rebooting -2s/lockdown +2s 조절 컷신 연출 & 메신저 버블 숨김) -> 비상 봉쇄 & 비상 HUD/60분 타이머 가동 -> 본 퍼즐 진입 (18가지 상세 메인 터미널 UI/내용 정제 사양 반영)** 순서로 전개한다.

### Act 3 evidence scope

Resolved: 카테고리 A MVP의 Act 3 정답 증거는 원문 기획서 기준인 `ai_priority_matrix.json` + `deleted_override.txt`로 확정한다.

### AI External NPC API Integration (Updated for feat-007)

Resolved: Cloudflare Worker 기반 Hermes NPC API 명세(`https://royal-firefly-60c3.jwpark971219.workers.dev`, `npcId: echo | coworker`, TypeScript 타입 `src/types/npc.ts`)를 연동한다. 3초 타임아웃(`AbortController`)과 예외/단절 발생 시 100% 로컬 Fallback 안전장치를 가동하여 오프라인/장애 시에도 끊김 없이 동작한다.

## PM Readiness

- 기획 방향성 분석: ready (Change-001 및 Q21~Q48 사용자 피드백, Cloudflare Worker NPC API 명세 반영 완료)
- MVP 범위 확정: ready for Cloudflare Worker NPC API integrated MVP with Diegetic/ECHO-driven flow and 100% local fallback
- 전체 task 확정: `feat-001`~`feat-034` (완료 및 18가지 상세 정제 반영), `feat-007` (done - Cloudflare Worker NPC API & 100% 로컬 Fallback)
- Active Task: `feat-007` (completed)
- 미확정 항목: 없음 (Q1~Q48 전 항목 답변/명세 수립 완료)

## Recommended PM Decision

Cloudflare Worker NPC API 연동과 함께 3초 타임아웃 및 100% 로컬 Fallback 안전장치를 적용하는 `feat-007`을 완료하고, 18가지 상세 게임플레이/UI/내용 정제 사양을 운영 문서 전반에 적용하여 개발 및 QA 검증 표준으로 확정한다.



