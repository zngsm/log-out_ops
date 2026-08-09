# feat-031 Localize File Content To Korean

## Document Meta

- type: feat
- status: done
- owner: dev-agent
- priority: 46
- created: 2026-08-09
- completed: 2026-08-09

## User Request

파일 컨텐츠가 영어라 플레이어가 읽고 추리하기 어렵다. 게임의 핵심 플레이가 파일 내용을 읽는 구조이므로, 플레이어가 이해해야 하는 본문을 한국어 중심으로 바꾼다.

## Scope

- Translate Category A file titles and readable file body copy into Korean.
- Preserve file names, paths, protocol ids, mode names, and system tokens where terminal fiction benefits from them.
- Localize key evidence files for Act 1, Act 2, and Act 3.
- Localize supporting/flavor logs enough that wrong files are still understandable.
- Translate file viewer metadata labels from English to Korean.

## Acceptance Criteria

- Core evidence files can be understood by Korean players without interpreting long English prose.
- Sensor calibration, quarantine expiry, AI priority, and deleted override clues remain clear.
- System flavor remains intact through filenames, ids, and protocol tokens.
- Production build passes.

## Dependencies

- Previous: `feat-030`
- Next: human play review or QA follow-up bugs

## Implementation Notes

- Code commit: `feat-031 localize file content to korean`
- Verification: `npm run build`, `git diff --check`

## Status Log

- todo: user reported file contents are difficult because they are in English.
- in_progress: Category A file data and viewer labels localized.
- done: build passed and ops tracking updated.
