# feat-007 Implement external AI ECHO rules for category A

## Status

- status: blocked
- blocked by: Q11 in `project/pm_questions.md`
- type: feat
- priority: 9
- owner agent: dev-agent
- branch: `feat-007-implement-external-ai-echo-rules-category-a`
- commit message: `feat-007 implement external ai echo rules category a`

## Goal

Implement ECHO responses and verdicts for the category A MVP scenario using an external AI/API integration.

## Scope

- Integrate the human-confirmed external AI/API provider.
- Respond to correct and incorrect evidence submissions.
- Use Act-specific ECHO messages.
- Reflect old evidence resubmission behavior.
- Trigger door unlock or ending-ready state after Act 3 success.
- Support free-text hint conversation.
- Include file context tags such as `@{로그파일명}` in the AI request context.
- Define strict response schema for act verdict, assistant message, resource penalty, and unlock state.
- Add validation guard so AI output cannot unlock the door before Act 3 requirements are satisfied.

## Dependencies

- before: `feat-003`, `feat-005`, `feat-006`, Q11
- after: `qa-001`

## Acceptance Criteria

- ECHO uses the human-confirmed external AI/API provider and auth contract.
- ECHO response content follows planning docs and confirmed Act 3 evidence.
- Door unlock is not triggered before final confirmed Act completion.
- Incorrect submissions provide feedback without leaking full answers unless specified.
- Category A MVP Act 3 uses `ai_priority_matrix.json` + `deleted_override.txt`.
- API key is never exposed directly to the browser if Q11 confirms a server route.
- Invalid AI response schema fails safely without advancing the Act.
