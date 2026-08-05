# chore-002 Enrich MVP internal file contents

## Status

- status: todo
- type: chore
- priority: 10
- owner agent: dev-agent
- branch: `chore-002-enrich-mvp-internal-file-contents`
- commit message: `chore-002 enrich mvp internal file contents`

## Goal

Fill the MVP Hermes OS file contents with enough readable in-world text for the player to feel like they are investigating a real ship system, while preserving the existing deterministic Act progression contract.

## Scope

- Expand Category A file contents using `project/human-input/LOG_OUT 로그 예시.md`.
- Use `project/human-input/LOG_OUT 로그파일 구조.md` to add useful decoy/flavor files where they improve exploration density.
- Keep required evidence files and ids unchanged unless PM explicitly approves a contract change.
- Preserve Act 3 MVP truth: `ai_priority_matrix.json` + `deleted_override.txt`.
- Add source references or comments when content is derived from human-input docs.
- Do not add other category scenarios to MVP.

## Dependencies

- before: `chore-001`, `feat-005`, `feat-006`
- after: `qa-001`

## Acceptance Criteria

- Each required evidence file contains enough text for a human player to infer why it matters.
- At least a small number of non-critical flavor/decoy files make the file system feel populated.
- Evidence keywords used by deterministic validation still appear in the relevant files or player-facing clues.
- No old Act 3 evidence pair is reintroduced as category A MVP truth.
- Content remains readable inside the current file viewer UI.
