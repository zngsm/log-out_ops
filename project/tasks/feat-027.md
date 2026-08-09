# feat-027 Move gameplay HUD into title status bar

## Status

- status: done
- type: feat
- priority: 42
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-027 move gameplay hud into title status bar`

## Goal

Prevent gameplay HUD cards such as Audio System and Power Grid from covering the terminal work area, completely removing `ECHO STATE / monitoring` card and `ACT-1 100%` (`mission-clock`) block from the top title status bar (Q25, Q28).

## Scope

- Move visible HUD cards from the lower overlay position to the top title/status area.
- Keep the HUD compact enough to read as status chips beside `LOG_OUT`.
- Completely remove the `ACT-1 100%` (`mission-clock`) status bar block (Q28 user feedback).
- Remove bottom padding previously reserved for the lower HUD overlay.
- Preserve mobile fallback behavior.

## Dependencies

- before: `feat-026`
- after: human visual review

## Acceptance Criteria

- [x] HUD no longer covers the lower terminal/file/chat area on desktop.
- [x] Oxygen, power, timer, and audio status appear as compact top status chips (`ECHO STATE / monitoring` card and `ACT-1 100%` block completely removed).
- [x] `LOG_OUT` title remains visible.
- [x] Terminal work area keeps full vertical space for file tree, file viewer, and ECHO chat.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-027 move gameplay hud into title status bar`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-09 | dev-agent | todo -> in_progress | Started HUD relocation from human visual feedback |
| 2026-08-09 | dev-agent | in_progress -> done | Moved compact HUD chips to the top title/status bar area |

