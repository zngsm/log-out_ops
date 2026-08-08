# feat-024 Rebuild opening-to-terminal flow from visual DOCX

## Status

- status: todo
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

- [ ] Initial screen reads as a spaceship control room with a computer, not an OS dashboard.
- [ ] Computer/monitor click starts the entry flow.
- [ ] The terminal appears to expand from inside the monitor frame.
- [ ] Opening beats follow the DOCX 00:00~01:00 sequence, compressed only if debug speed is active.
- [ ] Gameplay starts only after the terminal handoff beat.
- [ ] The layout remains usable on desktop and mobile widths.
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/docx_content_conversion_plan.md`

