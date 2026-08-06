# feat-020 Add directed Ending A and result panel

## Status

- status: done
- type: feat
- priority: 25
- owner agent: dev-agent
- branch: `main`
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

- [x] Act 3 success does not jump instantly to completion.
- [x] Door release is represented as a scene beat.
- [x] Door release is visible in the 3D room or a faithful placeholder, not only described by text.
- [x] Result panel clearly says Normal Ending A was achieved.
- [x] Failure and blackout states remain distinct from Normal Ending A.
- [x] The ending sequence is testable without external AI.

## Implementation Notes

- Act 3 success now enters a 5-second `FINAL_REVIEW` overlay with input locked.
- The final review overlay summarizes the three contradiction axes: sensor, quarantine, and override.
- Door release triggers scene runtime transition, visible released door state through feat-019 props, door clunk cue, success cue, and ECHO/SYSTEM log messages.
- Normal Ending A now has a structured result panel with survival state, ending type, and a seed-sharing placeholder hook.
- Ending B/C remain explicitly out of scope for this phase.

## Validation

- `npm run build` passed.
- `git diff --check` passed.
- Review-agent pass completed within the dev-agent workflow.

## Delivery

- code repo commit: `28ee506 feat-020 add directed ending a and result panel`
- code repo target: `main`

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
| 2026-08-06 | dev-agent | todo -> in_progress | Directed Ending A implementation started after feat-019 main push |
| 2026-08-06 | review-agent | in_progress -> approved | Build and diff checks passed; ending flow remains deterministic and scoped to Normal Ending A |
| 2026-08-06 | dev-agent | approved -> done | Pushed code commit `28ee506` to `log-out/main` |
