# feat-021 Convert DOCX Category A logs into production game content

## Status

- status: todo
- type: feat
- priority: 34
- owner agent: dev-agent
- branch: `main`
- commit message: `feat-021 convert docx category a logs into production game content`

## Goal

Replace placeholder-like internal file content with the concrete Category A content from the DOCX sources so the game feels like an investigation rather than a guided checklist.

## Scope

- Use `project/human-input/우주선 탈출게임 로그 예시.docx` as the primary source for Category A file tree and file contents.
- Align the in-game tree around `/Logs`, `/Personnel`, `/System`, `/Utilities`, and `/Recycle_Bin`.
- Preserve the Category A Act path:
  - Act 1: `sensor_calib.log` proves sensor drift and 186-day missed calibration.
  - Act 2: `email_chain_july.txt` reveals Security PIN `8842`; `quarantine_rules.conf` is corrupted and requires `Log_Fixer.exe`; recovered content proves `+17520_HOURS` offset and expired 72-hour quarantine.
  - Act 3: `ai_priority_matrix.json` + `deleted_override.txt` prove ECHO cannot prioritize mission/security over human life.
- Remove or hide production-facing `PLAYER NOTE`, `QA hint`, or direct answer copy.
- Keep optional debug hints behind an explicit debug/hint state only.

## Dependencies

- before: `bug-009`
- after: `feat-022`, `feat-023`, `qa-003`

## Acceptance Criteria

- [ ] Category A files match the DOCX source intent and paths closely.
- [ ] Each required evidence file is discoverable through in-world clues, not direct answer labeling.
- [ ] Noise files exist and are readable but do not falsely block progress.
- [ ] Corrupted and recovered `quarantine_rules.conf` states both exist.
- [ ] Security folder PIN discovery is driven by `email_chain_july.txt`.
- [ ] Existing Act 1~3 progression still passes with the canonical evidence.
- [ ] `npm run build` passes.
- [ ] `git diff --check` passes.

## Source References

- `project/human-input/우주선 탈출게임 로그 예시.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/docx_content_conversion_plan.md`

