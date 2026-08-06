# log-out Ops Guide

이 문서는 `log-out_ops` 저장소를 실제로 운영할 때 참고하는 가이드다.

목표는 다음과 같다.

- 사람이 작성한 게임 기획 문서를 에이전트가 읽기 쉬운 구조로 정리한다.
- PM agent가 자의 판단 없이 기획을 분석하고 질문하도록 만든다.
- PM agent가 MVP 범위를 정의하고 task를 분해하도록 만든다.
- 개발 / 리뷰 / QA agent가 같은 문서 규칙을 기준으로 일하도록 만든다.

상세 운영 규칙은 [OPS_WORKFLOW.md](/Users/a202107061/private/log-out/log-out_ops/OPS_WORKFLOW.md)에 있다.
에이전트 역할 규칙은 [AGENT_PLAYBOOK.md](/Users/a202107061/private/log-out/log-out_ops/AGENT_PLAYBOOK.md)와 [agents](/Users/a202107061/private/log-out/log-out_ops/agents) 폴더에 있다.

## Quick Start

1. 사람이 러프 기획서를 준비한다.
2. 러프 기획서를 PM handoff용 입력 문서 세트로 재정리한다.
3. `pm agent, 기획서 분석해줘`로 PM agent에게 분석을 요청한다.
4. PM agent가 질문 문서를 만들면 사람이 답변한다.
5. PM agent가 MVP 범위, task board, timeline, task 문서를 만든다.
6. 개발 agent가 task 단위로 구현하고 리뷰 agent 승인까지 한 사이클로 수행한다.
7. MVP 완료 후 PM agent가 QA 계획을 만들고 QA agent가 검증한다.
8. 실패 항목은 bug task로 다시 생성한다.

## Current Project Source Of Truth

현재 LOG_OUT 프로젝트에서는 `project/human-input/LOG_OUT **.md` 원본문서가 최우선 기획 소스다.

PM/dev/QA agent는 아래 순서로 문서를 해석해야 한다.

1. `project/human-input/LOG_OUT 기획서.md`
2. `project/human-input/LOG_OUT visual 기획서.md`
3. `project/human-input/LOG_OUT 로그 예시.md`
4. `project/human-input/LOG_OUT AI 프롬포트 예시.md`
5. `project/human-input/LOG_OUT 로그파일 구조.md`
6. `project/human-input/우주선 탈출게임 개요.docx`
7. `project/human-input/LOG_OUT visual 복사본.docx`
8. `project/human-input/우주선 탈출게임 로그 예시.docx`
9. `project/human-input/우주선 탈출 게임 로그 파일 구조.docx`
10. `project/human-input/우주선 탈출 게임 AI 프롬프트 예시.docx`
11. `project/human-input/LOG_OUT_PM_QA.md`
12. PM이 생성한 `project/*.md`, `project/tasks/*.md`

원본문서와 PM 파생 문서가 충돌하면 PM agent가 자의로 판단하지 않는다. 이미지 reference가 필요한 visual 판단은 DOCX를 우선한다. 현재 phase의 정리는 [phase_2_original_source_replan.md](/Users/a202107061/private/log-out/log-out_ops/project/phase_2_original_source_replan.md)와 [docx_source_reassessment.md](/Users/a202107061/private/log-out/log-out_ops/project/docx_source_reassessment.md)를 따른다.

## Folder Guide

```text
log-out_ops/
  README.md
  OPS_WORKFLOW.md
  HANDOFF_SPEC.md
  AGENT_PLAYBOOK.md
  agents/
  templates/
    human-input/
    agent-output/
  project/
    human-input/
      LOG_OUT **.md
    project_brief.md
    gameplay_spec.md
    scene_flow.md
    direction_and_content.md
    asset_plan.md
    pm_analysis.md
    pm_questions.md
    mvp_scope.md
    task_board.md
    timeline.md
    tasks/
    qa/
    changes/
```

