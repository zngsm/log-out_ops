# PM Questions

## Document Meta

- version: 0.6
- pm agent: codex
- date: 2026-08-09
- status: Q21~Q23 answered; Change-001 specifications finalized; Q11 still blocking external AI

## Blocking Questions

### Q1. MVP 카테고리 범위

`project_brief.md` 기준으로는 MVP에서 카테고리 A만 구현하고 10개 카테고리 procedural 생성은 제외합니다. 반면 `scene_flow.md`에는 10개 카테고리가 상세히 들어 있습니다.

MVP는 카테고리 A 단일 시나리오만 구현하면 될까요?

### Answer

MVP에서는 카테고리 A 단일 시나리오만 먼저 구현한다. MVP 구현 이후 가능하면 나머지 시나리오를 확장한다.

### Q2. MVP 엔딩 범위

`project_brief.md`는 Ending B/C를 제외한다고 되어 있고, `scene_flow.md`는 Ending A/B/C를 모두 정의합니다.

MVP에서는 Act 3 성공 후 Normal Ending A만 구현하면 될까요?

### Answer

MVP에서는 Normal Ending A만 구현한다.

### Q3. MVP 시각 구현 범위

`project_brief.md`는 복잡한 3D/고화질 연출을 제외한다고 되어 있지만, `direction_and_content.md`와 `asset_plan.md`는 R3F, 3D 통제실, 손 모델, GLB asset을 요구합니다.

MVP에서는 3D 구현 없이 2D/CSS 기반 Hermes OS와 placeholder 배경으로 진행해도 될까요?

### Answer

MVP에서도 배경 우주선과 컴퓨터는 R3F 기반 3D 모델이 필요하다. 손 모델은 MVP에서는 placeholder로 구현한다. 컴퓨터 화면에 보이는 Hermes OS는 3D 컴퓨터와 어우러지는 선에서 2D로 구현한다.

### Q4. 카테고리 A Act 3 정답 증거

원문 기획서와 로그 예시는 `ai_priority_matrix.json` + `deleted_override.txt`를 Act 3 핵심 증거로 제시합니다. 구조화된 scene flow는 카테고리 A Act 3 증거를 `auxiliary_capacitor.log` + `emergency_grid_switch.conf`로 제시합니다.

카테고리 A MVP의 Act 3 정답 증거는 어느 조합으로 확정할까요?

### Answer

원문 기획서 기준으로 확정한다. 카테고리 A MVP의 Act 3 정답 증거는 `ai_priority_matrix.json` + `deleted_override.txt` 조합이다.

### Q5. ECHO 판정 규칙

MVP에서 ECHO 판정은 실제 LLM API 없이 로컬 deterministic rule로 구현할까요, 아니면 외부 AI/API 연동을 전제로 할까요?

### Answer

외부 AI/API 연동을 전제로 한다.

### Q6. 60분 타이머

문서상 기본 세션은 60분입니다. MVP 개발/QA 효율을 위해 실제 60분 모드와 별도 debug fast timer를 함께 제공해도 될까요?

### Answer

함께 제공한다. Debug mode에서는 컷신 스킵 기능과 15분 세션을 제공한다.

### Q7. Asset placeholder 허용 범위

`asset_plan.md`는 3D/사운드 asset 준비 전 placeholder 대체를 허용합니다.

MVP에서는 모든 외부 asset을 CSS, SVG, WebAudio synthetic sound 같은 placeholder로 대체해도 될까요?

### Answer

대체 가능하다.

## Non-blocking Follow-up Questions

### Q8. 플레이어 입력 자유도

ECHO 대화창은 자유 텍스트 입력을 허용하되 키워드/첨부 파일 기반으로 판정하면 될까요?

### Answer

자유 텍스트 입력 대화를 통해 힌트를 얻고, 입력 텍스트에 키워드가 있을 경우 판정한다. 첨부 파일은 파일 탐색기에서 클릭했을 때 입력창에 `@{로그파일명}` 형태의 컨텍스트 태그로 주입한다. 태그는 사용자가 쉽게 지울 수 있어야 한다.

### Q9. 로그 난독화 난이도

MVP의 로그는 사람이 직접 읽고 추론 가능한 평문 중심으로 둘까요, 아니면 암호/복구/오프셋 계산을 실제 퍼즐로 구현할까요?

### Answer

암호, 복구, 오프셋 계산을 실제 퍼즐로 구현한다.

### Q10. 실패 UX

산소 0% 또는 전력 악화로 실패했을 때 즉시 게임 오버 화면으로 이동하면 될까요, 아니면 ECHO 최종 대사와 짧은 연출이 필요할까요?

### Answer

화면이 암전되는 정도의 짧은 연출이 필요하다.

## Derived Blocking Questions

### Q11. 외부 AI/API provider와 인증 방식

