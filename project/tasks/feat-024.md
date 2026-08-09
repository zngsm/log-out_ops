# feat-024 Rebuild opening-to-terminal flow from visual DOCX

## Status

- status: done
- type: feat
- priority: 37
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-024 rebuild opening to terminal flow from visual docx`

## Goal

Make the initial experience match the intended visual structure: visible control room and computer, sudden ECHO lockdown, computer click/approach, zoom into monitor, then Hermes OS gameplay.

## Scope

- Use `LOG_OUT visual 복사본.docx` as the visual flow source.
- Start with a 3D/CSS control-room composition where the computer monitor is physically visible.
- Let the player click the computer/monitor to enter the terminal approach.
- Avoid showing full Hermes OS as a disconnected full-page web layout before the monitor zoom completes.
- Align zoom crop/origin with the monitor frame.
- Opening sequence must depict:
  - normal work state
  - red alert
  - door lockdown
  - crew message interruption
  - ECHO quarantine declaration
  - O2/Power HUD activation
  - terminal focus view

## Dependencies

- before: `bug-009`
- after: `qa-003`

## Acceptance Criteria

- [x] Initial screen reads as a spaceship control room with a computer, not an OS dashboard.
- [x] Computer/monitor click starts the entry flow.
- [x] The terminal appears to expand from inside the monitor frame.
- [x] Opening beats follow the DOCX 00:00~01:00 sequence, compressed only if debug speed is active.
- [x] Gameplay starts only after the terminal handoff beat.
- [x] The layout remains usable on desktop and mobile widths.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Implementation Notes

- Reframed the initial overlay as a normal control-room standby state rather than an already-active lockdown state.
- The computer hotspot now communicates monitor approach first, with ECHO lockdown reserved for the opening cutscene beats.
- Added clearer first-person control-room/footer copy explaining the physical computer -> monitor zoom -> Hermes OS flow.
- Added a secondary monitor reticle around the computer hotspot to make the clickable physical monitor target more legible.
- Existing terminal surface animation from bug-008 remains the monitor-frame zoom handoff.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-024 rebuild opening to terminal flow from visual docx`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-08 | dev-agent | todo -> in_progress | Started visual DOCX opening-to-terminal flow cleanup after feat-023 |
| 2026-08-08 | dev-agent | in_progress -> done | Reframed initial room state and clarified physical monitor approach |

## Change-001 Impact Note

- Smooth Zoom-in transition from main menu to terminal monitor is updated to expand to 100% Full Screen (removing 90% aspect border).
- Entry flow is updated to insert Company Intranet screen & [출근] button, followed by a 5-minute Rapport Phase before ECHO reboot and lockdown.
- Follow-up implementation defined in `feat-031`, `feat-032`, `feat-033`, `feat-034`.


## Source References

- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/docx_content_conversion_plan.md`
