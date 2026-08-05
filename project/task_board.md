# Task Board

## Document Meta

- version: 0.4
- pm agent: codex
- date: 2026-08-05
- status: pre-AI MVP reinforcement plan confirmed

## Task Index

| priority | task id | type | title | status | owner agent | parallelizable | depends on | blocks | doc path |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | feat-001 | feat | Bootstrap Vite + React game project | done | dev-agent | no | none | feat-002, feat-003, feat-004, feat-009 | project/tasks/feat-001.md |
| 2 | feat-002 | feat | Build Hermes OS terminal shell | done | dev-agent | yes | feat-001 | feat-005, feat-006, feat-008 | project/tasks/feat-002.md |
| 3 | feat-003 | feat | Implement oxygen and power game state | done | dev-agent | yes | feat-001 | feat-005, qa-001, phase 2 feat-007 | project/tasks/feat-003.md |
| 4 | feat-004 | feat | Build category A file system data | done | dev-agent | yes | feat-001 | feat-005, feat-006, phase 2 feat-007 | project/tasks/feat-004.md |
| 5 | chore-001 | chore | Align content fixtures with planning docs | done | dev-agent | yes | feat-004 | feat-005, chore-002, phase 2 feat-007 | project/tasks/chore-001.md |
| 6 | feat-009 | feat | Build R3F spaceship computer scene | done | dev-agent | yes | feat-001 | feat-008 | project/tasks/feat-009.md |
| 7 | feat-005 | feat | Implement evidence attachment and act progression | done | dev-agent | no | feat-002, feat-003, feat-004 | feat-011, qa-001, phase 2 feat-007 | project/tasks/feat-005.md |
| 8 | feat-006 | feat | Implement Log Fixer recovery interaction | done | dev-agent | yes | feat-002, feat-004 | feat-011, qa-001, phase 2 feat-007 | project/tasks/feat-006.md |
| 9 | feat-010 | feat | Implement intro narrative sequence | done | dev-agent | no | feat-008 | qa-001 | project/tasks/feat-010.md |
| 10 | chore-002 | chore | Enrich MVP internal file contents | done | dev-agent | yes | chore-001, feat-005, feat-006 | qa-001 | project/tasks/chore-002.md |
| 11 | feat-011 | feat | Improve MVP player guidance and UX guardrails | done | dev-agent | yes | feat-005, feat-006, feat-008 | qa-001 | project/tasks/feat-011.md |
| 12 | qa-001 | chore | Run MVP scenario QA and create bug tickets | done | qa-agent | no | feat-003, feat-005, feat-006, feat-008, feat-010, chore-002, feat-011 | bug-001, bug-002 | project/tasks/qa-001.md |
| 13 | bug-001 | bug | Connect oxygen timer to active gameplay session | done | dev-agent | no | qa-001, feat-003 | MVP human review | project/tasks/bug-001.md |
| 14 | bug-002 | bug | Enforce blackout interaction lock in gameplay UI | done | dev-agent | no | qa-001, feat-003, feat-008 | MVP human review | project/tasks/bug-002.md |
| 15 | feat-007 | feat | Implement external AI ECHO rules for category A | deferred | dev-agent | no | Q11, pre-AI MVP QA | phase 2 AI work | project/tasks/feat-007.md |

## Parallel Work Notes

- `feat-002`, `feat-003`, `feat-004`, and `feat-009` can start after `feat-001` because they touch different layers: UI shell, game state, content data, and 3D scene.
- `chore-001` can run alongside implementation once `feat-004` defines the file data shape.
- `feat-006` can proceed before final ECHO wording if the recovery interaction contract is stable.
- `feat-007` is deferred to phase 2 because deterministic local ECHO rules are enough to validate the current MVP loop.
- `feat-010`, `chore-002`, and `feat-011` are pre-AI MVP reinforcement tasks that improve comprehension, content density, and playability.
- PM task docs are the implementation source of truth when older human-input examples conflict with answered PM questions.

## Sequencing Notes

- Do not let dev agent decide unresolved planning conflicts independently.
- If a task depends on a question ID, PM must update `pm_questions.md` and this board after the human answer.
- QA can run before `feat-007` as long as it tests deterministic ECHO behavior rather than external AI behavior.
- Every dev task must update its task md status from `todo` to `in_progress` to `done`.
- Every dev task must follow branch, commit, review, push, and PR rules from the agent guides.