## What Humans Need To Fill

사람이 처음 직접 작성해야 하는 문서는 아래 5개뿐이다.

단, 현재 LOG_OUT처럼 사람이 이미 러프 원본문서 `LOG_OUT **.md`를 제공한 경우에는 이 원본문서가 최우선이다. 아래 5개 템플릿은 PM agent가 읽기 쉽게 보조 정리하는 문서이며, 원문 의도를 덮어쓰는 문서가 아니다.

상세 기준은 [HANDOFF_SPEC.md](/Users/a202107061/private/log-out/log-out_ops/HANDOFF_SPEC.md)에 있다.

| target doc | use this template |
| --- | --- |
| `project/project_brief.md` | [project_brief.template.md](/Users/a202107061/private/log-out/log-out_ops/templates/human-input/project_brief.template.md) |
| `project/gameplay_spec.md` | [gameplay_spec.template.md](/Users/a202107061/private/log-out/log-out_ops/templates/human-input/gameplay_spec.template.md) |
| `project/scene_flow.md` | [scene_flow.template.md](/Users/a202107061/private/log-out/log-out_ops/templates/human-input/scene_flow.template.md) |
| `project/direction_and_content.md` | [direction_and_content.template.md](/Users/a202107061/private/log-out/log-out_ops/templates/human-input/direction_and_content.template.md) |
| `project/asset_plan.md` | [asset_plan.template.md](/Users/a202107061/private/log-out/log-out_ops/templates/human-input/asset_plan.template.md) |

이 5개가 준비되면 아래 한 줄로 PM 분석을 시작하면 된다.

```text
pm agent, 기획서 분석해줘
```

## What PM Agent Produces

아래 문서는 사람이 처음 만들지 않는다.
`pm agent, 기획서 분석해줘` 이후 PM agent가 만들거나 갱신한다.

| output doc | purpose |
| --- | --- |
| `project/pm_analysis.md` | 기획 분석 결과 |
| `project/pm_questions.md` | 사용자에게 물어야 할 질문 |
| `project/mvp_scope.md` | MVP 범위 정의 |
| `project/task_board.md` | 전체 task 인덱스 |
| `project/timeline.md` | 작업 순서와 병렬 계획 |
| `project/tasks/*.md` | 개별 개발 업무 문서 |

## What Other Agents Produce

- DEV agent: `log-out` 코드 변경, `project/tasks/*.md` 상태 갱신, 필요한 ops 문서 업데이트를 `log-out_ops/main`에 반영
- PM agent: `project/qa/test-plan-*.md`
- QA agent: `project/qa/test-result-*.md`
- PM agent: `project/changes/*.md` 영향 분석 또는 후속 bug task 생성

## Execution Contract

이 저장소 운영에서 `dev agent feat-001 작업해줘`는 단순 구현만 의미하지 않는다.

반드시 아래를 한 사이클로 수행한다.

1. `log-out_ops/project/tasks/feat-001.md` 읽기
2. `log-out`에서 task 브랜치 생성
3. 구현
4. 검증
5. 리뷰 승인 획득
6. `log-out`에서 commit
7. `log-out`에서 push
8. `log-out_ops`의 task 상태 / 관련 운영 문서 갱신
9. `log-out_ops`는 별도 브랜치 없이 최신 `main`에 반영

즉, task 문서 상태가 바뀌면 `log-out_ops`도 같이 업데이트되어야 한다.

## PR Open Rule

사람이 아래처럼 요청할 수 있다.

```text
pr-open 해줘
```

이 요청은 현재 완료되고 승인된 task를 기준으로 PR open 준비를 수행한다.

- branch naming format: `<task-id>-<english-task-name>`
- example: `feat-001-setup-project`
- PR title format: `<TASK-ID> <한글 작업명>`
- example: `FEAT-001 Vite + React 기본 프로젝트 셋업`
- PR description format:

