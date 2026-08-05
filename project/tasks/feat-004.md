# feat-004 Build category A file system data

## Status

- status: done
- type: feat
- priority: 4
- owner agent: dev-agent
- branch: `feat-004-build-category-a-file-system-data`
- commit message: `feat-004 build category a file system data`

## Goal

Create structured file system data for the Bio-hazard category A MVP scenario.

## Scope

- Define directories and files used by category A.
- Include Act 1 sensor evidence.
- Include Act 2 quarantine rule evidence.
- Include Act 3 evidence confirmed from the original plan.
- Mark corrupted/locked/recoverable files where needed.
- Include content metadata for password, recovery, and offset puzzles.

## Category A MVP File Requirements

| act | path | role | required gameplay metadata |
| --- | --- | --- | --- |
| Act 1 | `/Logs/Sensors/sensor_calib.log` | sensor error evidence | keywords include `오차`, `보정`, `186일 미보정` |
| Act 2 | `/Personnel/Dr_Kim/email_chain_july.txt` | password hint | reveals password `8842` |
| Act 2 | `/Utilities/Log_Fixer.exe` | recovery utility | can recover corrupted security config |
| Act 2 | `/System/Security/quarantine_rules.conf` | recovered rule evidence | corrupted before recovery, proves 72-hour quarantine expired after `+17,520시간` offset |
| Act 3 | `/System/Security/ai_priority_matrix.json` | final priority evidence | must be submitted with `deleted_override.txt` |
| Act 3 | `/Recycle_Bin/deleted_override.txt` | final override evidence | must be submitted with `ai_priority_matrix.json` |

## Dependencies

- before: `feat-001`
- after: `chore-001`, `feat-005`, `feat-006`, `feat-007`

## Acceptance Criteria

- [x] File data can be rendered by the explorer and viewer.
- [x] Each file has stable id, path, title, content, and gameplay metadata.
- [x] Content source references are traceable to `project/human-input`.
- [x] Category A Act 3 evidence is explicitly `ai_priority_matrix.json` + `deleted_override.txt`.
- [x] The old category A `auxiliary_capacitor.log` + `emergency_grid_switch.conf` pair is not used for MVP Act 3.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | category A file system data implementation started |
| 2026-08-05 | review-agent | review approved | no blocking findings; data module matches confirmed MVP evidence scope |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- Build output confirmed: `dist/index.html`, `dist/assets/index-DuEYgauW.css`, `dist/assets/index-Dy7o_4NI.js`

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for category A file system data | closed |

## Deliverables

- code changes: `src/game/categoryAFileSystem.ts`
- branch: `feat-004-build-category-a-file-system-data`
- commit: `fc82a54`
- tests: `npm run build`

## PR Draft

- pr title: FEAT-004 카테고리 A 파일 시스템 데이터 구현
- pr description:
  - `## Summary`
  - Bio-hazard 카테고리 A MVP 시나리오에 필요한 디렉터리, 파일, 증거, 암호 힌트, 복구 대상, Act별 gameplay metadata를 추가함
  - `## Changes`
  - `src/game/categoryAFileSystem.ts`: category A directory/file 타입, 파일 목록, Act별 evidence mapping, 파일 조회 helper 추가
