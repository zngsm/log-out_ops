# PM Questions

# Document Meta

\- version: 0.1  
\- pm agent: codex  
\- date: 2026-08-04  
\- status: waiting\_for\_human

# Blocking Questions

## Q1. MVP 카테고리 범위

project\_brief.md 기준으로는 MVP에서 카테고리 A만 구현하고 10개 카테고리 procedural 생성은 제외합니다. 반면 \`scene\_flow.md\`에는 10개 카테고리가 상세히 들어 있습니다.

MVP는 카테고리 A 단일 시나리오만 구현하면 될까요?

### A1.

MVP 스펙에선 먼저 카테고리 A 단일 시나리오만 구현. MVP 구현 이후 가능하면 나머지 시나리오도 구현

## Q2. MVP 엔딩 범위

\`project\_brief.md\`는 Ending B/C를 제외한다고 되어 있고, \`scene\_flow.md\`는 Ending A/B/C를 모두 정의합니다.

MVP에서는 Act 3 성공 후 Normal Ending A만 구현하면 될까요?

### A2.

MVP에서는 Normal Ending A만 구현

## Q3. MVP 시각 구현 범위

\`project\_brief.md\`는 복잡한 3D/고화질 연출을 제외한다고 되어 있지만, \`direction\_and\_content.md\`와 \`asset\_plan.md\`는 R3F, 3D 통제실, 손 모델, GLB asset을 요구합니다.

MVP에서는 3D 구현 없이 2D/CSS 기반 Hermes OS와 placeholder 배경으로 진행해도 될까요?

### A3.

배경이 되는 우주선은 및 컴퓨터는 r3f 기반 3D 모델 필요. 손 모델은 MVP 에서는 placeholder로 구현. 컴퓨터 화면에 보여지는 Hermes OS는 3D로 구현된 컴퓨터와 어우러지는 선에서 2D로 구현.

## Q4. 카테고리 A Act 3 정답 증거

원문 기획서와 로그 예시는 ai\_priority\_matrix.json \+ \`deleted\_override.txt\`를 Act 3 핵심 증거로 제시합니다. 구조화된 scene flow는 카테고리 A Act 3 증거를 auxiliary\_capacitor.log \+ \`emergency\_grid\_switch.conf\`로 제시합니다.

카테고리 A MVP의 Act 3 정답 증거는 어느 조합으로 확정할까요?

### A4.

원문 기획서

## Q5. ECHO 판정 규칙

MVP에서 ECHO 판정은 실제 LLM API 없이 로컬 deterministic rule로 구현할까요, 아니면 외부 AI/API 연동을 전제로 할까요?

### A5.

외부 ai/api 연동

## Q6. 60분 타이머

문서상 기본 세션은 60분입니다. MVP 개발/QA 효율을 위해 실제 60분 모드와 별도 debug fast timer를 함께 제공해도 될까요?

### A6.

함께 제공. Debug 모드에서는

* 컷신 스킵 기능  
* 15분 세션

## Q7. Asset placeholder 허용 범위

\`asset\_plan.md\`는 3D/사운드 asset 준비 전 placeholder 대체를 허용합니다.

MVP에서는 모든 외부 asset을 CSS, SVG, WebAudio synthetic sound 같은 placeholder로 대체해도 될까요?

### A7.

대체 가능

# Non-blocking Follow-up Questions

## Q8. 플레이어 입력 자유도

ECHO 대화창은 자유 텍스트 입력을 허용하되 키워드/첨부 파일 기반으로 판정하면 될까요?

### A8.

자유 텍스트 입력 대화를 통해 힌트를 얻고 입력한 텍스트에 키워드가 있을 경우에 판정. 첨부 파일의 경우 파일 탐색기에서 클릭 했을 때 텍스트 입력창에 “@{로그파일명}” 으로 컨텍스트 주입. “@{로그파일명}” 은 쉽게 지울 수 있는 태그 형식으로 입력창에 보여줌.

## Q9. 로그 난독화 난이도

MVP의 로그는 사람이 직접 읽고 추론 가능한 평문 중심으로 둘까요, 아니면 암호/복구/오프셋 계산을 실제 퍼즐로 구현할까요?

### A9.

실제 퍼즐까지 구현 필요

## Q10. 실패 UX

산소 0% 또는 전력 악화로 실패했을 때 즉시 게임 오버 화면으로 이동하면 될까요, 아니면 ECHO 최종 대사와 짧은 연출이 필요할까요?

### A10.

화면이 암전되는정도의 짧은 연출 구현 필요