```md
## Summary
작업 내용 요약

## Changes
어떤 파일에서 어떤 수정 작업을 진행했는지
```

개발 agent는 `pr-open 해줘` 요청을 받으면 아래를 확인해야 한다.

- 해당 task 브랜치가 규칙에 맞는지
- 해당 task가 `done` 상태인지
- 리뷰 승인이 있는지
- commit이 완료됐는지
- push가 완료됐는지
- task 문서의 제목이 한글 작업명으로 정리되어 있는지
- 검증 기록이 task 문서에 남아 있는지

## How To Convert Current Rough Docs

현재처럼 `우주선_*.md` 러프 문서가 있을 때는 아래처럼 옮기면 된다.

### `우주선 탈출게임 개요.md`

- `project_brief.md`
- `scene_flow.md`
- `direction_and_content.md`

### `우주선 탈출 게임 로그 파일 구조.md`

- `gameplay_spec.md`
- `asset_plan.md`

### `우주선 탈출게임 로그 예시.md`

- `direction_and_content.md`
- `gameplay_spec.md`

### `우주선 탈출 게임 AI 프롬프트 예시.md`

- `direction_and_content.md`
- `gameplay_spec.md`

## Writing Rules For Human Input Docs

에이전트가 잘 이해하려면 아래 원칙이 좋다.

- 서술보다 표를 우선 사용한다.
- 씬, 시스템, 연출은 분리해서 적는다.
- "언제", "왜", "어떤 조건에서", "무슨 결과가 나오는지"를 같이 적는다.
- 예시 대사인지 확정 대사인지 구분한다.
- 시간 단위는 초, 분 등으로 명시한다.
- 모호한 형용사만 쓰지 않는다.

## How To Describe Game Details

게임은 디테일이 많아서 아래 네 가지를 분리해서 적는 게 좋다.

### 1. System Rule

예:

- 잘못된 파일 제출 시 `Power -15%`
- `Power 59%~30%` 구간에서는 산소 소모 속도 `1.5x`

### 2. Scene Flow

예:

- Scene 시작 시 문 잠금 SFX 재생
- 2초 후 ECHO 첫 대사 출력
- 대사 종료 후 파일 탐색기 활성화

### 3. Cue / Timing

예:

- `00:00` 화면 암전
- `00:02` 경고등 점멸 시작
- `00:04` 대사 타이핑 시작
- `00:10` 플레이어 입력 허용

### 4. Presentation Rule

예:

- 산소 30% 미만이면 비네팅 강도 20%
- 손상 파일은 붉은 하이라이트와 깨진 문자열 표시
- 복구 완료 시 녹색 텍스트와 짧은 글리치 효과

## Standard Workflow

### Step 1. Human Prepares Handoff Docs

사람이 아래 5개를 채운다.

- `project/project_brief.md`
- `project/gameplay_spec.md`
- `project/scene_flow.md`
- `project/direction_and_content.md`
- `project/asset_plan.md`

최소 분석 시작선은 앞의 3개 문서다.
하지만 게임 완성도를 위해 5개 전부 준비하는 것을 권장한다.

### Step 2. Ask PM Agent To Analyze

권장 요청 예시:

```text
pm agent, 기획서 분석해줘
```

이 요청에는 아래 작업이 포함된다.

- `project/project_brief.md`, `project/gameplay_spec.md`, `project/scene_flow.md`, `project/direction_and_content.md`, `project/asset_plan.md` 읽기
- `project/pm_analysis.md` 작성 또는 갱신
- `project/pm_questions.md`에 사용자 질의 정리
- 답변 완료 시 `project/mvp_scope.md` 작성
- `project/task_board.md`, `project/timeline.md` 작성
- `project/tasks/*.md` 생성 및 정리

### Step 3. Human Answers Questions

사람은 `project/pm_questions.md`를 읽고 답한다.

답변 후 권장 요청 예시:

