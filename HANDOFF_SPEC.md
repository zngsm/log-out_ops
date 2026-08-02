# PM Handoff Spec

이 문서는 사람이 작성한 게임 기획을 PM agent가 오해 없이 분석할 수 있도록, `PM에게 선행 전달해야 하는 입력 문서 세트`를 정의한다.

핵심 원칙은 간단하다.

- 사람의 러프 문서는 그대로 두어도 된다.
- 하지만 PM agent에게 분석을 요청하기 전에는 아래 구조로 재정리된 입력 문서가 있어야 한다.
- PM agent는 이 입력 문서 세트를 읽고 분석, 질의, MVP 범위화, task 분해를 수행한다.

## Why This Exists

게임 기획은 보통 아래 정보가 한 문서에 섞여 있다.

- 세계관
- 플레이 감정
- 시스템 규칙
- 씬 흐름
- 연출
- 오디오
- 에셋
- 구현 우선순위

이 상태로는 PM agent가 정확히 분석하기 어렵다.
그래서 사람의 의도를 아래 5개 입력 문서로 분리해야 한다.

## Required Human Input Docs

PM agent에게 넘기기 전에 최소 아래 5개 문서를 준비하는 것을 권장한다.

### 1. `project/project_brief.md`

무엇을 만들고 싶은지 정의하는 문서다.

반드시 포함:

- 게임 한 줄 설명
- 플레이어 목표
- 핵심 재미
- 세계관 / 배경
- 목표 플랫폼
- 세션 길이
- 이번 빌드 목표
- 이번 빌드에서 제외할 것

### 2. `project/gameplay_spec.md`

게임 규칙과 상태 전이를 정의하는 문서다.

반드시 포함:

- 코어 루프
- 승리 / 실패 조건
- 리소스 규칙
- 입력 방식
- 상태 전이
- 퍼즐 진행 규칙
- 오답 패널티
- 예외 처리

### 3. `project/scene_flow.md`

씬, Act, 컷씬, 대사 흐름, 시간 분배를 정의하는 문서다.

반드시 포함:

- Act/Scene 목록
- 각 씬의 목적
- 플레이어가 씬에서 해야 하는 일
- 시작 조건 / 종료 조건
- 예상 소요 시간
- 컷씬 유무
- 대사 / 힌트 공개 타이밍
- 상호작용 가능 시점

### 4. `project/direction_and_content.md`

톤앤매너, UI 무드, 연출 방향, 텍스트 스타일을 정의하는 문서다.

반드시 포함:

- 비주얼 톤
- UI 분위기
- ECHO 말투
- 로그 문체
- 경고/글리치/조명 연출 규칙
- BGM/SFX 방향
- 확정 대사와 예시 대사 구분

### 5. `project/asset_plan.md`

어떤 asset이 어디서 어떻게 필요한지 정의하는 문서다.

반드시 포함:

- asset id
- asset type
- 사용 씬
- 트리거
- 용도
- 필수 여부
- 규격
- 포맷
- placeholder 허용 여부

## Human Template Paths

사람이 실제로 참고할 템플릿은 아래 5개다.

- `templates/human-input/project_brief.template.md`
- `templates/human-input/gameplay_spec.template.md`
- `templates/human-input/scene_flow.template.md`
- `templates/human-input/direction_and_content.template.md`
- `templates/human-input/asset_plan.template.md`

## Optional Human Input Docs

아래 문서는 있으면 좋지만 없다고 바로 분석이 불가능한 것은 아니다.

- `project/reference_links.md`
- `project/monetization_notes.md`
- `project/live_ops_notes.md`
- `project/change_intent.md`

## Mapping From Rough Docs

현재처럼 `우주선_*.md` 형태로 러프 문서가 있을 때는 보통 이렇게 재배치하면 된다.

### `우주선 탈출게임 개요.md`

주로 아래로 분해:

- `project/project_brief.md`
- `project/scene_flow.md`
- `project/direction_and_content.md`

### `우주선 탈출 게임 로그 파일 구조.md`

주로 아래로 분해:

- `project/gameplay_spec.md`
- `project/asset_plan.md`

### `우주선 탈출게임 로그 예시.md`

주로 아래로 분해:

- `project/direction_and_content.md`
- `project/gameplay_spec.md`

### `우주선 탈출 게임 AI 프롬프트 예시.md`

주로 아래로 분해:

- `project/direction_and_content.md`
- `project/gameplay_spec.md`

## What PM Agent Assumes

PM agent는 아래를 스스로 추론하면 안 된다.

- 컷씬 길이
- 씬별 플레이 시간
- 어떤 asset이 필수인지
- 어떤 연출이 MVP에 포함되는지
- 수치 밸런스
- 예시 대사가 확정 대사인지 여부

이 정보는 사람 입력 문서에 있어야 한다.

## Minimum Acceptable Handoff

최소한 아래가 채워져 있으면 PM agent가 분석을 시작할 수 있다.

- `project/project_brief.md`
- `project/gameplay_spec.md`
- `project/scene_flow.md`

다만 게임 완성도와 QA 정확도를 위해서는 아래까지 권장한다.

- `project/direction_and_content.md`
- `project/asset_plan.md`
