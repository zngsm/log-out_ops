# chore-003 Rewrite Category A content into diegetic clue layer

## Status

- status: todo
- type: chore
- priority: 22
- owner agent: dev-agent
- branch: `chore-003-rewrite-category-a-content-into-diegetic-clue-layer`
- commit message: `chore-003 rewrite category a content into diegetic clue layer`

## Goal

Align Category A file contents with the original LOG_OUT examples while separating production clues from debug/hint notes.

## Scope

- Re-check all Category A files against `LOG_OUT 로그 예시.md`.
- Keep exact canonical evidence paths for Act 1, Act 2, and Act 3.
- Add or preserve original decoy/flavor files where they improve investigation density.
- Move `[PLAYER NOTE]` or direct-answer text behind a debug/hint layer.
- Keep diegetic logs readable and inferable without giving direct instructions.
- Keep deterministic keyword validation compatible with rewritten content.

## Dependencies

- before: `feat-004`, `chore-002`
- after: `qa-002`

## Acceptance Criteria

- [ ] Required evidence files contain original-source clue information.
- [ ] Production file contents do not directly say "this is the answer."
- [ ] Debug/hint information is still available for QA or accessibility if enabled.
- [ ] Decoy files feel plausible and do not accidentally satisfy evidence validation.
- [ ] Act 3 remains `ai_priority_matrix.json` + `deleted_override.txt`.

## Source References

- `project/human-input/LOG_OUT 로그 예시.md`
- `project/human-input/LOG_OUT 로그파일 구조.md`
- `project/phase_2_original_source_replan.md`

## Asset Inputs

- `public/assets/images/sensor_diagram.png`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
