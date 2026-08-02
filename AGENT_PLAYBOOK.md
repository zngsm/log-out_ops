# Agent Playbook

이 문서는 `log-out_ops`와 `log-out`을 함께 운용할 때 각 에이전트가 기본적으로 따라야 하는 역할, 입력 문서, 출력 문서, 금지사항을 정의한다.

목표는 매번 긴 요청문을 쓰지 않아도, 에이전트가 자신의 역할 문서를 기준으로 일하게 만드는 것이다.

## Core Principle

- 운영 문서는 `log-out_ops`에서 관리한다.
- 실제 코드는 `log-out`에서 수정한다.
- 모든 에이전트는 먼저 관련 문서를 읽고, 그다음 행동한다.
- PM agent를 제외한 다른 에이전트는 기획 해석을 새로 하지 않는다.
- 문서에 없는 내용을 자의적으로 확정하지 않는다.

## Recommended Usage

짧은 요청 예시:

```text
pm agent, 기획서 분석해줘
```

```text
dev agent feat-001 작업해줘
```

```text
pm agent, 테스트 시나리오 작성해줘
```

```text
qa agent 테스트 해줘
```

```text
pr-open 해줘
```

## Folder Contract

```text
log-out_ops/
  AGENT_PLAYBOOK.md
  agents/
    PM_AGENT.md
    DEV_AGENT.md
    REVIEW_AGENT.md
    QA_AGENT.md
  project/
    ...

log-out/
  actual code repository
```

## Global Rules For All Agents

- 먼저 `log-out_ops/project/`의 관련 문서를 읽는다.
- 작업 대상이 코드면 `log-out`에서 작업한다.
- 작업 대상이 운영 문서면 `log-out_ops`에서 작업한다.
- 작업 시작 전 어떤 문서를 기준으로 삼았는지 명시한다.
- 작업 완료 후 어떤 문서를 갱신했는지 남긴다.
- 애매한 요구를 임의 해석하지 않는다.
- DEV agent는 task별 브랜치를 `feat-001-setup-project` 형식으로 사용한다.

## Agent Sequence

1. Human writes or updates planning docs in `log-out_ops/project/`
2. PM agent analyzes and asks questions
3. PM agent defines MVP and creates tasks
4. DEV agent executes one task in `log-out`
5. DEV agent requests REVIEW agent review and addresses feedback if needed
6. After approval, DEV agent commits and pushes the task branch
7. If requested, DEV agent opens PR using the approved task state
8. If review loops exceed 2 rejections, DEV agent escalates to human
9. PM agent prepares QA plan
10. QA agent runs tests
11. PM agent turns failures into bug tasks
12. Repeat until MVP is complete

## Short Command Pattern

실제 운영에서는 아래 정도로만 요청해도 되도록 한다.

### PM

```text
pm agent, 기획서 분석해줘
```

### DEV

```text
dev agent feat-001 작업해줘
```

### PM Test

```text
pm agent, 테스트 시나리오 작성해줘
```

### QA

```text
qa agent 테스트 해줘
```

### PR

```text
pr-open 해줘
```

## When Humans Should Intervene

- PM agent가 `pm_questions.md`에 질문을 남겼을 때
- DEV agent가 리뷰 루프 2회 초과 병목을 보고했을 때
- QA 결과에서 우선순위 충돌이나 기획 수정 필요성이 생겼을 때
- 범위 변경이 필요해 `changes/change-xxx.md`가 생성되었을 때

## Source Of Truth

- 기획의 진실: `log-out_ops/project/*.md`
- 작업 상태의 진실: `log-out_ops/project/task_board.md`와 `project/tasks/*.md`
- 구현의 진실: `log-out/`
- 테스트 결과의 진실: `log-out_ops/project/qa/*.md`
- PR 제목/본문의 진실: 현재 `done` + `approved` 상태의 task 문서
