# feat-007 Implement ECHO response rules for category A

## Status

- status: blocked
- blocked by: Q4 and Q5 in `project/pm_questions.md`
- type: feat
- priority: 8
- owner agent: dev-agent
- branch: `feat-007-implement-echo-response-rules-category-a`
- commit message: `feat-007 implement echo response rules category a`

## Goal

Implement ECHO responses and verdicts for the category A MVP scenario.

## Scope

- Respond to correct and incorrect evidence submissions.
- Use Act-specific ECHO messages.
- Reflect old evidence resubmission behavior.
- Trigger door unlock or ending-ready state after Act 3 success.

## Dependencies

- before: `feat-003`, `feat-005`, `feat-006`, Q4, Q5
- after: `qa-001`

## Acceptance Criteria

- ECHO response rules are deterministic if Q5 confirms local rules.
- ECHO response content follows planning docs and confirmed Act 3 evidence.
- Door unlock is not triggered before final confirmed Act completion.
- Incorrect submissions provide feedback without leaking full answers unless specified.
