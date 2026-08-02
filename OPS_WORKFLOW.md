# Ops Workflow

이 저장소는 게임 기획 문서를 에이전트가 해석 가능한 운영 문서로 정규화하고, PM/개발/리뷰/QA 에이전트가 같은 규칙으로 일하도록 만들기 위한 공간이다.

## Goal

- 사람은 자유 형식의 러프 기획서를 작성한다.
- 사람은 아래 템플릿 컨벤션에 맞춰 기획서를 정리해 `ops`에 반영한다.
- PM agent는 문서를 읽고 자의적으로 판단하지 않는다.
- PM agent는 이해되지 않거나 해석이 갈리는 지점만 사용자에게 질의한다.
- PM agent는 확정된 정보를 기준으로 MVP 범위를 정의하고 작업을 분해한다.
- 개발 agent는 개별 task 문서를 기준으로 구현하고 문서 상태를 갱신한다.
- 개발 요청 1회에는 개발 agent의 작업 계획, 구현, 리뷰 agent 요청, 반려 대응, 승인 확보까지 포함된다.
- 리뷰 agent는 최대 2회까지 반려할 수 있으며, 반복 반려 시 병목을 사용자에게 올린다.
- QA agent는 PM이 만든 테스트 시나리오를 수행하고 결과를 문서화한다.
- 버그 수정과 기획 변경은 동일한 사이클로 반복한다.

## Recommended Folder Layout

```text
log-out_ops/
  OPS_WORKFLOW.md
  templates/
    human-input/
      project_brief.template.md
      gameplay_spec.template.md
      scene_flow.template.md
      direction_and_content.template.md
      asset_plan.template.md
    agent-output/
      pm_analysis.template.md
      pm_questions.template.md
      mvp_scope.template.md
      task_board.template.md
      timeline.template.md
      task.template.md
      qa_test_plan.template.md
      qa_result.template.md
      change_request.template.md
  project/
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
      feat-001.md
      feat-002.md
      bug-001.md
      chore-001.md
    qa/
      test-plan-mvp-001.md
      test-result-mvp-001.md
    changes/
      change-001.md
```

## Workflow

### 1. Human Draft

- 사람은 러프 기획서를 작성한다.
- 러프 기획서에는 배경, 핵심 재미, 씬 흐름, 주요 시스템, 사운드/연출 아이디어를 자유롭게 적어도 된다.
- 이후 `templates/human-input/` 템플릿에 맞춰 구조화된 문서로 변환해 `project/`에 넣는다.

### 2. PM Analysis

- PM agent는 `project_brief.md`, `gameplay_spec.md`, `scene_flow.md`를 우선 읽고, 가능하면 `direction_and_content.md`, `asset_plan.md`까지 함께 읽는다.
- PM agent는 문서에 없는 내용을 추론하지 않는다.
- PM agent는 모호한 부분을 `pm_questions.md`에 기록하고 사용자에게 질문한다.
- PM agent는 답변이 오기 전까지 미확정 영역을 `assumption prohibited`로 유지한다.

### 3. MVP Definition

- PM agent는 확정된 기획만 사용해 `mvp_scope.md`를 작성한다.
- MVP에서 구현하지 않는 범위를 반드시 명시한다.
- MVP 범위는 기능, 콘텐츠, 연출, QA 기준까지 포함한다.

### 4. Task Breakdown

- PM agent는 `task_board.md`와 `timeline.md`를 작성한다.
- task ID 규칙은 `feat-001`, `bug-001`, `chore-001`이다.
- 각 task는 독립 문서로 `project/tasks/` 아래에 생성한다.
- 각 task는 선행조건, 병렬 가능 여부, 후속 작업, 완료 조건을 포함해야 한다.

### 5. Development Execution

- 개발 agent는 항상 task 문서 하나를 기준으로 작업한다.
- 개발 agent는 브랜치를 `task-id-english-task-name` 형식으로 만든다.
- 작업 시작 시 상태를 `todo -> in_progress`로 바꾼다.
- 구현과 검증이 끝나면 리뷰 agent에 스스로 리뷰를 요청한다.
- 승인되면 commit과 push까지 완료하고 PR open 준비 상태로 만들고 상태를 `done`으로 바꾼다.
- task 상태 변경과 관련 운영 문서 변경은 `log-out_ops`에도 반영한다.
- `log-out_ops`는 엄격한 브랜치 전략 없이 최신 `main` 기준으로 갱신한다.
- 반려되면 반려 사유만 수정하고 다시 리뷰를 요청한다.
- 같은 task에서 리뷰 반려 루프가 2회를 넘기면 병목을 사용자에게 질의한다.
- 작업 중 발견된 범위 외 요구는 task 문서에 적지 말고 PM으로 되돌린다.

