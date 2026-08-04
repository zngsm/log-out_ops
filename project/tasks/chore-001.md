# chore-001 Align content fixtures with planning docs

## Status

- status: todo
- type: chore
- priority: 5
- owner agent: dev-agent
- branch: `chore-001-align-content-fixtures-with-planning-docs`
- commit message: `chore-001 align content fixtures with planning docs`

## Goal

Keep implementation fixtures aligned with PM-confirmed planning docs so content does not drift from the game design.

## Scope

- Add comments or metadata that map game files to planning sources.
- Normalize naming for file ids, paths, act ids, and evidence ids.
- Update docs if implementation discovers missing content fields.

## Dependencies

- before: `feat-004`
- after: `feat-005`, `feat-007`

## Acceptance Criteria

- Content fixtures have consistent naming and source references.
- Any unresolved ambiguity is recorded in ops docs instead of guessed in code.
- No player-facing behavior changes are required unless needed for fixture consistency.
