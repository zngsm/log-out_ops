# feat-026 Reframe gameplay UI as fixed computer terminal screen

## Status

- status: done
- type: feat
- priority: 41
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-026 reframe gameplay ui as fixed computer terminal screen`

## Goal

Make the gameplay screen feel like a fixed in-world computer terminal instead of a scrollable web page with many floating panels.

## Scope

- Lock the gameplay viewport so the page itself does not scroll on desktop.
- Keep the terminal screen full-viewport and fixed after monitor zoom-in.
- Use a three-column terminal layout:
  - left: file path tree and files
  - center: selected file content
  - right: ECHO conversation and evidence submission
- Allow only internal panels to scroll when content is long.
- Move resource/state information into a compact external overlay that does not push the terminal layout.
- Hide guide/debug-like HUD cards from the normal gameplay layout.

## Dependencies

- before: `feat-025`
- after: human visual review

## Acceptance Criteria

- [x] Desktop gameplay does not scroll the whole page.
- [x] File tree, file viewer, and ECHO chat scroll internally.
- [x] Terminal work area is visually dominant and fills the computer screen.
- [x] Resource HUD is compact and visually separate from the terminal work area.
- [x] Scene/objective/recovery helper cards no longer appear as extra gameplay windows.
- [x] Mobile still has a usable vertical fallback.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Implementation Notes

- Changed `terminal-screen-surface` to a fixed 100vh terminal surface on desktop.
- Converted the terminal layout into a flex/fixed viewport where only child panels scroll.
- Reworked HUD cards into a compact bottom-right overlay.
- Hid scene runtime, objective, alert, and recovery helper HUD cards from normal gameplay.
- Preserved mobile fallback by allowing the page to scroll below 760px width.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-026 reframe gameplay ui as fixed computer terminal screen`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-09 | dev-agent | todo -> in_progress | Started terminal-screen layout correction from human visual feedback |
| 2026-08-09 | dev-agent | in_progress -> done | Fixed desktop viewport, internal scrolling, and compact external HUD |

## Change-001 Impact Note

- Gameplay UI flow is updated to enter Company Intranet first, followed by split desktop/ECHO work UI during the 5-minute Rapport Phase, before shifting to the Category A puzzle terminal layout upon ECHO reboot.
- Follow-up implementation defined in `feat-032`, `feat-033`, `feat-034`.


