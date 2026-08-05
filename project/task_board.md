# Task Board

## Document Meta

- version: 0.3
- pm agent: codex
- date: 2026-08-05
- status: confirmed - pending AI/API provider detail

## Task Index

| priority | task id | type | title | status | owner agent | parallelizable | depends on | blocks | doc path |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | feat-001 | feat | Bootstrap Vite + React game project | done | dev-agent | no | none | feat-002, feat-003, feat-004, feat-009 | project/tasks/feat-001.md |
| 2 | feat-002 | feat | Build Hermes OS terminal shell | done | dev-agent | yes | feat-001 | feat-005, feat-006, feat-008 | project/tasks/feat-002.md |
| 3 | feat-003 | feat | Implement oxygen and power game state | done | dev-agent | yes | feat-001 | feat-005, feat-007, qa-001 | project/tasks/feat-003.md |
| 4 | feat-004 | feat | Build category A file system data | done | dev-agent | yes | feat-001 | feat-005, feat-006, feat-007 | project/tasks/feat-004.md |
| 5 | chore-001 | chore | Align content fixtures with planning docs | done | dev-agent | yes | feat-004 | feat-005, feat-007 | project/tasks/chore-001.md |
| 6 | feat-009 | feat | Build R3F spaceship computer scene | done | dev-agent | yes | feat-001 | feat-008 | project/tasks/feat-009.md |
| 7 | feat-005 | feat | Implement evidence attachment and act progression | done | dev-agent | no | feat-002, feat-003, feat-004 | feat-007, feat-008 | project/tasks/feat-005.md |
| 8 | feat-006 | feat | Implement Log Fixer recovery interaction | done | dev-agent | yes | feat-002, feat-004 | feat-007 | project/tasks/feat-006.md |
| 9 | feat-007 | feat | Implement external AI ECHO rules for category A | blocked | dev-agent | no | feat-003, feat-005, feat-006, Q11 | qa-001 | project/tasks/feat-007.md |
| 10 | feat-008 | feat | Add opening, ending, visual, and audio feedback | done | dev-agent | yes | feat-002, feat-003, feat-009 | qa-001 | project/tasks/feat-008.md |
| 11 | qa-001 | chore | Run MVP scenario QA and create bug tickets | blocked | qa-agent | no | feat-003, feat-007, feat-008 | bug tasks | project/tasks/qa-001.md |

## Parallel Work Notes

- `feat-002`, `feat-003`, `feat-004`, and `feat-009` can start after `feat-001` because they touch different layers: UI shell, game state, content data, and 3D scene.
- `chore-001` can run alongside implementation once `feat-004` defines the file data shape.
- `feat-006` can proceed before final ECHO wording if the recovery interaction contract is stable.
- `feat-007` requires the new Q11 API detail before final implementation.
- PM task docs are the implementation source of truth when older human-input examples conflict with answered PM questions.

## Sequencing Notes

- Do not let dev agent decide unresolved planning conflicts independently.
- If a task depends on a question ID, PM must update `pm_questions.md` and this board after the human answer.
- Every dev task must update its task md status from `todo` to `in_progress` to `done`.
- Every dev task must follow branch, commit, review, push, and PR rules from the agent guides.
