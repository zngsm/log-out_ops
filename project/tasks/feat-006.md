# feat-006 Implement Log Fixer recovery interaction

## Status

- status: done
- type: feat
- priority: 8
- owner agent: dev-agent
- branch: `feat-006-implement-log-fixer-recovery-interaction`
- commit message: `feat-006 implement log fixer recovery interaction`

## Goal

Implement the MVP file recovery interaction needed to access restored security or rule content.

## Scope

- Represent corrupted or locked files in the file system.
- Add a `Log_Fixer.exe` style interaction.
- Change file state from corrupted to recovered when the player completes the action.
- Surface recovered content in the file viewer.
- Require or expose password `8842` from `/Personnel/Dr_Kim/email_chain_july.txt` for the category A recovery path.
- Recover `/System/Security/quarantine_rules.conf` for Act 2.

## Dependencies

- before: `feat-002`, `feat-004`
- after: `feat-007`

## Acceptance Criteria

- [x] Recoverable files are visually distinguishable.
- [x] Recovery interaction changes file state.
- [x] Recovered files can be submitted as evidence where relevant.
- [x] Recovery action does not require final animation or sound asset.
- [x] `quarantine_rules.conf` cannot be used as valid Act 2 evidence until recovered.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | Log Fixer recovery interaction started from latest feat-009 main plus chore-001 fixture alignment |
| 2026-08-05 | review-agent | review approved | no blocking findings; security unlock, corrupted/recovered state, and recovery UI meet MVP scope |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three in feat-009.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for MVP Log Fixer recovery flow | closed |

## Deliverables

- code changes: `src/App.tsx`, `src/styles.css`
- branch: `feat-006-implement-log-fixer-recovery-interaction`
- commit: `a233ddd`
- tests: `npm run build`, `git diff --check`
- sequencing note: branch includes chore-001 fixture alignment dependency and should be reviewed after chore-001 is merged

## PR Draft

- pr title: FEAT-006 Log Fixer 복구 인터랙션 구현
- pr description:
  - `## Summary`
  - Log_Fixer.exe를 통해 `/System/Security/quarantine_rules.conf`를 복구하고, 복구 전 Act 2 증거 사용이 차단되는 MVP 복구 흐름을 구현함
  - `## Changes`
  - `src/App.tsx`: Category A fixture 기반 파일 탐색기, 보안 폴더 비밀번호 해제, corrupted/recovered runtime state 추가
  - `src/App.tsx`: Log_Fixer.exe 선택 시 quarantine_rules.conf 복구 액션과 복구 콘텐츠 표시 연결
  - `src/styles.css`: locked/corrupted/recovered 파일 상태, password unlock form, recovery console, warning notice 스타일 추가
