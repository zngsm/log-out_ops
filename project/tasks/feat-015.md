# feat-015 Add resource pressure HUD and threshold effects

## Status

- status: todo
- type: feat
- priority: 19
- owner agent: dev-agent
- branch: `feat-015-add-resource-pressure-hud-and-threshold-effects`
- commit message: `feat-015 add resource pressure hud and threshold effects`

## Goal

Make oxygen and power feel like emergency pressure, not only numbers.

## Scope

- Display O2 level, drain multiplier, power level, and elapsed/session time in the planned HUD style.
- Apply power thresholds: Normal, Caution, Warning, Critical, Blackout.
- Match the DOCX crisis monitor direction: red alert status, strong monitor glow, oxygen/power bars, and surrounding-room warning signage or placeholder equivalents.
- Add Caution file/viewer delay, Warning Log_Fixer slowdown, Critical vignette/cursor shake, and Blackout reboot lock.
- On wrong submission, show a clear power surge moment with ECHO warning copy.
- Keep debug timer and normal 60-minute mode separated.

## Dependencies

- before: `feat-003`, `bug-001`, `bug-002`
- after: `feat-018`, `feat-019`, `qa-002`

## Acceptance Criteria

- [ ] HUD shows O2 percentage and current drain multiplier.
- [ ] Red Alert/Critical presentation affects both monitor UI and surrounding scene treatment when available.
- [ ] Power threshold changes affect visuals and at least one interaction timing behavior.
- [ ] Blackout includes a timed reboot sequence before power recovery.
- [ ] Wrong evidence penalty feels like a ship-system event.
- [ ] Resource behavior remains deterministic and testable.

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/phase_2_original_source_replan.md`
- `project/docx_source_reassessment.md`

## Asset Inputs

- `public/assets/images/fx/glitch-noise.webp`
- `public/assets/images/fx/red-vignette.webp`
- `public/assets/audio/sfx_wrong_surge.ogg`
- `public/assets/audio/sfx_blackout_clunk.ogg`
- `public/assets/audio/sfx_reboot.ogg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
