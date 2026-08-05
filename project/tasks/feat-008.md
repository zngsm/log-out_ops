# feat-008 Add opening, ending, visual, and audio feedback

## Status

- status: done
- type: feat
- priority: 10
- owner agent: dev-agent
- branch: `feat-008-add-opening-ending-visual-and-audio-feedback`
- commit message: `feat-008 add opening ending visual and audio feedback`

## Goal

Add MVP-level atmosphere and feedback for opening, resource danger states, blackout, and ending.

## Scope

- Add lightweight opening presentation.
- Add visual feedback for Normal, Caution, Warning, Critical, and Blackout.
- Add ending presentation after successful Act 3.
- Add placeholder sound or WebAudio feedback if approved.
- Add short blackout failure presentation for oxygen 0% or terminal failure.
- Respect debug mode cutscene skip.

## Dependencies

- before: `feat-002`, `feat-003`, `feat-009`
- after: `qa-001`

## Acceptance Criteria

- [x] Scope matches human-confirmed visual direction: R3F spaceship/computer background, placeholder hands, 2D Hermes OS screen.
- [x] MVP does not require final rigged hand assets.
- [x] Ending implementation is Normal Ending A only.
- [x] Visual/audio feedback improves readability and tension without blocking gameplay.

## Workflow Status Log

| date | agent | status change | notes |
| --- | --- | --- | --- |
| 2026-08-05 | dev-agent | todo -> in_progress | opening, ending, and resource feedback implementation started on top of feat-005 gameplay loop |
| 2026-08-05 | review-agent | review approved | no blocking findings; visual feedback uses existing resource/Act state without adding final asset requirements |
| 2026-08-05 | dev-agent | in_progress -> done | build passed, commit pushed to origin |

## Validation

- `npm run build`: pass
- `git diff --check`: pass
- Non-blocking warning: Vite reported a chunk larger than 500 kB after adding R3F/three in feat-009.

## Review History

| round | reviewer | result | findings summary | follow-up status |
| --- | --- | --- | --- | --- |
| 1 | review-agent | approve | no blocking findings for MVP opening, ending, and visual feedback scope | closed |

## Deliverables

- code changes: `src/App.tsx`, `src/styles.css`
- branch: `feat-008-add-opening-ending-visual-and-audio-feedback`
- commit: `2e6be4d`
- tests: `npm run build`, `git diff --check`
- sequencing note: branch includes chore-001, feat-006, and feat-005 dependency commits and should be reviewed after those PRs are merged

## PR Draft

- pr title: FEAT-008 오프닝 엔딩 및 시각 피드백 구현
- pr description:
  - `## Summary`
  - MVP용 오프닝 시퀀스, 전력 위험도별 화면 피드백, blackout/terminal failure 경고, Normal Ending A 연출을 추가함
  - `## Changes`
  - `src/App.tsx`: debug skippable opening overlay, blackout/failure alert, Normal Ending A overlay와 confirmation flow 추가
  - `src/App.tsx`: resource power state와 Act ending-ready 상태를 HUD/visual feedback에 연결
  - `src/styles.css`: cinematic overlay, boot line animation, power danger wash, blackout pulse, ending/failure presentation 스타일 추가
