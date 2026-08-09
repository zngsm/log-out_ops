# chore-003 Rewrite Category A content into diegetic clue layer

## Status

- status: done
- type: chore
- priority: 22
- owner agent: dev-agent
- branch: `main`
- commit message: `chore-003 rewrite category a content into diegetic clue layer`

## Goal

Align Category A file contents with the original LOG_OUT examples while separating production clues from debug/hint notes.

## Scope

- Re-check all Category A files against `LOG_OUT 로그 예시.md`.
- Completely rewrite `power_grid_maint.note` into natural diegetic Korean description (Q44).
- Replace Sensor diagram prompt remnants with diegetic diagram containing specified labels (`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점`, etc.) (Q46).
- Completely remove `<dt>증거성</dt>` and `<dt>상태</dt>` DL items from file viewer (Q32).
- Keep exact canonical evidence paths for Act 1, Act 2, and Act 3.
- Add or preserve original decoy/flavor files where they improve investigation density.
- Move `[PLAYER NOTE]` or direct-answer text behind a debug/hint layer.
- Keep diegetic logs readable and inferable without giving direct instructions.
- Keep deterministic keyword validation compatible with rewritten content.

## Dependencies

- before: `feat-004`, `chore-002`
- after: `qa-002`

## Acceptance Criteria

- [x] Required evidence files contain original-source clue information.
- [x] `power_grid_maint.note` is rewritten as natural diegetic Korean text (Q44).
- [x] Sensor diagram prompt remnants are replaced with diegetic diagram with specified labels (`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점`, etc.) (Q46).
- [x] File viewer bottom `<dt>증거성</dt>` and `<dt>상태</dt>` DL items are completely removed (Q32).
- [x] Production file contents do not directly say "this is the answer."
- [x] Debug/hint information is still available for QA or accessibility if enabled.
- [x] Decoy files feel plausible and do not accidentally satisfy evidence validation.
- [x] Act 3 remains `ai_priority_matrix.json` + `deleted_override.txt`.

## Implementation Notes

- Removed direct-answer `[PLAYER NOTE]`, `MVP target`, and system hint copy from production Category A file contents.
- Added `debugHint` metadata to evidence/utility files so QA/accessibility hints remain available behind an explicit viewer toggle.
- Added `SHOW QA HINT` / `HIDE QA HINT` action in the file viewer.
- Preserved canonical evidence paths and validation compatibility.
- Kept Act 3 evidence as `ai_priority_matrix.json` + `deleted_override.txt`.

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- `rg -n "PLAYER NOTE|player_note|mvp_operator_note|System hint|MVP target|핵심" src/game/categoryAFileSystem.ts`: no production matches
- review-agent result: approved

## Delivery

- workflow: latest `main` -> task commit -> push `main`
- code commit: `76427ce chore-003 rewrite category a content into diegetic clue layer`

## Source References

- `project/human-input/LOG_OUT 로그 예시.md`
- `project/human-input/LOG_OUT 로그파일 구조.md`
- `project/phase_2_original_source_replan.md`

## Asset Inputs

- `public/assets/images/sensor_diagram.png`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-06 | dev-agent | todo -> in_progress | Category A diegetic clue rewrite started after feat-016 main push |
| 2026-08-06 | review-agent | in_progress -> approved | Build, diff, and direct-answer text checks passed |
| 2026-08-06 | dev-agent | approved -> done | Code committed and pushed directly to main |
