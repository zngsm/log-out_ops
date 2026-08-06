# feat-020 Add directed Ending A and result panel

## Status

- status: todo
- type: feat
- priority: 25
- owner agent: dev-agent
- branch: `feat-020-add-directed-ending-a-and-result-panel`
- commit message: `feat-020 add directed ending a and result panel`

## Goal

Replace the minimal ending-ready state with a directed Normal Ending A sequence that resolves the quarantine confrontation.

## Scope

- After Act 3 success, play ECHO's final review mode for about 5 seconds.
- Unlock the door with visible/audible feedback.
- Show the physical door release using the DOCX door/control-room reference where available.
- Show Normal Ending A result panel with survival state and summary.
- Keep Ending B/C out of scope for current phase.
- Leave hooks for seed/result sharing later without implementing full sharing.

## Dependencies

- before: `feat-013`, `feat-014`, `feat-018`, `feat-019`
- after: `qa-002`

## Acceptance Criteria

- [ ] Act 3 success does not jump instantly to completion.
- [ ] Door release is represented as a scene beat.
- [ ] Door release is visible in the 3D room or a faithful placeholder, not only described by text.
- [ ] Result panel clearly says Normal Ending A was achieved.
- [ ] Failure and blackout states remain distinct from Normal Ending A.
- [ ] The ending sequence is testable without external AI.

## Source References

- `project/human-input/LOG_OUT 기획서.md`
- `project/human-input/LOG_OUT visual 기획서.md`
- `project/human-input/LOG_OUT visual 복사본.docx`
- `project/phase_2_original_source_replan.md`
- `project/docx_source_reassessment.md`

## Asset Inputs

- `public/assets/audio/sfx_door_lock_clunk.ogg`
- `public/assets/audio/sfx_success_chime.ogg`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
