# feat-004 Build category A file system data

## Status

- status: todo
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

- File data can be rendered by the explorer and viewer.
- Each file has stable id, path, title, content, and gameplay metadata.
- Content source references are traceable to `project/human-input`.
- Category A Act 3 evidence is explicitly `ai_priority_matrix.json` + `deleted_override.txt`.
- The old category A `auxiliary_capacitor.log` + `emergency_grid_switch.conf` pair is not used for MVP Act 3.