ECHO 판정은 외부 AI/API 연동으로 확정되었다. 구현을 시작하려면 provider, model, API key env var 이름, 실패 시 fallback 정책, 클라이언트 직접 호출 금지 여부가 필요하다.

어떤 AI/API provider와 model을 사용하고, API key는 어떤 env var 이름으로 받을까요?

### Q12. Act 3 최종 퍼즐 방향성

### Answer

Resolved by the primary original source and Q4.

Current Category A MVP and Phase 2 vertical slice keep `ai_priority_matrix.json` + `deleted_override.txt` as the canonical Act 3 solution.

The older power-route pair, `auxiliary_capacitor.log` + `emergency_grid_switch.conf`, is not a blocker for current implementation. It can be reconsidered only as a later phase expansion, alternate route, or advanced ending after human approval.

### Q13. 다음 목표의 완성도 기준

다음 milestone은 단순히 기능이 동작하는 MVP를 유지할까요, 아니면 원 기획 의도를 체감할 수 있는 vertical slice로 재정렬할까요?

### PM Recommendation

`first vertical slice that feels like the intended game`로 전환하는 것을 권장합니다.

### Answer

PM assumes Phase 2 should target a first vertical slice that feels like the intended game because the user explicitly requested re-planning against the original `LOG_OUT **.md` intent.

### Q14. 파일 내 직접 힌트 노출 정책

현재 일부 파일에는 `[PLAYER NOTE]` 형태로 정답에 가까운 힌트가 직접 노출됩니다.

이 힌트를 MVP 플레이어에게 계속 보여줄까요, 아니면 debug/hint toggle 뒤로 숨기고 실제 파일은 diegetic log로만 유지할까요?

### PM Recommendation

프로덕션 플레이에서는 숨기고, debug/hint layer로 분리하는 것을 권장합니다.

### Answer

PM assumes Phase 2 should move direct `[PLAYER NOTE]` style hints behind debug/hint UI while keeping diegetic file contents readable.

### Q15. ECHO AI 재개 시점

외부 AI/API를 지금 재개할까요, 아니면 먼저 deterministic scripted ECHO 대화/연출 시스템을 만들어 의도한 경험을 API 없이 구현할까요?

### PM Recommendation

먼저 scripted ECHO를 구현하고, 외부 AI는 힌트/자유 대화 확장으로 붙이는 것을 권장합니다.

### Answer

PM assumes Phase 2 should implement deterministic scripted ECHO first. External AI remains blocked only by Q11.

## Change-001 Derived Questions

### Q16. 라포 형성 Phase의 좌측 업무 화면 미션 목록 및 문서 구체 사양

Change-001 기획 변경으로 라포 형성 Phase (약 5분간)에 AI 관리자로서 좌측 업무 화면에서 실제 업무 미션을 수행합니다. "ECHO 시스템 업데이트 필요" 기안 외에 5분간 플레이어가 처리해야 하는 구체적인 서류/보고서/기안 미션 목록과 문서 양식이 기획서에 명시되어 있지 않습니다.

라포 형성 Phase 동안 수행할 업무 미션의 구체적 리스트와 문서 내용을 제공해 주실 수 있나요?

- 미응답 리스크: 기안 승인 단일 버튼 외에 라포 형성용 인터랙티브 업무 문서 내용이 없어 5분간의 일상 업무 체험 UX를 완성하기 어렵습니다.

### Answer

라포 Phase 진행 시간은 반드시 5분에 고정될 필요 없으며 플레이어의 미션 수행 진행에 따르는 자율 진행으로 구성한다.
라포 Phase 동안 좌측 업무 화면에서 진행하는 업무 미션 목록(총 5종)은 다음과 같이 확정한다:
1. **자원 채굴 현황 보고서 확인**: 추이 그래프, 통계 데이터 등 실제 보고서처럼 보이게 구성
2. **함선의 전력/산소 현황 보고서 확인**: 함선 자원 상태 데이터 구성
3. **동료 메시지 답장**: 일상적인 소통 (예: "오늘 점심 메뉴 뭐먹을래?") ➔ 동료 반응 메시지 수신
4. **김우주의 동료 포지션 지원자 이력서 검토**: 신규 지원자 이력서 서류 확인
5. **ECHO 시스템 업데이트 기안 승인**: 업데이트 승인 처리

### Q17. 라포 형성 Phase 종료 및 비상 봉쇄 전환 조건 (시간 경과 vs 기안 승인)

라포 형성 Phase가 "약 5분간" 진행된다고 작성되어 있습니다. Phase의 종료 및 ECHO 리부팅/비상 봉쇄 진입이 5분 타이머 경과에 의해 자동 진행되는지, 아니면 플레이어가 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인] 버튼을 클릭하는 순간(5분 미만이라도) 즉시 실행되는지 조건 관계가 불명확합니다.

