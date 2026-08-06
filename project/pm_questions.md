# PM Questions

## Document Meta

- version: 0.3
- pm agent: codex
- date: 2026-08-06
- status: Q11 still blocking external AI; original-source phase 2 can proceed

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
