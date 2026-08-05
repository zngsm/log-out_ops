# chore-001 Align content fixtures with planning docs

## Status

- status: done
- type: chore
- priority: 5
- owner agent: dev-agent
- branch: `chore-001-align-content-fixtures-with-planning-docs`
- commit message: `chore-001 align content fixtures with planning docs`

## Goal

Keep implementation fixtures aligned with PM-confirmed planning docs so content does not drift from the game design.

## Scope

- Add comments or metadata that map game files to planning sources.
- Normalize naming for file ids, paths, act ids, and evidence ids.
- Update docs if implementation discovers missing content fields.

## Dependencies

- before: `feat-004`
- after: `feat-005`, `feat-007`

## Acceptance Criteria

- Content fixtures have consistent naming and source references.
- Any unresolved ambiguity is recorded in ops docs instead of guessed in code.
- No player-facing behavior changes are required unless needed for fixture consistency.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | content fixture alignment started from latest main after feat-009 merge |
| 2026-08-05 | review-agent | review approved | no blocking findings; fixture ids, paths, source refs, and validation helper are consistent |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three in feat-009.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for content fixture alignment scope | closed |

## Deliverables

- code changes: `src/game/categoryAFileSystem.ts`
- branch: `chore-001-align-content-fixtures-with-planning-docs`
- commit: `92b28e9`
- tests: `npm run build`, `git diff --check`

## PR Draft

- pr title: CHORE-001 기획 문서 기준 콘텐츠 fixture 정렬
- pr description:
  - `## Summary`
  - Category A 파일 시스템 fixture의 act id, file id, directory path, evidence mapping, source reference를 기획 문서 기준으로 정규화하고 검증 유틸을 추가함
  - `## Changes`
  - `src/game/categoryAFileSystem.ts`: 공용 act/file/path/source-ref 상수 추가
  - `src/game/categoryAFileSystem.ts`: fixture 내부 하드코딩 id/path/source-ref를 공용 상수 기반으로 정렬
  - `src/game/categoryAFileSystem.ts`: file id type guard와 fixture validation helper 추가
