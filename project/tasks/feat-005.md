# feat-005 Implement evidence attachment and act progression

## Status

- status: blocked
- blocked by: Q4 in `project/pm_questions.md`
- type: feat
- priority: 6
- owner agent: dev-agent
- branch: `feat-005-implement-evidence-attachment-and-act-progression`
- commit message: `feat-005 implement evidence attachment and act progression`

## Goal

Allow the player to attach evidence files, submit them to ECHO, and progress through Act 1, Act 2, and Act 3.

## Scope

- Select or attach evidence files from the file explorer.
- Submit evidence with optional text input.
- Validate evidence against current Act.
- Move from Act 1 to Act 2 to Act 3 to ending-ready state.
- Penalize incorrect submissions through the resource state from `feat-003`.

## Dependencies

- before: `feat-002`, `feat-003`, `feat-004`, Q4
- after: `feat-007`, `feat-008`

## Acceptance Criteria

- Correct Act evidence advances the game.
- Incorrect evidence does not advance the game and applies penalty.
- Act 3 evidence follows the human-confirmed answer to Q4.
- Dev agent does not choose between conflicting Act 3 evidence docs independently.
