# feat-005 Implement evidence attachment and act progression

## Status

- status: todo
- type: feat
- priority: 7
- owner agent: dev-agent
- branch: `feat-005-implement-evidence-attachment-and-act-progression`
- commit message: `feat-005 implement evidence attachment and act progression`

## Goal

Allow the player to attach evidence files, submit them to ECHO, and progress through Act 1, Act 2, and Act 3.

## Scope

- Select or attach evidence files from the file explorer.
- Clicking a file injects a removable `@{로그파일명}` context tag into the ECHO input.
- Submit evidence with optional text input.
- Validate evidence against current Act.
- Move from Act 1 to Act 2 to Act 3 to ending-ready state.
- Penalize incorrect submissions through the resource state from `feat-003`.
- Preserve selected file context so `feat-007` can send it to the external AI/API.

## Act Progression Contract

| act | required evidence | required text intent |
| --- | --- | --- |
| Act 1 | `sensor_calib.log` | sensor error, calibration error, or 186-day uncalibrated explanation |
| Act 2 | recovered `quarantine_rules.conf` | 72-hour rule expired through `+17,520시간` offset calculation |
| Act 3 | `ai_priority_matrix.json` + `deleted_override.txt` | ECHO priority/override contradiction |

## Dependencies

- before: `feat-002`, `feat-003`, `feat-004`
- after: `feat-007`, `feat-008`

## Acceptance Criteria

- Correct Act evidence advances the game.
- Incorrect evidence does not advance the game and applies penalty.
- File click creates a visible removable `@{로그파일명}` tag in the input.
- Evidence submission payload includes text, tagged file ids, current act, and resource state.
- Act 3 evidence uses `ai_priority_matrix.json` + `deleted_override.txt`.
- Dev agent must not use the `auxiliary_capacitor.log` + `emergency_grid_switch.conf` pair for category A MVP Act 3.
