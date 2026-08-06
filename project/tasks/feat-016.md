# feat-016 Improve Hermes file explorer interaction fidelity

## Status

- status: todo
- type: feat
- priority: 20
- owner agent: dev-agent
- branch: `feat-016-improve-hermes-file-explorer-interaction-fidelity`
- commit message: `feat-016 improve hermes file explorer interaction fidelity`

## Goal

Make Hermes OS file investigation closer to the original ship-computer fantasy.

## Scope

- Add path bar, search field, directory tree/nav, and file metadata panel.
- Separate single-click select from double-click open where feasible.
- Add context-menu style actions: attach to ECHO, copy path, open with recovery tool.
- Improve locked, corrupted, recovered, executable, image, and folder states.
- Add viewer support or placeholder rendering for `sensor_diagram.png`.

## Dependencies

- before: `feat-002`, `feat-011`
- after: `feat-017`, `qa-002`

## Acceptance Criteria

- [ ] Player can understand file path, file type, and file state before opening.
- [ ] Evidence attachment feels like an OS action, not just a puzzle button.
- [ ] Corrupted and recovered files are visually distinct.
- [ ] `sensor_diagram.png` has a viewer path or graceful placeholder.
- [ ] Existing evidence progression remains compatible.

## Source References

- `project/human-input/LOG_OUT 로그파일 구조.md`
- `project/human-input/LOG_OUT 로그 예시.md`
- `project/human-input/LOG_OUT visual 기획서.md`

## Asset Inputs

- `public/assets/images/sensor_diagram.png`
- `public/assets/images/ui/file-icons/*.svg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
