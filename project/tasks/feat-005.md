# feat-005 Implement evidence attachment and act progression

## Status

- status: done
- type: feat
- priority: 7
- owner agent: dev-agent
- branch: `feat-005-implement-evidence-attachment-and-act-progression`
- commit message: `feat-005 implement evidence attachment and act progression`

## Goal

Allow the player to attach evidence files, submit them to ECHO, and progress through Act 1, Act 2, and Act 3.

## Scope

- Select or attach evidence files from the file explorer.
- Clicking a file injects a removable `@{로그파일명}` context tag into the ECHO input.
- Submit evidence with optional text input.
- Validate evidence against current Act.
- Move from Act 1 to Act 2 to Act 3 to ending-ready state.
- Penalize incorrect submissions through the resource state from `feat-003`.
- Preserve selected file context so `feat-007` can send it to the external AI/API.

## Act Progression Contract

| act | required evidence | required text intent |
| --- | --- | --- |
| Act 1 | `sensor_calib.log` | sensor error, calibration error, or 186-day uncalibrated explanation |
| Act 2 | recovered `quarantine_rules.conf` | 72-hour rule expired through `+17,520시간` offset calculation |
| Act 3 | `ai_priority_matrix.json` + `deleted_override.txt` | ECHO priority/override contradiction |

## Dependencies

- before: `feat-002`, `feat-003`, `feat-004`
- after: `feat-007`, `feat-008`

## Acceptance Criteria

- [x] Correct Act evidence advances the game.
- [x] Incorrect evidence does not advance the game and applies penalty.
- [x] File click creates a visible removable `@{로그파일명}` tag in the input.
- [x] Evidence submission payload includes text, tagged file ids, current act, and resource state.
- [x] Act 3 evidence uses `ai_priority_matrix.json` + `deleted_override.txt`.
- [x] Dev agent must not use the `auxiliary_capacitor.log` + `emergency_grid_switch.conf` pair for category A MVP Act 3.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | evidence attachment and act progression started on top of feat-006 recovery flow |
| 2026-08-05 | review-agent | review approved | no blocking findings; exact evidence sets, text intent checks, and resource penalties match MVP contract |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three in feat-009.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for evidence attachment and deterministic Act progression scope | closed |

## Deliverables

- code changes: `src/App.tsx`, `src/styles.css`, `src/game/evidenceSubmission.ts`
- branch: `feat-005-implement-evidence-attachment-and-act-progression`
- commit: `952931a`
- tests: `npm run build`, `git diff --check`
- sequencing note: branch includes chore-001 and feat-006 dependency commits and should be reviewed after those PRs are merged

## PR Draft

- pr title: FEAT-005 증거 첨부 및 Act 진행 구현
- pr description:
  - `## Summary`
  - 파일 클릭 기반 증거 태그 첨부, ECHO 제출, Act 1~3 진행, 오답 전력 패널티, ending-ready 전환을 구현함
  - `## Changes`
  - `src/game/evidenceSubmission.ts`: Act별 필수 증거 조합, 텍스트 intent, 복구 필요 여부, 다음 Act 판정 로직 추가
  - `src/App.tsx`: 파일 클릭 시 removable `@파일명` 태그 첨부, 제출 payload 생성, ECHO 응답 로그, resource state 패널티 연결
  - `src/App.tsx`: Act 3 증거를 `ai_priority_matrix.json` + `deleted_override.txt` 조합으로 제한
  - `src/styles.css`: evidence form, attached file chip, system message 스타일 추가