### 6. Review Loop

- 개발 agent는 정해진 commit message 규칙과 PR 요약 규칙을 따른다.
- 개발 agent가 리뷰 agent 호출까지 포함해 end-to-end로 진행한다.
- 리뷰 agent는 최대 2회까지 반려할 수 있다.
- 2회 반려 후에도 승인이 불가능하면 개발 agent가 병목과 선택지를 사용자에게 질의한다.
- 무한 루프 방지를 위해 동일 사유의 반복 반려는 금지한다.

### 7. QA Cycle

- PM agent는 MVP 완료 후 `templates/agent-output/qa_test_plan.template.md` 형식에 맞춰 테스트 시나리오를 만든다.
- QA agent는 실행 결과를 `templates/agent-output/qa_result.template.md` 형식에 맞춰 작성한다.
- 실패 항목은 `bug-*` task로 다시 생성한다.

### 8. Change Requests

- 기획 변경은 기존 문서를 직접 덮어쓰기 전에 `changes/change-xxx.md`로 먼저 남긴다.
- PM agent는 변경 영향 범위를 다시 계산한다.
- 필요 시 Phase 2 MVP 또는 후속 릴리즈 범위를 재정의한다.

## Agent Rules

### PM Agent

- 자의 판단 금지
- 문서 외 정보 추론 금지
- 모호성 발견 시 질문 필수
- 질문 전 작업 범위 확정 금지
- 분석 결과를 task 가능한 수준까지 구체화

### Development Agent

- 지정된 task 범위만 수행
- task 상태 문서 갱신 필수
- 정해진 완료 조건과 검증 기준 충족 필수
- 리뷰 agent 요청 및 반려 대응까지 직접 수행
- 범위 변경 필요 시 PM으로 에스컬레이션

### Review Agent

- 버그, 리스크, 누락 테스트 우선 검토
- 최대 2회 반려 가능
- 2회 이후에는 사용자 질의로 전환

### QA Agent

- 테스트 계획 문서 기준으로만 검증
- 재현 절차와 기대 결과를 분리 기록
- 실패 시 bug task 생성 근거를 남김

## Status Conventions

- `todo`: 아직 시작되지 않음
- `in_progress`: 현재 담당 에이전트가 수행 중
- `blocked`: 외부 답변, 선행 task, 리소스 부족 등으로 중단
- `done`: 완료 조건과 검증 조건까지 충족

## Commit Convention

```text
<task-id> <summary>
```

Examples:

- `feat-001 setup project`
- `bug-003 fix quarantine timer expiration check`
- `chore-002 add mvp smoke test fixtures`

## Branch Naming Convention

```text
<task-id>-<english-task-name>
```

Rules:

- task id는 소문자로 사용한다
- 작업 설명은 영문으로 쓴다
- 공백은 `-`로 치환한다

Examples:

- `feat-001-setup-project`
- `feat-002-build-game-layout`
- `bug-001-fix-dialog-state`

## PR Summary Convention

```text
PR Title
<TASK-ID> <한글 작업명>

PR Description
## Summary
작업 내용 요약

## Changes
어떤 파일에서 어떤 수정 작업을 진행했는지
```

## PR Open Sequence

`pr-open 해줘`는 아래 조건이 충족된 뒤에만 수행한다.

1. task 구현 완료
2. 리뷰 승인 완료
3. commit 완료
4. push 완료

즉, PR open은 개발과 리뷰 루프가 끝난 뒤의 별도 단계다.

## Task Ordering Rules

- 선행조건이 없고 충돌 가능성이 낮은 작업은 병렬 가능으로 표시한다.
- 동일 파일을 크게 수정하는 작업은 병렬 금지로 표시한다.
- UI 기반 task와 데이터/시뮬레이션 task는 가능한 분리한다.
- narrative, audio, fx는 시스템 상태 정의 후 연결한다.

## Human Checklist

- 원본 기획이 `project_brief.md`에 반영되었는가
- 시스템 규칙이 `gameplay_spec.md`에 구조화되었는가
- 씬 흐름이 `scene_flow.md`에 정리되었는가
- PM 질문이 모두 답변되었는가
- MVP 제외 범위가 명시되었는가
- 각 task의 완료 조건이 테스트 가능하게 적혀 있는가
- QA 실패 사항이 bug task로 환원되었는가
