# feat-005 Implement evidence attachment and act progression

## Status

- status: todo
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

- before: `feat-002`, `feat-003`, `feat-004`
- after: `feat-007`, `feat-008`

## Acceptance Criteria

- Correct Act evidence advances the game.
- Incorrect evidence does not advance the game and applies penalty.
- Act 3 evidence uses `ai_priority_matrix.json` + `deleted_override.txt`.
- Dev agent must not use the `auxiliary_capacitor.log` + `emergency_grid_switch.conf` pair for category A MVP Act 3.