5분 타이머 만료 시 자동 승인 처리되는지, 아니면 시간 제한 없이 승인 버튼 클릭 시에만 전환되는지 결정이 필요합니다.

- 미응답 리스크: 플레이어가 업데이트 기안을 승인하지 않고 대기하거나 너무 일찍 승인했을 때 타이머와 서사 연출 간 충돌이 발생할 수 있습니다.

### Answer

업데이트 기안 승인이 우선적인 전환 조건이다.
시간 경과에 의한 자동 진행이 아닌, 플레이어가 "ECHO 시스템 업데이트 필요" 기안의 [업데이트 승인] 버튼을 클릭하면 ECHO 대화창이 리부팅되고 비상 봉쇄 단계로 진입한다.

### Q18. 라포 형성 Phase 중 산소/전력 HUD 및 60분 세션 타이머 표시/작동 여부

기존 기획에서는 게임 시작 직후 산소(100%)/전력(100%) 비상 HUD와 60분 제한시간 카운트다운이 동작했습니다. 라포 형성 Phase (회사 인트라넷 및 출근 후 업무 UI) 진행 동안에도 산소/전력/타이머가 화면에 표시되고 차감되는지, 아니면 ECHO 리부팅 완료 후 비상 봉쇄가 발령될 때 비상 HUD가 처음 등장하고 60분 카운트다운이 시작되는지 결정이 필요합니다.

- 미응답 리스크: 인트라넷/출근 상태에서 산소 소모가 가속되거나, 비상 봉쇄 직후 타이머 시작 연출의 일치성이 손상될 수 있습니다.

### Answer

라포 Phase 동안에는 비상 HUD 및 60분 타이머가 노출되지 않으며 차감 작동도 하지 않는다.
라포 Phase 종료(업데이트 승인 & ECHO 리부팅 완료) 이후 비상 봉쇄 발령 시점에 HUD가 표시되고 60분 타이머 카운트다운이 비로소 작동하기 시작한다.

### Q19. 2D 컷신 표현 방식 및 에셋 사양

기존 3D 컷신 기획이 2D 연출로 변경되었습니다. 2D 컷신의 구체적인 표현 방식(예: MP4/WebM 비디오, CSS/SVG 기반 인게임 연출, 텍스트 + 2D 일러스트 스틸컷 slide-show) 및 요구되는 에셋 확장자/해상도가 미정입니다.

2D 컷신의 포맷과 표현 방식을 어떤 형태로 구현할까요?

- 미응답 리스크: 에셋 수급 차질 및 인게임 Cutscene Player 컴포넌트의 구현 방식 혼선.

### Answer

2D 컷신 연출은 **CSS / SVG 기반 인게임 연출**로 구현한다.

### Q20. 회사 인트라넷 화면의 추가 로그인/보안 인증 UX 절차 여부

인게임 터미널 Zoom-in 직후 첫 화면인 회사 인트라넷에 [출근] 버튼 외에 별도의 계정 로그인(사번/비밀번호 입력)이나 2차 인증 등의 추가 단계가 있는지, 아니면 단일 [출근] 버튼 클릭으로 바로 2분할 업무 화면에 진입하는지 명확한 UX 흐름 확인이 필요합니다.

- 미응답 리스크: 인트라넷 UI 컴포넌트 구성 요소의 축소/확장 범위 불확실.

### Answer

회사 인트라넷 화면은 아이디와 비밀번호가 이미 채워져 있는 로그인 폼 형태로 구성한다.
- 로그인 폼의 `🔒 READ-ONLY` 마크 텍스트 완전 제거
- "시스템 자동 인증이 완료되었습니다. 계정 정보는 보안 정책에 의해 수정 불가능한 읽기 전용 상태입니다." 메타 텍스트 완전 제거
- 아이디: `woojoo.kim`
- 비밀번호: 10자리 마스킹 처리 (`**********`)
로그인 폼과 함께 단순 [출근] 버튼만 노출되며 (하단 "Clock-in :: 2분할 업무 화면 진입" 등 메타 문구 완전 제거), [출근] 버튼 클릭 시 업무 화면으로 진입한다.

## Change-001 Follow-up & Feedback Questions

### Q21. 지원자 이력서 검토 후보 인원 및 판정 결과 영향 범위

사용자 피드백으로 지원자 이력서 검토 시 "여러 명의 지원자 후보 프로필 제시" 및 "후보별 '적격'/'부적격' 판정 선택 기능"이 도입되었습니다. 
제시되는 지원자 후보의 적정 인원수(예: 3~4명)와 플레이어의 '적격'/'부적격' 판정 결과가 라포 Phase 이후 본 퍼즐 진행이나 대화/엔딩에 영향을 주는지, 아니면 오직 라포 형성을 위한 서사적 선택 요소인지 사양이 필요합니다.

