# feat-021 Convert DOCX Category A logs into production game content

## Status

- status: done
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
- Completely rewrite `power_grid_maint.note` into natural diegetic Korean description (Q44).
- Clean Sensor diagram content of developer prompt remnants and replace with diegetic diagram containing specified labels (`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점`, etc.) (Q46).
- Preserve the Category A Act path:
  - Act 1: `sensor_calib.log` proves sensor drift and 186-day missed calibration.
  - Act 2: `email_chain_july.txt` reveals Security PIN `8842` (with bottom note `--- 이전 답장 / 김 박사 ---...` completely removed per Q63 / feat-040); `quarantine_rules.conf` is corrupted and requires `Log_Fixer.exe`; recovered content proves `+17520_HOURS` offset and expired 72-hour quarantine.
  - Completely remove developer explanation note (`<-- 치명적 오차: 약 2년 앞으로 밀림`) from `quarantine_rules.conf` offset item, displaying purely diegetic `시간 오프셋 값: +17,520시간` (Q49 user feedback).
  - Act 3: `ai_priority_matrix.json` + `deleted_override.txt` prove ECHO cannot prioritize mission/security over human life.
- Remove or hide production-facing `PLAYER NOTE`, `QA hint`, or direct answer copy.
- Keep optional debug hints behind an explicit debug/hint state only.

## Dependencies

- before: `bug-009`
- after: `feat-022`, `feat-023`, `qa-003`

## Acceptance Criteria

- [x] Category A files match the DOCX source intent and paths closely.
- [x] `power_grid_maint.note` is rewritten into natural diegetic Korean text (Q44).
- [x] Sensor diagram developer prompt remnants are removed and replaced with diegetic diagram containing specified labels (`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점`, etc.) (Q46).
- [x] Each required evidence file is discoverable through in-world clues, not direct answer labeling.
- [x] Noise files exist and are readable but do not falsely block progress.
- [x] Corrupted and recovered `quarantine_rules.conf` states both exist.
- [x] Developer explanation note (`<-- 치명적 오차: 약 2년 앞으로 밀림`) is completely removed from `quarantine_rules.conf` offset item (Q49 user feedback).
- [x] Security folder PIN discovery is driven by `email_chain_july.txt`.
- [x] Existing Act 1~3 progression still passes with the canonical evidence.
- [x] `npm run build` passes.
- [x] `git diff --check` passes.

## Implementation Notes

- Added DOCX source refs to Category A fixtures so PM/QA can trace content back to the actual `.docx` files.
- Expanded `sensor_calib.log`, `email_chain_july.txt`, `tool_manual.txt`, `quarantine_rules.conf`, and final Act 3 files with DOCX-aligned diegetic details.
- Removed production-facing direct answer labels from several noise/context files.
- Initial gameplay no longer starts with `sensor_calib.log` already attached.
- File viewer now hides evidence role metadata unless QA/debug hints are explicitly enabled.

## Validation

- `npm run build` passed.
- `git diff --check` passed.

## Delivery

- code repo commit: `feat-021 convert docx category a logs into production game content`
- code repo target: `main`

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-08 | dev-agent | todo -> in_progress | Started DOCX Category A content conversion from latest main |
| 2026-08-08 | dev-agent | in_progress -> done | Replaced QA-like labels with diegetic file content and pushed code |

## Source References

- `project/human-input/우주선 탈출게임 로그 예시.docx`
- `project/human-input/우주선 탈출게임 개요.docx`
- `project/docx_content_conversion_plan.md`
