# feat-006 Implement Log Fixer recovery interaction

## Status

- status: todo
- type: feat
- priority: 7
- owner agent: dev-agent
- branch: `feat-006-implement-log-fixer-recovery-interaction`
- commit message: `feat-006 implement log fixer recovery interaction`

## Goal

Implement the MVP file recovery interaction needed to access restored security or rule content.

## Scope

- Represent corrupted or locked files in the file system.
- Add a `Log_Fixer.exe` style interaction.
- Change file state from corrupted to recovered when the player completes the action.
- Surface recovered content in the file viewer.

## Dependencies

- before: `feat-002`, `feat-004`
- after: `feat-007`

## Acceptance Criteria

- Recoverable files are visually distinguishable.
- Recovery interaction changes file state.
- Recovered files can be submitted as evidence where relevant.
- Recovery action does not require final animation or sound asset.
