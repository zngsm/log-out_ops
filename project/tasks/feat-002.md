# feat-002 Build Hermes OS terminal shell

## Status

- status: todo
- type: feat
- priority: 2
- owner agent: dev-agent
- branch: `feat-002-build-hermes-os-terminal-shell`
- commit message: `feat-002 build hermes os terminal shell`

## Goal

Create the base in-game Hermes OS screen that can host file exploration, file viewing, ECHO chat, and resource HUD.

## Scope

- Build responsive game shell layout.
- Add file explorer panel placeholder.
- Add file viewer panel placeholder.
- Add ECHO chat panel placeholder.
- Add oxygen and power HUD placeholder.
- Keep the Hermes OS as a 2D interface that can later be embedded into the R3F computer scene from `feat-009`.

## Dependencies

- before: `feat-001`
- after: `feat-005`, `feat-006`, `feat-008`

## Acceptance Criteria

- App renders a recognizable Hermes OS game interface.
- Layout works on desktop and remains usable on smaller screens.
- UI areas are clearly separated for explorer, viewer, chat, and HUD.
- No final gameplay logic or R3F scene work is required in this task.