- 미응답 리스크: 지원자 데이터 세트 구성 및 판정 상태의 게임 데이터 지속성 저장 범위 불확실.

### Answer

지원자 이력서 검토 시 '적격' / '부적격' 판정 선택 결과는 게임 진행, 퍼즐, 엔딩에 아무런 영향도 미치지 않음 (몰입용 서사적 선택 요소).

### Q22. ECHO 대화 주도 업무 전환 시 플레이어 대화 요청 인식 규칙

ECHO가 보고서 검토 완료 안내 후 플레이어가 대화로 요청 시 다음 업무 문서를 출력하도록 결정되었습니다 ("ㅇㅇ 보고서 검토를 완료하셨으면 저에게 말씀해 주세요. 다음 업무인 ㅇㅇ을 보여드리겠습니다").
플레이어가 ECHO 대화창에 입력하는 문장에서 다음 업무 요청 의도를 인식하는 방식(특정 키워드 포함 매칭 e.g. "다 봤어", "다음", "보여줘" vs ECHO 대화창 상단의 빠른 대화 요청 버튼 템플릿 제공 vs NLP 의도 감지)의 구체 사양이 필요합니다.

- 미응답 리스크: 플레이어 대화 입력 파싱 로직의 복잡도 및 텍스트 미인식에 따른 업무 진행 막힘 현상 발생 위험.

### Answer

ECHO 채팅 대화 인식 방식 대신, **좌측 보고서/문서 하단에 [확인 완료] 버튼**을 배치하여 업무를 전환한다.
- **메타 문구 제거 & Diegetic 정제**:
  - 보고서 하단 버튼: "(다음 업무로 이동)" 괄호 보조 텍스트를 완전 제거하고 단순 `[확인 완료]`로만 표기한다.
  - ECHO 첫 안내 대사: "좌측 보고서 하단의 [확인 완료] 버튼을 눌러 다음 업무로 진행하세요" 등 개발자/튜토리얼 지침풍 텍스트를 제거하고, natural diegetic 대사(예: "오늘 확인하셔야 할 서류들을 좌측 화면에 올려두었습니다. 검토 후 완료되면 말씀해 주세요.")로 구성한다.
- 플레이어가 [확인 완료] 버튼 클릭 시:
  - 우측 ECHO 채팅창: "다음 업무는 [다음 업무명]입니다. 보여드릴게요." 대사 안내 출력.
  - 좌측 업무 화면: 다음 업무 문서/보고서로 화면 전환.

### Q23. 동료 메신저 팝업 이벤트 발생 시점 및 메시지 텍스트 사양

동료 메신저 이벤트가 전력/산소 현황 보고서 검토 단계 또는 지원자 이력서 검토 단계 중 무작위(랜덤) 발생하도록 결정되었습니다.
1) 보고서/이력서 화면 진입 후 팝업이 발생하는 무작위 시간 범위(예: 3초~10초 사이)
2) 동료가 보내는 첫 메시지 텍스트(예: "오늘 점심 뭐 먹을래?", "오늘 근무 끝나고 휴게실 갈래?")
3) 플레이어가 자유 텍스트 답장 후 수신되는 동료의 1회 반응 메시지 텍스트의 구체적 대사 스크립트 제공이 필요합니다.

- 미응답 리스크: 메신저 팝업 타이머 로직 및 대사 스크립트 Fixture 미비.

### Answer

동료 메신저 UI/UX 및 대화 로직 사양은 다음과 같이 확정한다:
- **질문 카피**: 항상 점심 메뉴를 묻는 질문 (예: "오늘 점심 메뉴 뭐먹을래?").
- **답장 및 동료 반응**: 플레이어가 자유 텍스트로 메뉴 답장 시 동료가 "그 메뉴 좋다!" 식의 긍정 반응 메시지 1회 수신.
- **팝업 연출**: 2분할 업무 화면 기준 **오른쪽 상단 (Top-Right)**에 메신저 팝업 알림 발생 (알림 SFX 포함).
- **별도 메신저 앱 UI**: 팝업 클릭 시 별도의 메신저/채팅 앱 창 인터페이스가 열림.
- **축소/무응답 UX & 신규 메시지 버블**: 플레이어가 팝업/채팅창을 축소(닫기)하여 나중에 응답할 수 있음. 축소 시 2분할 업무 화면 기준 **오른쪽 하단 (Bottom-Right)**에 말풍선 채팅 앱 아이콘 + 신규 메시지 알림 버블(숫자 `1`)이 노출되며, 아이콘 클릭 시 채팅 앱 재개.
- **무한 대화 방지**: 답장 ➔ 동료 긍정 반응 수신 후, 플레이어가 추가 메시지를 보내면 읽지 않음(Unread) 상태 유지.