```text
pm agent, 기획서 분석해줘
```

### Step 4. Ask Development Agent To Execute One Task

권장 요청 예시:

```text
dev agent feat-001 작업해줘
```

이 요청에는 아래 작업이 포함된다.

- `project/tasks/feat-001.md` 읽기
- 작업 계획 수립
- `log-out`에서 구현
- 검증 수행
- 리뷰 agent 요청
- 반려 시 수정 및 재요청
- 승인 후 task 상태를 `done`으로 갱신
- 리뷰 루프가 2회를 초과하면 사용자 질의

필요하면 이어서 아래 요청을 사용할 수 있다.

```text
pr-open 해줘
```

이 요청은 `commit -> push`까지 끝난 뒤 별도로 수행한다.

### Step 5. Ask PM Agent To Prepare QA

권장 요청 예시:

```text
pm agent, 테스트 시나리오 작성해줘
```

이 요청에는 아래 작업이 포함된다.

- 완료된 MVP 범위를 읽기
- `project/qa/test-plan-*.md` 작성 또는 갱신
- happy path, failure path, regression 항목 정리

### Step 6. Ask QA Agent To Execute Tests

권장 요청 예시:

```text
qa agent 테스트 해줘
```

이 요청에는 아래 작업이 포함된다.

- 최신 `project/qa/test-plan-*.md` 읽기
- `log-out` 현재 구현 기준으로 테스트 수행
- `project/qa/test-result-*.md` 기록
- bug task 환원 가능한 실패 정리

### Step 7. Ask PM Agent To Convert QA Failures Into Bug Tasks

권장 요청 예시:

```text
pm agent, 기획서 분석해줘
```

QA 결과가 생긴 뒤 다시 같은 호출을 사용하면, PM agent는 최신 QA 결과를 읽고 bug task와 후속 계획까지 갱신한다.

### Step 8. Change Request Flow

기획 변경이 생기면 먼저 변경 요청 문서를 만든다.

권장 요청 예시:

```text
이 변경 내용을 project/changes/change-001.md 형식으로 정리하고,
기존 MVP 범위와 task에 어떤 영향이 있는지 분석해줘.
문서에 없는 내용은 추론하지 말고,
필요하면 사용자 질문 문서도 같이 갱신해줘.
```

## Commands Humans Actually Use

```text
pm agent, 기획서 분석해줘
pm agent, 테스트 시나리오 작성해줘
dev agent feat-001 작업해줘
qa agent 테스트 해줘
pr-open 해줘
```

## Document Update Rules

- task 시작 시 `todo -> in_progress`
- 구현 완료 및 검증 완료 후 리뷰 승인까지 받으면 `in_progress -> done`
- 외부 답변이 필요하면 `blocked`
- 리뷰 결과와 QA 결과는 각각 이력으로 남긴다.
- 문서를 최신 상태로 유지하는 것도 업무의 일부다.

## Recommended First Files To Create

처음 시작할 때는 아래 순서가 가장 좋다.

1. `project/project_brief.md`
2. `project/gameplay_spec.md`
3. `project/scene_flow.md`
4. `project/direction_and_content.md`
5. `project/asset_plan.md`
6. `pm agent, 기획서 분석해줘`
7. `project/pm_questions.md` 답변
8. `pm agent, 기획서 분석해줘`
9. `dev agent feat-001 작업해줘`
10. `pm agent, 테스트 시나리오 작성해줘`
11. `qa agent 테스트 해줘`

## Notes

- 기획 문서는 길어도 괜찮지만, 구현 규칙은 구조화돼 있어야 한다.
- PM agent는 기획자처럼 상상하면 안 되고 분석가처럼 행동해야 한다.
- 개발 agent는 task 범위 밖의 창의적 개선을 하지 않는 편이 안전하다.
- QA agent는 “느낌상 괜찮음”이 아니라 시나리오 기준으로 통과 여부를 기록해야 한다.
