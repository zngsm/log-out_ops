# chore-002 Enrich MVP internal file contents

## Status

- status: done
- type: chore
- priority: 10
- owner agent: dev-agent
- branch: `chore-002-enrich-mvp-internal-file-contents`
- commit message: `chore-002 enrich mvp internal file contents`

## Goal

Fill the MVP Hermes OS file contents with enough readable in-world text for the player to feel like they are investigating a real ship system, while preserving the existing deterministic Act progression contract.

## Scope

- Expand Category A file contents using `project/human-input/LOG_OUT 로그 예시.md`.
- Completely rewrite `power_grid_maint.note` with natural diegetic Korean explanation (Q44).
- Completely remove developer explanation note (`<-- 치명적 오차: 약 2년 앞으로 밀림`) from `quarantine_rules.conf` offset item, displaying purely diegetic `시간 오프셋 값: +17,520시간` (Q49 user feedback).
- Clean Sensor diagram content of developer prompt remnants and replace with diegetic diagram containing specified labels (`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점`, etc.) (Q46).
- Completely remove Tool manual security notes (Q35).
- Use `project/human-input/LOG_OUT 로그파일 구조.md` to add useful decoy/flavor files where they improve exploration density.
- Keep required evidence files and ids unchanged unless PM explicitly approves a contract change.
- Preserve Act 3 MVP truth: `ai_priority_matrix.json` + `deleted_override.txt`.
- Add source references or comments when content is derived from human-input docs.
- Do not add other category scenarios to MVP.

## Dependencies

- before: `chore-001`, `feat-005`, `feat-006`
- after: `qa-001`

## Acceptance Criteria

- [x] Each required evidence file contains enough text for a human player to infer why it matters.
- [x] `power_grid_maint.note` is rewritten with natural diegetic Korean description (Q44).
- [x] Developer explanation note (`<-- 치명적 오차: 약 2년 앞으로 밀림`) is completely removed from `quarantine_rules.conf` offset item (Q49 user feedback).
- [x] Sensor diagram developer prompt remnants are removed and replaced with diegetic diagram containing specified labels (`SENSOR-BIO-04 열 감지 스캔 헤드`, `통제실 모듈 #04 장착 지점`, etc.) (Q46).
- [x] Tool manual security notes are completely removed (Q35).
- [x] At least a small number of non-critical flavor/decoy files make the file system feel populated.
- [x] Evidence keywords used by deterministic validation still appear in the relevant files or player-facing clues.
- [x] No old Act 3 evidence pair is reintroduced as category A MVP truth.
- [x] Content remains readable inside the current file viewer UI.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | MVP internal file content enrichment started from latest main |
| 2026-08-05 | review-agent | review approved | no blocking findings; required evidence ids stayed stable and old Act 3 pair was not reintroduced |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three in feat-009.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for MVP content enrichment scope | closed |

## Deliverables

- code changes: `src/App.tsx`, `src/game/categoryAFileSystem.ts`
- branch: `chore-002-enrich-mvp-internal-file-contents`
- commit: `59edca9`
- tests: `npm run build`, `git diff --check`

## PR Draft

- pr title: CHORE-002 MVP 내부 파일 콘텐츠 보강
- pr description:
  - `## Summary`
  - Category A MVP의 필수 증거 파일 본문을 원문 기획서 기준으로 확장하고, 탐색 밀도를 높이기 위한 노이즈/플레이버 파일을 추가함
  - `## Changes`
  - `src/game/categoryAFileSystem.ts`: sensor_calib, email_chain, tool_manual, Log_Fixer, quarantine_rules, ai_priority_matrix, deleted_override 본문 보강
  - `src/game/categoryAFileSystem.ts`: temp_history.db, air_flow.log, daily_routine.log, medical_summary.txt 등 노이즈/플레이버 파일 추가
  - `src/game/categoryAFileSystem.ts`: `/Logs/LifeSupport`, `/Logs/Events` 디렉토리와 관련 file id/path/source refs 추가
  - `src/App.tsx`: 새 로그 디렉토리가 파일 탐색기에 표시되도록 visible directory 목록 추가
