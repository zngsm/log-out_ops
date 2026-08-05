# feat-002 Build Hermes OS terminal shell

## Status

- status: done
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

- [x] App renders a recognizable Hermes OS game interface.
- [x] Layout works on desktop and remains usable on smaller screens.
- [x] UI areas are clearly separated for explorer, viewer, chat, and HUD.
- [x] No final gameplay logic or R3F scene work is required in this task.

## Validation

- `npm run build`: pass
- Build output confirmed: `dist/index.html`, `dist/assets/index-BAjvl8N0.css`, `dist/assets/index-CcaR_iP-.js`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | Hermes OS terminal shell implementation started |
| 2026-08-05 | review-agent | review approved | no blocking findings; scope limited to 2D shell placeholders |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for `feat-002` shell scope | closed |

## Deliverables

- code changes: `src/App.tsx`, `src/styles.css`
- branch: `feat-002-build-hermes-os-terminal-shell`
- commit: `bd0d49e`
- tests: `npm run build`

## PR Draft

- pr title: FEAT-002 Hermes OS 터미널 셸 구현
- pr description:
  - `## Summary`
  - Hermes OS 기반 파일 탐색기, 파일 뷰어, ECHO 채팅, 산소/전력 HUD가 분리된 기본 게임 UI 셸을 구현함
  - `## Changes`
  - `src/App.tsx`: 정적 파일 트리, 로그 뷰어, ECHO 메시지, 입력 placeholder를 포함한 Hermes OS 구조 추가
  - `src/styles.css`: responsive terminal layout, HUD card, explorer/viewer/chat panel 스타일 추가
